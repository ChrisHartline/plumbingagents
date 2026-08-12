# Plumbing Agents

An article-first, Colab-friendly lab for exploring a practical multi-agent ecosystem in a plumbing supply business.

The first scenario balances two competing needs:

- keep high-demand parts in stock;
- avoid tying up scarce cash in slow-moving inventory.

The lab uses deterministic Python so the business reasoning is inspectable. It models agent responsibilities, MCP-style tool permissions, A2A-style message contracts, inventory forecasting, stock aging, and cash guardrails without requiring API keys or exposing accounting records.

## Run in Colab

[Open the notebook in Google Colab](https://colab.research.google.com/github/ChrisHartline/plumbingagents/blob/main/notebooks/01_plumbing_agents_colab_lab.ipynb)

Run the cells from top to bottom. The notebook loads the synthetic CSV files from this repository when it is running in Colab, or from `../sample_data` when it is run from the `notebooks` directory in a local clone.

## What the first lab demonstrates

1. The Inventory Agent forecasts reorder quantities and identifies aged stock.
2. Deterministic MCP-style tools restrict each agent to approved data sources.
3. The Accounting Agent converts private finance data into shareable purchasing guardrails.
4. An A2A-style gateway validates sender, recipient, action, and allowed payload fields.
5. The Purchasing Agent builds a purchase plan within the disclosed cash budget.
6. The audit trail shows what was called, shared, removed, selected, and deferred.

## Repository layout

```text
plumbingagents/
|-- notebooks/
|   `-- 01_plumbing_agents_colab_lab.ipynb
|-- sample_data/
|   |-- cash_constraints.csv
|   |-- inventory.csv
|   |-- sales_history.csv
|   `-- supplier_terms.csv
|-- .gitignore
|-- README.md
`-- requirements.txt
```

## Design principle

Prompts tell an agent how it should behave. Protocol and tool policy determine what it can actually access or disclose. In this lab, raw accounting records never enter the shared workflow. Purchasing receives only a period, purchasing budget, minimum reserve, and per-order limit.

## Status

This is a teaching and design artifact, not a production purchasing system. The next engineering phase can extract the notebook layers into a tested Python package and replace the in-process MCP and A2A simulations with protocol-compliant services.
