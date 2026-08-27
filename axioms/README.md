# Axioms — Enterprise Semantic Architecture

This directory holds the three ESA axioms in their own files, each with its full ECF derivation. The axioms are axiom-derived from the [Enterprise Concept Framework](https://github.com/technehub-labs/dea-metaframework); they are not invented.

| # | Axiom | Tenet |
|---|-------|-------|
| 1 | [axiom-01-semantic-layer-discipline.md](./axiom-01-semantic-layer-discipline.md) | Semantic layers are architectural, not accidental |
| 2 | [axiom-02-vocabulary-governance.md](./axiom-02-vocabulary-governance.md) | Vocabulary governance is a first-class discipline |
| 3 | [axiom-03-concept-graph-topology.md](./axiom-03-concept-graph-topology.md) | Concept graphs admit multiple edge kinds, not just hierarchies |

Each axiom derives from one or more ECF cells (the 7-domain × 7-stage matrix). The derivation is shown explicitly in each axiom file — a sector extension that does not show its ECF derivation is non-conformant by definition.

## How to derive a sector tenet extension

When a sector ESA asset (telecom operator, cloud service provider, etc.) needs a sector-specific tenet, the extension MUST:

1. Pick one of the three base axioms to extend.
2. Identify the additional ECF cell(s) the sector populates.
3. Add a sector-specific tenet that derives from those cells, with the same Statement / ECF derivation / Operational rule / Anti-pattern structure as the base axioms.
4. Cite the ECF cells it populates, mirroring the table structure in the base axioms.

Sector extensions live in `sectors/<sector>/tenets/` (Phase 2 onward). They never modify the three base axioms — they extend them.

## How the axioms relate to patterns

The axioms are *what*. The patterns (Phase 4) are *how*. Each axiom file points at the pattern family that operationalises it:

- Axiom 1 → Pattern family 1: Semantic layer architectures.
- Axiom 2 → Pattern family 2: Vocabulary governance patterns.
- Axiom 3 → Pattern family 3: Concept-graph topology patterns.

Additional pattern families (semantic interoperability, knowledge-graph architecture) ship in Phase 4.

## How the axioms relate to the registry

Each sector ESA asset registers with the [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) under `asset_class: semantic`. The asset's `compatibility` block (per CR-AR-01 Phase 1) declares the axes it satisfies:

- `governance` (cross-class shared baseline)
- `vocabulary_governance` (Axiom 2)
- `concept_graph_topology` (Axiom 3)
- `pattern_conformance` (references patterns from `patterns/`)

See [`axes/catalog.yaml`](https://github.com/Assessment-Models/assessment-registry/blob/main/axes/catalog.yaml) for the full per-class axis catalogue.