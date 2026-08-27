# Change Requests — Enterprise Semantic Architecture

| CR | Title | Status | Date | PR |
|----|-------|--------|------|----|
| [CR-ESA-01](./CR-ESA-01.md) | Enterprise Semantic Architecture — umbrella / spec proposal | Proposed | 2026-08-26 | (Phase 0 — bootstrap on main `6900cfc`) |
| [CR-ESA-01 Phase 1](./CR-ESA-01.md#phase-plan) | Grounding docs (CHARTER + TENETS + three axioms with ECF derivation) | Proposed | 2026-08-26 | (Phase 1 — pending merge) |

## Pipeline

- **CR-ESA-01** — Umbrella / spec proposal. Phase plan lives in the CR doc; each phase is one future PR.
  - Phase 1 — Grounding docs (CHARTER, TENETS, axioms with ECF derivation).
  - Phase 2 — Telecom operator sector (paired with CR-EO-02).
  - Phase 3 — Cloud service provider sector (paired with CR-EO-03).
  - Phase 4 — Pattern library + full BUILD-A-SPECIALIZED-ASSET.md + GOVERNANCE.md.
  - Phase 5 — ESA Maturity Assessment (cross-repo PR on `Assessment-Models/dea-catalog-assessment-tools`).
  - Phase 6 — Additional sectors (banking, healthcare, government).

## How to add a CR

1. Author the CR doc following the umbrella CR's structure.
2. Land it in `change-requests/CR-<series>-NN-<slug>.md`.
3. Add a row to the table above.
4. Open a PR.