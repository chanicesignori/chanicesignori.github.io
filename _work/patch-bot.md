---
title: A patch bot 40+ teams actually use
kind: case study
topic: automation
date: 2026-09-15
summary: Patch confirmations and exceptions moved into Teams, with signed payloads.
tags: [uipath, teams, adaptive-cards, hmac]
ask: Get dozens of server-owning teams to confirm patch windows and flag exceptions every cycle, without chasing them by email.
result: Used by 40+ teams across 10 patch cycles, with every response tied to a signed, verifiable payload.
flow:
  - name: uipath
    note: schedules the cycle
  - name: teams card
    note: confirm or flag exception
  - name: hmac check
    note: signed payload
  - name: patch record
---

## The constraint

Patch cycles depend on server owners confirming their windows or calling out exceptions. Email threads made that slow to collect and hard to trust.

## What I built

- **Meet people where they work.** UiPath automation sends each team a Teams adaptive card for the upcoming cycle.
- **Confirm or flag in one tap.** Owners confirm their window or log an exception right from the card.
- **Trust the answer.** Card payloads are HMAC-signed, so a response can be verified before it changes anything.

## Outcome

Adopted by 40+ teams and run across 10 patch cycles.
