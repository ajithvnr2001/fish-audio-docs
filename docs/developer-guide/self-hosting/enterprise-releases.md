---
url: https://docs.fish.audio/developer-guide/self-hosting/enterprise-releases/
title: Releases - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-17T10:47:38.067978+00:00
---

# Releases - Fish Audio

> Source: https://docs.fish.audio/developer-guide/self-hosting/enterprise-releases/

## On this page

  * Version identifiers
  * Upgrading
  * Next step



Self-Hosting

# Releases

Copy pageCopy page

How Fish Audio Enterprise versions are identified and how to move between them

Copy pageCopy page

Fish Audio publishes a version for each mode once it has been tested. **Developer → Self Host** lists the versions available to your team and fills the one you pick into the install commands on that page.

## 

​

Version identifiers

Platform| Identified by| Applied with  
---|---|---  
Helm| A chart version| `--version` on `helm pull`/`install`  
All-in-One| An image tag| The tag in the image reference  
  
Both Helm profiles are one chart, so they share a version. Which profile you deploy is decided by the values file, not by the version. Each All-in-One mode — the combination of billing, GPU topology, and how weights are delivered — is released and tagged independently; **Developer → Self Host** shows the ones your team is granted.

## 

​

Upgrading

A deployment stays on its version until you change it. Take the new version from **Developer → Self Host** , then follow the upgrade procedure in the deployment runbook for the Helm platform, or pull the new tag and recreate the container against the same volume for [All-in-One](https://docs.fish.audio/developer-guide/self-hosting/all-in-one). Air-gapped deployments mirror the new version first. See [Air-gapped deployments](https://docs.fish.audio/developer-guide/self-hosting/air-gapped).

Talk to your account team before skipping versions, and before upgrading a production deployment, so the change can be checked against how yours is configured.

## 

​

Next step

Return to [Kubernetes deployment](https://docs.fish.audio/developer-guide/self-hosting/kubernetes) or [All-in-One container](https://docs.fish.audio/developer-guide/self-hosting/all-in-one) to apply the version you picked.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/self-hosting/enterprise-releases.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/self-hosting/enterprise-releases)

[Operations](https://docs.fish.audio/developer-guide/self-hosting/operations)[AI Coding Assistants](https://docs.fish.audio/developer-guide/resources/coding-agents)
