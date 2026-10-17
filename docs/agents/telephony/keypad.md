---
url: https://docs.fish.audio/agents/telephony/keypad/
title: Keypad Menu and Input - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:46:44.292990+00:00
---

# Keypad Menu and Input - Fish Audio

> Source: https://docs.fish.audio/agents/telephony/keypad/

## On this page

  * Keypad menu
    * What the caller hears
    * Set up the menu
    * In the console
    * Through the API
    * Use the choice
    * Sessions without the menu
    * See what callers chose
  * Keypad input
    * How digits reach the agent
    * Set up keypad input
  * Key tones and speech
  * Phone line requirements
  * Test with a real call
  * Going further



Telephony

# Keypad Menu and Input

Copy pageCopy page

Let phone callers use their keypad: a menu before the agent’s first reply, and digits typed during the call

Copy pageCopy page

Callers can use their phone keypad in two ways:

  * **Keypad menu** : on inbound calls, before the agent’s first reply, the agent plays a short menu (“For appointments, press 1”), takes one key press or a spoken option, and stores the choice in a [dynamic variable](https://docs.fish.audio/agents/build/dynamic-variables). The system prompt, first message, transfers, and webhook tools can act on it. It replaces a separate phone menu in front of the agent, so callers reach the agent without a second hop and a second greeting.
  * **Keypad input** : during inbound and outbound phone calls, digits the caller types, such as a member ID ending with `#`, reach the agent as one message.

Both are off by default and only apply to phone calls.

Keypad menu and keypad input are rolling out to teams gradually. If you don’t see them in the console, contact [support@fish.audio](mailto:support@fish.audio) to turn them on for your team. Until then, turning either one on through the API returns `403`.

## 

​

Keypad menu

### 

​

What the caller hears

1

The menu plays

When the call connects, the agent speaks the menu prompt in its own voice. Any key press stops the prompt at once. When callers can also say an option, speaking stops it too.

2

The caller chooses

A key that belongs to an option selects that option. Any other key counts as no valid choice. When spoken options are on, the caller can say an option’s value (“appointments”) or its key (“two”, “option 2”, “press star”), and other phrasing is matched to the option the caller most likely meant. With a [custom LLM](https://docs.fish.audio/agents/build/custom-llm), only a spoken value or key counts.

3

Retries and fallback

After each prompt the menu waits for input, 5 seconds by default. If the caller is still speaking when the wait ends, the menu lets them finish. Without a valid choice, the agent speaks the retry message and plays the prompt again, up to the configured number of plays. If the caller never makes a valid choice, the variable gets the fallback value.

4

The agent takes over

The variable is filled and the agent’s first message plays with the choice in place. If the caller has already started talking, for example right after pressing the key, the agent answers what they said instead. With the first message off, the agent waits for the caller to speak.

While the menu runs, the agent doesn’t reply. What the caller says or presses still goes into the transcript and into the agent’s context, so the agent knows it once the conversation starts.

### 

​

Set up the menu

#### 

​

In the console

On the agent’s **Phone** page, turn on the **Keypad menu** card and fill it in:

Setting| What it does  
---|---  
**Menu prompt**|  Spoken when the call connects. Name each option and its key. It can use other variables, but not the menu’s own variable.  
**Options**|  Up to 12. Each pairs a key (`0` to `9`, `*`, or `#`) with a value. The variable receives the value, and callers who speak say the value.  
**Callers can also say an option**|  Accept a spoken option instead of a key press. On by default.  
**Variable**|  The variable that receives the choice.  
**Wait for input**|  How long to wait after each prompt.  
**Prompt plays**|  How many times the prompt can play in total, including the first.  
**Retry message**|  Spoken before the prompt plays again. Leave it empty to replay the prompt alone.  
**Fallback value**|  Stored in the variable when the caller makes no valid choice.  
  
Then [publish](https://docs.fish.audio/agents/deploy/versions-publishing). Calls always use the published configuration.

#### 

​

Through the API

Set `conversation.keypad_menu` in the config, then publish:
    
    
    curl --request PATCH https://api.fish.audio/v1/agent/agents/YOUR_AGENT_ID/config \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "conversation": {
          "keypad_menu": {
            "enabled": true,
            "prompt": "Thanks for calling Acme Clinic. For appointments, press 1 or say appointments. For prescriptions, press 2 or say prescriptions. For anything else, press 3.",
            "options": [
              { "key": "1", "value": "appointments" },
              { "key": "2", "value": "prescriptions" },
              { "key": "3", "value": "front desk" }
            ],
            "accept_speech": true,
            "variable": "department",
            "no_input_timeout_seconds": 5,
            "max_attempts": 2,
            "retry_message": "Sorry, I didn'\''t catch that.",
            "fallback_value": "front desk"
          }
        }
      }'
    

Field| Default| Description  
---|---|---  
`enabled`| `false`| Play the menu on inbound calls.  
`prompt`| `""`| Up to 1,000 characters. Required when the menu is enabled.  
`options`| `[]`| 1 to 12 options when enabled, each `{ "key", "value" }`. Keys are unique, values are 1 to 64 characters.  
`accept_speech`| `true`| Accept a spoken option.  
`variable`| `menu_choice`| Follows the [variable name rules](https://docs.fish.audio/agents/build/dynamic-variables#custom-variables).  
`no_input_timeout_seconds`| `5`| 2 to 15.  
`max_attempts`| `2`| Total prompt plays, 1 to 3.  
`retry_message`| `""`| Up to 300 characters.  
`fallback_value`| `""`| Up to 64 characters.  
  
`keypad_menu` is replaced as a whole: fields you leave out go back to their defaults, and `{}` resets the menu. An enabled menu needs a prompt and at least one option, with no key used twice. The prompt and retry message can’t use the menu’s own `{{variable}}`, because it has no value while the menu plays. A request that breaks these rules returns `422`.

### 

​

Use the choice

The menu’s variable works like any [custom variable](https://docs.fish.audio/agents/build/dynamic-variables#custom-variables). Write `{{department}}` (your variable’s name) in:

  * the system prompt and the first message, fixed text or prompt
  * the [transfer announcement](https://docs.fish.audio/agents/telephony/transfers#the-transfer-announcement) and [warm briefing](https://docs.fish.audio/agents/telephony/transfers#customizing-the-briefing)
  * the fixed [farewell](https://docs.fish.audio/agents/build/system-tools#farewell) of the Hang up call tool
  * [webhook tool](https://docs.fish.audio/agents/build/webhook-tools#argument-templating) URLs, header values, and body templates



System prompt
    
    
    The caller chose "{{department}}" in the phone menu. If it is "prescriptions",
    ask for the medication name before anything else.
    

First message
    
    
    You've reached {{department}}. How can I help?
    

On a call where the menu plays, the menu’s value always wins: a default value or an [inbound call webhook](https://docs.fish.audio/agents/monitor/webhooks#inbound-call-webhook) value with the same name is not used.

The first message plays after the menu, and the default first message, fixed or generated, greets the caller. With a menu turned on, the caller hears two greetings until you rewrite it to pick up from the choice, like the fixed first message above. For a generated first message, change the prompt:

First message prompt
    
    
    Don't greet the caller again. Confirm they want {{department}} and ask how you can help.
    

#### 

​

Sessions without the menu

Outbound calls, web and API sessions, preview calls, and agent tests skip the menu. There the variable renders like any other custom variable, from its [default value](https://docs.fish.audio/agents/build/dynamic-variables#default-values) and then `on_missing`. Give the menu’s variable a default, usually the same as the fallback value, so these sessions read well. Without one, `on_missing: reject` rejects them.

### 

​

See what callers chose

Phone sessions report how the menu ended in `keypad_menu`, on [`GET /v1/agent/sessions`](https://docs.fish.audio/agents/monitor/conversation-history) (list and detail) and on the `session` of the `call.ended` and `call.analyzed` [webhooks](https://docs.fish.audio/agents/monitor/webhooks):
    
    
    {
      "keypad_menu": {
        "outcome": "selected",
        "variable": "department",
        "value": "appointments",
        "key": "1",
        "input": "dtmf",
        "attempts": 1,
        "completed_at": "2026-10-01T09:00:05Z"
      }
    }
    

Field| Description  
---|---  
`outcome`| `selected`: the caller chose an option. `no_input` or `no_match`: no play got a valid choice, and the last one got no input or input matching no option. `skipped`: the menu could not run on this call.  
`variable`| The variable the menu filled.  
`value`| The chosen option’s value, or the fallback value without a valid choice.  
`key`| The chosen option’s key. `null` without a valid choice.  
`input`| `dtmf` for a key press, `speech` for a spoken option. `null` without a valid choice.  
`attempts`| How many times the prompt played.  
`completed_at`| When the menu ended.  
  
`keypad_menu` is `null` when the call had no menu, while the call is still in progress, when the caller hung up before the menu ended, and after the session’s content is deleted under the agent’s [data retention](https://docs.fish.audio/agents/monitor/conversation-history#what-gets-stored). Keys pressed during the menu also appear in the transcript, as a user message like `Keypad entry: 2`.

## 

​

Keypad input

### 

​

How digits reach the agent

When keypad input is on, the keys a caller types are grouped into entries. An entry ends when the caller presses the end key (which is not part of the entry), pauses for the configured time, or reaches 50 keys. The agent receives each entry as one user message:
    
    
    Keypad entry: 0071
    

The digits arrive as text, exactly as typed, leading zeros included. The caller doesn’t need to say anything afterwards. A [custom LLM](https://docs.fish.audio/agents/build/custom-llm) receives the same message. Tell the agent what to expect in its system prompt:

System prompt
    
    
    When you need the caller's member ID, ask them to type it on the keypad and
    press pound. Typed digits arrive as "Keypad entry: <digits>". Read the digits
    back one at a time and ask the caller to confirm.
    

  * **Interrupting** : the first key of an entry interrupts the agent the same way speech does, when [interruptions](https://docs.fish.audio/agents/build/configuration#interruptions) are on.
  * **Agent still busy** : an entry that ends while the agent is thinking or speaking waits until the agent is done, then the agent replies to it. Entries are answered in order.
  * **Silence** : key presses count as caller activity, so a caller typing a long number is not treated as silent.
  * **Transcript** : entries are user messages with `input_medium: "dtmf"` in the [session timeline](https://docs.fish.audio/agents/monitor/conversation-history). Other messages have `input_medium: null`.

When keypad input is off, the agent doesn’t respond to keys pressed during the call. Once a transfer or a hang-up is underway, keys no longer reach the agent.

Typed digits are plain text in the transcript and in what the model sees. Don’t use keypad input to collect PINs, card numbers, or other secrets.

### 

​

Set up keypad input

On the agent’s **Configuration** page, open **Keypad input** , turn on **Accept keypad input** , and pick:

  * **End key** : `#`, `*`, or **Pause only**. With `#` as the end key, `*` is an ordinary key in the entry, and the other way around.
  * **Pause before sending** : entries are also sent after a pause this long, even without the end key.

Through the API, set `conversation.keypad_input` and publish. Like `keypad_menu`, it is replaced as a whole:
    
    
    curl --request PATCH https://api.fish.audio/v1/agent/agents/YOUR_AGENT_ID/config \
      --header "Authorization: Bearer $FISH_API_KEY" \
      --header "Content-Type: application/json" \
      --data '{
        "conversation": {
          "keypad_input": {
            "enabled": true,
            "terminator": "#",
            "inter_digit_timeout_seconds": 2
          }
        }
      }'
    

Field| Default| Description  
---|---|---  
`enabled`| `false`| Accept keypad input on phone calls.  
`terminator`| `#`| `#`, `*`, or `none` (pause only).  
`inter_digit_timeout_seconds`| `2`| 1 to 10.  
  
## 

​

Key tones and speech

A key press also makes a tone in the caller’s audio. On calls with a keypad menu or keypad input, these tones are never transcribed as speech and never interrupt the agent. A turn that starts with real speech still reaches the agent, even if the caller presses a key partway through it.

## 

​

Phone line requirements

Key presses can arrive as RFC 4733 telephone events or as tones in the caller’s audio, and the platform accepts both. This includes callers whose carrier only sends tones, which is common on international calls. Numbers you get from Fish Audio need no setup. With [your own SIP trunk](https://docs.fish.audio/agents/telephony/byo-sip), make sure your carrier or PBX either negotiates `telephone-event` in SDP or passes the tones through in the audio. A PBX that removes the tones without sending events delivers no key presses.

## 

​

Test with a real call

Preview calls in the Builder and agent tests don’t run the keypad menu or keypad input. Publish the agent, bind it to a number, and call it from a phone.

## 

​

Going further

## Dynamic variables

Defaults and where variables render.

## Inbound calls

Bind an agent to a number and personalize calls.

## Call transfers

Route callers to people based on their choice.

## Webhooks

Receive each call’s menu outcome.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/agents/telephony/keypad.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/agents/telephony/keypad)

[Call Transfers](https://docs.fish.audio/agents/telephony/transfers)[Conversation History](https://docs.fish.audio/agents/monitor/conversation-history)
