---
title: Locking down AI Foundry so patient data never leaves the network
kind: case study
topic: healthcare
date: 2026-10-01
featured: true
summary: A fully isolated AI platform behind a governance gateway, now the base app and AI teams build on.
tags: [ai-foundry, apim, private-endpoints, hipaa]
ask: Let application and AI teams at a regional health system build on generative AI without exposing anything to the public internet.
result: A BAA-covered AI platform teams now build on, plus a written secure-deployment pattern for every AI service that follows.
flow:
  - name: apps
  - name: apim gateway
    note: auth · limits · token logs
  - name: private endpoint
    note: no public ingress
  - name: ai foundry
    note: default-deny egress
---

## The constraint

Healthcare data can't take shortcuts. Teams wanted to experiment with generative AI, but anything that touched protected health information had to stay on private networks, be fully auditable, and sit under the organization's Business Associate Agreement (BAA).

## What I built

- **Private ingress only.** Azure AI Foundry is reachable solely through private endpoints, with no public network access.
- **Default-deny egress.** Outbound traffic is blocked unless it goes to an approved internal resource.
- **One front door.** Azure API Management sits in front as the governance gateway, handling authentication, rate limiting, and token usage monitoring.
- **A pattern, not a one-off.** I documented the secure deployment pattern for AI services so the next one starts locked down instead of being retrofitted.

## Outcome

Application development and AI teams now build on the platform, covered by the BAA, with usage visible and governed from a single gateway.
