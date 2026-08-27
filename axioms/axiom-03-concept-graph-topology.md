# ESA Axiom 03 — Concept graphs admit multiple edge kinds, not just hierarchies

**Tenet:** See [../TENETS.md#tenet-3--concept-graphs-admit-multiple-edge-kinds-not-just-hierarchies](../TENETS.md#tenet-3--concept-graphs-admit-multiple-edge-kinds-not-just-hierarchies).

**Status:** Phase 1 of [../../change-requests/CR-ESA-01.md](../../change-requests/CR-ESA-01.md). Full ECF derivation.

## Statement

A concept graph admits broader/narrower, related, equivalent, and mapped-from edges; collapsing it to a tree loses semantic fidelity. The edge-kind discipline is governed; not every concept graph needs every edge kind, but the chosen edge kinds are explicit.

## ECF derivation

**Principle:** Orthogonality (the two axes are independent) — from [dea-metaframework/framework/principles.md §4](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Construct:** Value stream (the end-to-end flow that carries an object across all seven stages) — from [dea-metaframework/framework/constructs.md](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/constructs.md).

**Edge-kind → stage mapping:** The five edge kinds of a mature concept graph correspond to transitions through the ECF stages:

| Edge kind | ECF stage | ECF cell (Product = row 5) | Cardinality rule |
|-----------|-----------|----------------------------|------------------|
| `narrower` (parent→child) | Build (hierarchical construction) | Product × Build (5×3) | 1..n (a concept may have multiple narrower children) |
| `broader` (child→parent, inverse of narrower) | Build (inverse) | Product × Build (5×3) | 1..1 (a concept has exactly one broader parent in a taxonomy; poly-hierarchies declare multiple parents as multiple narrower edges from the parents' perspective) |
| `related` (associative) | Activate (thesaurus stage) | Product × Activate (5×4) ★ high-risk handoff | 0..n (symmetric; cardinality declared per pair) |
| `equivalent` (cross-vocabulary equality) | Operate (live semantic contract) | Product × Operate (5×5) | 0..n (one concept can be equivalent to multiple concepts in other vocabularies) |
| `mapped-from` (cross-vocabulary approximation) | Operate (live semantic contract) | Product × Operate (5×5) | 0..n (one concept can be mapped-from multiple sources) |

**The transition cell:** Product × Activate (5×4) — the ★ high-risk handoff where a concept graph matures from a taxonomy (only narrower/broader) to a semantic asset (admits related + equivalent + mapped-from). The high-risk nature is because related-edges require semantic awareness to navigate; hierarchies are predictable.

**The drift-risk cell:** Operations × Build (6×3) ★ — the moment a concept graph is provisioned. Mapped-from edges are most prone to silent semantic drift because the source vocabulary may evolve without notice.

## Operational rule

Every concept graph in a sector ESA asset declares its **edge-kind inventory** (subset of `{broader, narrower, related, equivalent, mapped-from}`) with **cardinality rules per edge kind**. The edge-kind inventory is part of the asset's schema, not an ad-hoc extension. Concept graphs with no edge-kind discipline (every property becomes a generic "relation") are non-conformant by definition.

The edge-kind declaration cites the ECF cell(s) the asset populates, mirroring the table above.

## Anti-patterns

- **Tree-only concept graph** — only parent/child edges; loses related, equivalent, mapped-from (collapses Product × Build into a single cell, ignoring Product × Activate / Product × Operate).
- **Property-graph concept graph** — every relation is untyped; loses edge-kind discipline (violates Orthogonality principle).
- **Confusing narrower and related** — using a narrower edge to express semantic closeness (the two edge kinds have different semantics and different ECF cells; narrowing a "related" relation loses the ability to reason about hierarchy independently).
- **Undeclared mapped-from** — declaring a mapped-from edge without a mapping declaration in the source vocabulary (drift-risk cell violation; Operations × Build).

## Cross-references

- [../TENETS.md §3](../TENETS.md#tenet-3--concept-graphs-admit-multiple-edge-kinds-not-just-hierarchies) — the tenet.
- [../CHARTER.md §3.1](../CHARTER.md#31-in-scope) — concept-graph topology is in scope; concrete concept entries are deferred to the concepts model (CR-CM-001).
- [CR-ESA-04](./../../change-requests/CR-ESA-01.md#phase-plan) — Pattern family 3 (concept-graph topology patterns) expands this axiom.
