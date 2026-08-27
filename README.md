# dea-semantic-architecture

> **Canonical grounding repository for Enterprise Semantic Architecture (ESA) in the OpenDEA federation.**
> Status: **proposed pillar** — see [`change-requests/CR-ESA-01.md`](./change-requests/CR-ESA-01.md).

This repository grounds **how an enterprise organises meaning** — vocabularies, taxonomies, concept graphs, semantic layers, knowledge-graph architectures, and the governance of meaning. It is the discipline-of-architecture sibling to [`technehub-labs/dea-ontology`](https://github.com/technehub-labs/dea-ontology).

> **Scope split (with EO):**
> - **ESA** owns *how meaning is organised architecturally* (patterns, topologies, governance rules).
> - **EO** owns *what is formally asserted* (OWL/RDF axioms).
>
> ESA's outputs reference EO's outputs. EO's outputs cite ESA's patterns.

## What lives here

- `CHARTER.md` — core meaning, scope, and non-scope of ESA within OpenDEA. **(Phase 1 — full prose landed.)**
- `TENETS.md` — numbered axioms of the discipline, derived from the ECF 7×7 axiom grid. **(Phase 1 — three tenets with full ECF derivation tables.)**
- `axioms/` — three axiom files, each with derivation table to ECF.
  - `axiom-01-semantic-layer-discipline.md`
  - `axiom-02-vocabulary-governance.md`
  - `axiom-03-concept-graph-topology.md`
- `patterns/` — reusable Semantic Architecture patterns (semantic layer architectures, vocabulary governance, concept-graph topologies, semantic-interoperability patterns). **(Stub index; bodies in Phase 4.)**
- `sectors/` — sector-, industry-, and sub-sector-specific ESA assets. **(Index only in Phase 1; first pair — telecom operator + cloud service provider — in Phase 2–3.)**
- `BUILD-A-SPECIALIZED-ASSET.md` — playbook for authoring a new sector ESA asset. **(Outline in Phase 0; full prose in Phase 4.)**
- `change-requests/` — CRs that shape this repo. CR-ESA-01 is the umbrella.
- `GOVERNANCE.md` — contribution rules, CR template, version semantics. **(Stub prose in Phase 4.)**

## Relationship to OpenDEA

ESA is one of two conceptual pillars introduced by CR-ESA-01 (the other being EO). Both sit between the OpenDEAM root (`technehub-labs/dea-architecture-framework`) and the conceptual layer (`technehub-labs/dea-concepts-model`), instantiating specific dimensions of the architecture:

```
OpenDEAM (root authority)
   │
   ├── ECF (dea-metaframework) — 7×7 axiom grid
   ├── ESA (this repo) ← semantic dimension
   ├── EO (dea-ontology) ← ontological dimension
   │
   ├── Concepts Model (dea-concepts-model, CR-CM-001)
   │       │
   │   Metamodel (dea-metamodel, CR-8; 1.0.0)
   │       │
   │   Catalog repos (dea-catalog-*) — L1 typed content
   │
   └── Assessment-Models/assessment-registry (CR-AR-01 scope extension)
```

## Status

Phase 1 (full grounding docs — CHARTER + TENETS + three axioms with ECF derivation tables) **shipped on this branch, pending merge**. Subsequent phases per `change-requests/CR-ESA-01.md`.

**Visibility:** private at land; promoted to public after Phase 1 ships.

## How to contribute

1. Read the umbrella CR: [`change-requests/CR-ESA-01.md`](./change-requests/CR-ESA-01.md).
2. Read the charter (Phase 1+): [`CHARTER.md`](./CHARTER.md).
3. Propose new sector content via a sector-content CR (e.g. `CR-ESA-02` for telecom operator).
4. Phase plan lives in the umbrella CR; sectors land in pairs with EO.

---

*Established under [CR-ESA-01 — Enterprise Semantic Architecture](./change-requests/CR-ESA-01.md).*