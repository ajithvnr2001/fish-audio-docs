---
url: https://docs.fish.audio/agents/test/import-export-tests/
title: Import and Export Tests - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:03.007703+00:00
---

# Import and Export Tests - Fish Audio

> Source: https://docs.fish.audio/agents/test/import-export-tests/

## On this page

  * The export format
  * Export tests to files
  * Import into the same team
  * Import into another team
  * Going further



Test

# Import and Export Tests

Copy pageCopy page

Save tests as JSON files, recreate them in the same team, or move them to another team over the API

Copy pageCopy page

A test has one JSON format for reading and writing. [Get Test](https://docs.fish.audio/api-reference/endpoint/agent/get-test) returns it, and [Create Test](https://docs.fish.audio/api-reference/endpoint/agent/create-test) accepts the same body as is. That makes it easy to keep tests in version control, copy them to another agent, or move them to another team. **Prerequisites**

  * A Fish Audio [API key](https://docs.fish.audio/developer-guide/getting-started/api-key) for each team involved.
  * `bash`, `curl`, and `jq` 1.6 or later for the scripts below.



## 

​

The export format

An exported test contains every field of its [test type](https://docs.fish.audio/agents/test/agent-tests#test-types), plus:

Field| On import  
---|---  
`test_id`, `workspace_id`, `created_at`, `updated_at`| Ignored. The import gets its own values.  
`agent_ids`| The agents the test was attached to. The import attaches to them again, so change it to target others.  
  
Tools appear as `{"id", "name", "type"}` wherever a test references them: `referenced_tool`, `simulation.assertions`, `simulation.tool_mocks.tools`, and `simulation.tool_mocks.real_tools`. Webhook and client tool ids belong to your team. Integration tool ids, such as `google_calendar:create_event`, are the same in every team. Every call to Create Test creates a new test, so importing the same file twice gives you two copies.

## 

​

Export tests to files

This script saves every test attached to an agent as `tests/<test_id>.json`. Drop the `agent_id` parameter to export your whole test library instead.

export-tests.sh
    
    
    set -euo pipefail
    api=https://api.fish.audio/v1/agent
    auth="Authorization: Bearer $FISH_API_KEY"
    mkdir -p tests
    
    cursor=""
    while true; do
      page=$(curl -sfG "$api/tests" -H "$auth" \
        --data-urlencode "agent_id=$AGENT_ID" \
        --data-urlencode "page_size=100" \
        ${cursor:+--data-urlencode "cursor=$cursor"})
      for id in $(jq -r '.tests[].test_id' <<<"$page"); do
        curl -sf "$api/tests/$id" -H "$auth" > "tests/$id.json"
      done
      [ "$(jq -r .has_more <<<"$page")" = "true" ] || break
      cursor=$(jq -r .next_cursor <<<"$page")
    done
    

## 

​

Import into the same team

Within one team, tool ids stay valid, so the files import as they are:

import-tests.sh
    
    
    set -euo pipefail
    api=https://api.fish.audio/v1/agent
    auth="Authorization: Bearer $FISH_API_KEY"
    
    for file in tests/*.json; do
      curl -sf -X POST "$api/tests" -H "$auth" -H "Content-Type: application/json" \
        --data @"$file" | jq -r '"\(.test_id)  \(.name)"'
    done
    

Each test is attached to the agents in its `agent_ids`. To attach the copies to a different agent instead, rewrite that field on the way in:
    
    
    jq --arg agent "$AGENT_ID" '.agent_ids = [$agent]' "$file" |
      curl -sf -X POST "$api/tests" -H "$auth" -H "Content-Type: application/json" --data @-
    

All agents in `agent_ids` must be in the same workspace, and the test is created there.

## 

​

Import into another team

Webhook and client tool ids from the source team mean nothing in the target team, so each reference has to point at the target team’s tool of the same name first.

Create Test does not reject webhook and client tool ids it doesn’t know. A test imported without remapping saves fine but misbehaves when it runs: its mocks never apply, required tool calls fail with _This tool is not on the agent_ , and forbidden tool checks pass without checking anything. Always remap before importing into another team.

1

Recreate the tools

In the target team, create the tools the tests reference, with the same names, for example with [Create Tool](https://docs.fish.audio/api-reference/endpoint/agent/create-tool), and attach them to the target agent. Connect the same integrations on that agent if the tests reference integration tools.

2

Remap and import

Run this script with the target team’s API key and agent. It reads the tools the target agent offers from [List Test Tools](https://docs.fish.audio/api-reference/endpoint/agent/list-test-tools), replaces every webhook and client tool id by name, attaches each test to the target agent, and stops with the tool’s name if the agent has no tool with that name.

import-into-team.sh
    
    
    set -euo pipefail
    api=https://api.fish.audio/v1/agent
    auth="Authorization: Bearer $FISH_API_KEY"
    
    tools=$(curl -sf "$api/agents/$AGENT_ID/test-tools" -H "$auth" |
      jq '[.tools[] | select(.type != "integration") | {(.name): .id}] | add // {}')
    
    for file in tests/*.json; do
      jq --argjson tools "$tools" --arg agent "$AGENT_ID" '
        walk(
          if type == "object" and (.type == "webhook" or .type == "client")
            and has("id") and has("name")
          then .id = ($tools[.name] // error("No tool named \(.name) on the target agent"))
          else . end
        )
        | .agent_ids = [$agent]
      ' "$file" |
        curl -sf -X POST "$api/tests" -H "$auth" -H "Content-Type: application/json" \
          --data @- | jq -r '"\(.test_id)  \(.name)"'
    done
    

Integration tool ids are left as they are, since they are the same in every team.

## 

​

Going further

## Agent tests

Every test type and how its fields map to the API.

## Run tests from CI

Run an agent’s tests from your pipeline and gate on the result.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/test/import-export-tests.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/test/import-export-tests)

[Agent Tests](https://docs.fish.audio/agents/test/agent-tests)[Tutorial: Simulate a Rescheduling Call](https://docs.fish.audio/agents/test/simulation-tutorial)
