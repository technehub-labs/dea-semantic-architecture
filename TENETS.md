# Tenets — Enterprise Semantic Architecture

ESA tenets are **axiom-derived**, not invented. Every tenet traces to one or more cells of the [ECF](https://github.com/technehub-labs/dea-metaframework) 7×7 matrix, or is explicitly flagged as a sector-specific extension (deferred to [CR-ESA-02](./change-requests/CR-ESA-01.md#phase-plan) onward).

> **Status:** Phase 1 of [CR-ESA-01](./change-requests/CR-ESA-01.md). Three tenets with full ECF derivation.

---

## Tenet 1 — Semantic layers are architectural, not accidental

**Statement.** The organisation of meaning into layers — raw terms → vocabulary → taxonomy → thesaurus → ontology → knowledge graph — is an explicit architectural design choice, not an emergent property of ad-hoc practice.

**Axiom source.** This tenet derives from the **ECF design principle of MECE** (Mutually Exclusive, Collectively Exhaustive) plus the seven stages (Conceive → Design → Build → Activate → Operate → Improve → Retire) of the value-stream axis. The semantic-layer stack is the architectural realisation of the seven stages applied to *meaning itself*: each layer corresponds to a stage of how meaning matures from a raw term to a reasoned assertion.

| ECF cell | Contribution to Tenet 1 |
|---|---|
| Operations × Design (cell 6×2) | The vocabulary layer is designed, not discovered; it is the *Design* of the *Operations* domain. |
| Product × Build (cell 5×3) | The taxonomy layer is built from vocabulary by *Build* (the act of organising vocabulary into hierarchical categories). |
| Product × Activate (cell 5×4) | The thesaurus layer is activated when concepts begin to admit related-as well-as-hierarchical edges. |
| Product × Operate (cell 5×5) | The ontology layer operates continuously; it is the live semantic contract. |
| Product × Improve (cell 5×6) | The knowledge-graph layer improves over time as reasoning, inference, and graph analytics are added. |
| Governance × Operate (cell 1×5) | Assurance that the layers remain coherent as they evolve; the layer hierarchy is itself an architectural invariant. |

**Operational rule.** Every sector ESA asset declares which semantic layers it operates on (a vocabulary without a taxonomy is not an architecture; a taxonomy without a governance rule is not a discipline). Layer declarations cite the ECF cells they populate.

**Anti-pattern.** Treating vocabulary as a flat list. Treating ontology as a synonym for "any structured vocabulary." Treating the semantic-layer stack as optional or implied.

---

## Tenet 2 — Vocabulary governance is a first-class discipline

**Statement.** Vocabularies are versioned, deprecated, mapped, and retired; they are never silently evolved. The governance rules are explicit, owned, and auditable.

**Axiom source.** This tenet derives from the **ECF design principles of Lifecycle continuity** (every object passes through every stage) and **Traceability** (every cell traces to an owner, a state, and a set of dependencies). Vocabulary governance is the application of these principles to the semantic layer specifically.

| ECF cell | Contribution to Tenet 2 |
|---|---|
| Governance × Conceive (cell 1×1) | The policy intent for vocabulary governance is set here; a vocabulary owner commits to a lifecycle policy before adoption. |
| Governance × Design (cell 1×2) | The controls design specifies versioning rules, deprecation policy, mapping declaration rules. |
| Governance × Activate (cell 1×4) | The enforce step is when a vocabulary's governance policy goes live; vocabularies without active enforcement are not governed. |
| Governance × Improve (cell 1×6) | Risk review includes auditing vocabularies for silent evolution (the most common governance failure mode). |
| Governance × Retire (cell 1×7) | Retirement of a vocabulary follows the same governance discipline as retirement of any other enterprise object. |

**Operational rule.** Every vocabulary in a sector ESA asset declares its lifecycle policy (proposed → candidate → active → legacy → deprecated → retired), its deprecation path (mapping to its successor or to a retirement archive), and its owner (an actor in the ECF Actor construct). The vocabulary's lifecycle status is auditable via the [Assessment-Models/assessment-registry](./../../Assessment-Models/assessment-registry) `status` field.

**Anti-pattern.** Silent vocabulary evolution (changing a vocabulary's meaning without declaring a version bump). Silent deprecation (marking a vocabulary deprecated without announcing its successor). Ownerless vocabularies (a vocabulary without an explicit owner is governance-failed by definition).

---

## Tenet 3 — Concept graphs admit multiple edge kinds, not just hierarchies

**Statement.** A concept graph admits broader/narrower, related, equivalent, and mapped-from edges; collapsing it to a tree loses semantic fidelity. The edge-kind discipline is governed; not every concept graph needs every edge kind, but the chosen edge kinds are explicit.

**Axiom source.** This tenet derives from the **ECF design principle of Orthogonality** (the two axes are independent) plus the **formal Construct of Value stream** (the end-to-end flow that carries an object across all seven stages). A concept graph that admits only hierarchical edges is a taxonomy (cell Product × Build, 5×3); a concept graph that admits related + equivalent + mapped-from edges is a semantic asset (cell Product × Operate, 5×5). The transition between these two cell-positions is the architectural moment when a concept graph matures from a taxonomy to a semantic asset.

| ECF cell | Contribution to Tenet 3 |
|---|---|
| Customer × Activate (cell 4×4, ★ high-risk handoff) | The moment a concept graph admits a related-edge is a high-risk handoff: hierarchies can be navigated predictably; related-edges require semantic awareness. |
| Product × Design (cell 5×2) | The catalog & specs stage is where the edge-kind discipline is declared: which edges are admitted, with what cardinality rules. |
| Product × Operate (cell 5×5) | The catalog management stage is where the chosen edge kinds operate continuously; the cardinality rules apply here. |
| Product × Improve (cell 5×6) | The performance stage is where edge-kind effectiveness is measured (e.g. how often related-edges resolve ambiguous queries that hierarchies cannot). |
| Operations × Build (cell 6×3, ★ high-risk handoff) | Provisioning a concept graph that admits mapped-from edges is a high-risk handoff: mapped-from is the edge kind most prone to silent semantic drift. |

**Operational rule.** Every concept graph in a sector ESA asset declares its edge-kind inventory (subset of `{broader, narrower, related, equivalent, mapped-from}`) with cardinality rules per edge kind. The edge-kind inventory is part of the asset's schema, not an ad-hoc extension. Concept graphs with no edge-kind discipline (every property becomes a generic "relation") are non-conformant by definition.

**Anti-pattern.** A concept graph modelled as a tree (only parent/child edges; loses related, equivalent, mapped-from). A concept graph modelled as a property graph (every relation is untyped; loses edge-kind discipline). A concept graph that confuses narrower and related (using a narrower edge to express semantic closeness; the two edge kinds have different semantics).

---

## Sector extensions (forward pointer)

Sector-specific tenets are added in [CR-ESA-02](./change-requests/CR-ESA-01.md#phase-plan) (telecom operator) and [CR-ESA-03](./change-requests/CR-ESA-01.md#phase-plan) (cloud service provider), then [CR-ESA-04](./change-requests/CR-ESA-01.md#phase-plan)+ for additional sectors. Each sector tenet extends one or more of the three base tenets with explicit ECF derivation (mirroring the table structure above) and flags the cell it populates.

---

*Phase 1 of [CR-ESA-01 — Enterprise Semantic Architecture](./change-requests/CR-ESA-01.md).*