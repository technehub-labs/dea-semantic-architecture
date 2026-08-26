# ESA Axiom 01 — Semantic layers are architectural, not accidental

**Tenet:** See [../TENETS.md#tenet-1--semantic-layers-are-architectural-not-accidental](../TENETS.md#tenet-1--semantic-layers-are-architectural-not-accidental).

**Status:** Phase 1 of [../../change-requests/CR-ESA-01.md](../../change-requests/CR-ESA-01.md). Full ECF derivation.

## Statement

The organisation of meaning into layers — raw terms → vocabulary → taxonomy → thesaurus → ontology → knowledge graph — is an explicit architectural design choice, not an emergent property of ad-hoc practice.

## ECF derivation

**Principle:** MECE (Mutually Exclusive, Collectively Exhaustive) — from [dea-metaframework/framework/principles.md §2](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Stage-axis rationale:** The seven stages of the ECF value-stream axis (Conceive → Design → Build → Activate → Operate → Improve → Retire), when applied to *meaning itself*, generate the six semantic layers:

| Stage | Semantic layer | ECF cell (Product = row 5) |
|-------|----------------|----------------------------|
| Conceive | (raw terms emerge) | Product × Conceive (5×1) — *not* a layer; terms are pre-architectural |
| Design | **Vocabulary** | Product × Design (5×2) |
| Build | **Taxonomy** | Product × Build (5×3) |
| Activate | **Thesaurus** | Product × Activate (5×4) |
| Operate | **Ontology** | Product × Operate (5×5) |
| Improve | **Knowledge graph** | Product × Improve (5×6) |
| Retire | (layer retirement) | Product × Retire (5×7) |

**Cross-cutting guarantee:** The Governance × Operate cell (1×5) is the assurance that the layer hierarchy itself remains coherent as the layers evolve. Without this cell, the layer stack collapses to whatever ad-hoc practice the strongest current contributor prefers.

## Operational rule

Every sector ESA asset declares which semantic layers it operates on. The declaration cites the ECF cell(s) the asset populates. Layer declarations are auditable — a sector asset that claims to operate "at the vocabulary layer" must demonstrably operate at Product × Design (5×2), not just at "any structured list of terms."

## Anti-patterns

- Treating vocabulary as a flat list (no Design stage; no Product × Design cell).
- Treating ontology as a synonym for "any structured vocabulary" (collapses the Operate and Design stages; loses the layer hierarchy).
- Treating the semantic-layer stack as optional or implied (no cell-by-cell declaration; no governance × Operate assurance).

## Cross-references

- [../TENETS.md §1](../TENETS.md#tenet-1--semantic-layers-are-architectural-not-accidental) — the tenet.
- [../CHARTER.md §3.1](../CHARTER.md#31-in-scope) — semantic layer architectures are in scope.
- [CR-ESA-04](./../../change-requests/CR-ESA-01.md#phase-plan) — Pattern family 1 (semantic layer architectures) expands this axiom into reusable patterns.
