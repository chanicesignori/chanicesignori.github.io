---
title: Private Link from the hub out
kind: case study
topic: networking
date: 2026-09-01
summary: One hub-centralized pattern for private connectivity and the DNS that makes it work.
tags: [bicep, private-link, private-dns, hub-spoke]
ask: Connect a SaaS monitoring platform over Private Link and make private endpoint DNS resolve the same way everywhere.
result: One hub-centralized, code-defined pattern for private connectivity, and consistent DNS resolution for private endpoints across the network.
flow:
  - name: spokes
  - name: hub vnet
    note: private endpoints
  - name: private dns
    note: standard forwarding
  - name: saas over private link
    note: no public path
---

## The constraint

Private endpoints only help if every network can resolve them correctly. Without a standard, each new endpoint risks a one-off DNS fix and traffic quietly falling back to a public path.

## What I built

- **Centralize in the hub.** Datadog Private Link is deployed in the hub with Bicep, so spokes share one private path instead of each building their own.
- **Standardize DNS.** A consistent forwarding pattern for private endpoint DNS zones, so new endpoints resolve correctly from day one.
- **Everything as code.** The whole pattern lives in Bicep, so it can be reviewed, repeated, and rolled back.

## Outcome

A reusable pattern for private connectivity and fewer surprise DNS issues when new private endpoints come online.
