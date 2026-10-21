---
title: MCP servers without stored secrets
kind: field note
topic: home lab
date: 2026-08-15
summary: Managed identity and least-privilege RBAC instead of API keys, for MCP servers in C# and Python.
tags: [mcp, container-apps, managed-identity, rbac]
ask: Run MCP servers that call Azure resources without a single API key or connection string sitting in config.
result: MCP servers in C# and Python on Azure Container Apps that authenticate with managed identity and only the roles they need.
flow:
  - name: mcp client
  - name: container apps
    note: mcp server
  - name: managed identity
    note: DefaultAzureCredential
  - name: azure resources
    note: least-privilege rbac
---

## Why it matters

AI agents are only as safe as the tools they can call. An MCP server holding a long-lived secret is one leaked config file away from trouble.

## The approach

- **No secrets in config.** Servers use `DefaultAzureCredential`, which picks up the container app's managed identity in Azure and a developer login locally.
- **Least privilege.** Each server's identity gets only the RBAC roles its tools actually need.
- **Two languages, one pattern.** The same approach works for MCP servers written in C# and Python, deployed to Azure Container Apps.
