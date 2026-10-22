---
url: https://docs.fish.audio/developer-guide/self-hosting/introduction/
title: Introduction - Fish Audio
method: scrapling+scrapegraph
fetched_at: 2026-10-22T13:06:34.823815+00:00
---

# Introduction - Fish Audio

> Source: https://docs.fish.audio/developer-guide/self-hosting/introduction/

## On this page

  * Why self-host
  * Platforms and modes
  * What is included
  * Architecture at a glance
  * Getting access
  * Next steps



Self-Hosting

# Introduction

Copy pageCopy page

Run the Fish Audio Enterprise speech stack inside your own infrastructure

Copy pageCopy page

Fish Audio Enterprise can be deployed into infrastructure you control: your own cloud account, an on-premise data center, or a network with no internet access at all. Fish Audio delivers container images and a Helm chart through a private registry; you own the cluster, the network boundary, and the data. The self-hosted stack runs the same speech engine as the hosted API, so requests, audio formats, and voice behavior match what you already build against.

## 

​

Why self-host

Reason| What it gives you  
---|---  
Colocation| Run inference in the same region, VPC, or rack as your application and remove public-internet round trips from time-to-first-audio.  
Single-tenant isolation| Dedicated GPUs and queues. Capacity is not shared with other tenants, and you decide when the deployment is upgraded.  
Security posture| Voice traffic never leaves your network. The offline modes make no outbound calls at runtime and run on disconnected networks.  
Data sovereignty| Input text, generated audio, and reference voices stay inside your boundary and under your own retention policy.  
  
## 

​

Platforms and modes

The same engine ships on two platforms. Your enterprise agreement determines which platforms — and which modes of each — your team is granted.

| Helm (Kubernetes)| All-in-One (Docker)  
---|---|---  
Shape| The chart on your cluster: replicas across GPUs and nodes, rolling upgrades.| One container on a single machine; the smallest footprint.  
Best for| Production clusters and elastic capacity.| Evaluation, fixed-size appliances, strict air gaps.  
  
A **mode** is a combination of the axes below; on Helm only billing is a mode — the other axes are cluster configuration. **Developer → Self Host** shows the modes your team can install. **Online** billing authorizes and bills each request against Fish Audio and needs outbound access; **Offline** records usage to a local signed ledger and runs air-gapped.

Axis| All-in-One| Helm  
---|---|---  
Billing| Online or Offline.| The same two, as deployment profiles of one chart — a values file selects the profile.  
Topology| **Dual-GPU** — worker and vocoder on a card each. **Single-GPU** — a special case: both share one H100-class 80 GB card, with lower throughput.| Not a mode — each component takes a whole GPU; you add replicas to grow.  
Weights| **Baked** into the image, or **external** — mounted at run time.| In-cluster by default; the online profile can instead pull from S3-compatible storage — see [Kubernetes deployment](https://docs.fish.audio/developer-guide/self-hosting/kubernetes).  
  
The offline modes are air-gap capable — the Helm profile after mirroring images and the chart into your own registry. Choose the platform and mode that fit your constraints, then agree them with your Fish Audio account team — your agreement determines what **Developer → Self Host** offers you. Combinations beyond this standard set can be discussed there too. Both Helm profiles share one deployment procedure and differ only in a few values. See [Kubernetes deployment](https://docs.fish.audio/developer-guide/self-hosting/kubernetes) for the Helm platform and [All-in-One container](https://docs.fish.audio/developer-guide/self-hosting/all-in-one) for the single-container platform.

## 

​

What is included

Capability| Online Helm| Offline Helm| All-in-One (all modes)  
---|---|---|---  
Text to speech over `POST /v1/tts`| Included| Included| Included  
WebSocket streaming| Included| Included| Included  
Reference-voice requests (`reference_id`)| From local archives| From local archives| From local archives  
Word and segment timestamps| Optional, needs an extra GPU| Optional, needs an extra GPU| Not included  
Horizontal scaling and autoscaling| Included| Included| Not included  
Prometheus metrics| Included| Included| Edge API only, at `/metrics`  
  
Timestamp alignment is served by a separate forced-aligner component. It is disabled by default and is not built into the All-in-One image, so `/v1/tts/stream/with-timestamp` returns audio without alignment data there. Offline Helm needs its model staged on shared storage first; the deployment runbook has the step. Contact Fish Audio if your deployment needs timestamps.

Reference voices are resolved from local archives, which you stage yourself or the optional voice sync downloads: your team’s own fish.audio voices and Fish Audio’s official voices. A self-hosted deployment never reads from the hosted voice library at request time. Products other than text to speech are hosted-only unless your agreement says otherwise.

## 

​

Architecture at a glance

The table describes the Helm deployment; the All-in-One runs the same components inside one container.

Component| Role  
---|---  
Edge API| Entry point. Validates requests, applies product logic, and routes work to the model services.  
Model API layer| Coordinates normalization, inference, and audio decoding.  
Inference router| Distributes work across the GPU workers.  
Inference workers| GPU-backed generation.  
Vocoder| GPU-backed audio decoding.  
Text normalizer| Text normalization ahead of inference.  
Redis| Runtime state and cache. Installed by the chart into the release namespace.  
Shared storage| Model cache, reference archives, and the usage ledger. Mounted on every node.  
  
Fish Audio delivers the deployment at the Kubernetes service level. Ingress, DNS, TLS, external load balancing, and network allowlists are yours to choose and configure.

## 

​

Getting access

1

Agree the deployment scope

Self-hosting is enabled per team under an enterprise agreement. Reach out through [fish.audio/enterprise](https://fish.audio/enterprise) with your GPU target, expected concurrency, and whether you need air-gapped operation.

2

Get your team enabled

Once your agreement is in place, Fish Audio grants your team the artifacts it is entitled to: the Helm chart, the component images, and the All-in-One image where applicable.

3

Create a deploy token

Sign in to fish.audio and open **Developer → Self Host** to see the platforms and modes your team is granted and to create the token that authenticates against the registry. See [Registry & license](https://docs.fish.audio/developer-guide/self-hosting/registry-access).

## 

​

Next steps

## Requirements

GPU, CPU, memory, storage, and platform baselines.

## Registry & license

Create a deploy token, sign in, and download the license bundle.

## Kubernetes deployment

Install, upgrade, roll back, and validate the Helm release.

## All-in-One container

Run the whole stack from a single `docker run`.

## Air-gapped deployments

Mirror artifacts, account for usage offline, and prove zero egress.

## Operations

Monitoring signals, scaling, backups, and troubleshooting.

## Releases

How versions are published, and which one to deploy.

Was this page helpful?

YesNo

[Suggest edits](https://github.com/fishaudio/docs/edit/main/developer-guide/self-hosting/introduction.mdx)[Raise issue](https://github.com/fishaudio/docs/issues/new?title=Issue%20on%20docs&body=Path:%20/developer-guide/self-hosting/introduction)

[Realtime protocol](https://docs.fish.audio/developer-guide/compat/realtime-protocol)[Requirements](https://docs.fish.audio/developer-guide/self-hosting/requirements)
