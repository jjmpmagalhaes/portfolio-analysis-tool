# Portfolio Analysis Tool

A portfolio analysis project designed to support wealth management
workflows and develop practical skills in financial data analysis,
Python and software development.

## Objective

Evolve an existing Excel-based portfolio diagnostic workflow into
a reliable, documented and reproducible analytical tool.

## Current Status

Early development.

This repository currently contains project documentation.
The Python implementation has not started.

The existing Excel workflow provides the functional reference
for the project's development.

## Functional Scope

The project will progressively cover:

- Portfolio characterization and asset allocation.
- Position weights and concentration analysis.
- Data validation and unidentified asset alerts.
- Editable stress scenarios.
- Clear portfolio summaries and reports.

Financial instrument type and asset class will be treated as
separate dimensions.

## First Milestone

Build a small Python program that:

1. Reads a CSV file containing a fictional portfolio.
2. Checks that required fields and numeric values are valid.
3. Calculates total portfolio value.
4. Calculates the weight of each position.
5. Identifies the largest position.
6. Displays a clear summary.

For this first milestone, position values will be provided in EUR.

### Validation Example

A portfolio containing positions worth EUR 6,000, EUR 3,000
and EUR 1,000 must produce:

- Total value: EUR 10,000.
- Position weights: 60%, 30% and 10%.
- Largest position: EUR 6,000, representing 60%.

Invalid or missing values must be reported clearly.

## Development Roadmap

1. CSV import and basic calculations.
2. Asset classification and allocation analysis.
3. Concentration indicators and validation alerts.
4. Editable stress testing.
5. Charts and report generation.
6. A user interface, if useful.

## Working Principles

- Develop one small feature at a time.
- Keep financial calculations explicit and verifiable.
- Check results against examples with known answers.
- Document assumptions and limitations.
- Use fictional data for development and demonstrations.
- Keep client information and credentials out of the repository.

## Project Documentation

- [Roadmap](ROADMAP.md) — Existing Excel features and planned development.
- [Ideas](IDEAS.md) — Possible improvements to evaluate.
- [Changelog](CHANGELOG.md) — History of project changes.
- [Claude instructions](CLAUDE.md) — Project instructions for Claude Code.

## Technical Documentation

Initial documentation based on Excel v11.3.
Formula audits and functional validation remain pending.

- [Methodology](docs/METODOLOGIA.md)
- [Metrics](docs/METRICAS.md)
- [Asset Classification](docs/CLASSIFICACAO_ATIVOS.md)
- [Stress Testing](docs/STRESS_TEST.md)
- [Alerts and Controls](docs/ALERTAS.md)