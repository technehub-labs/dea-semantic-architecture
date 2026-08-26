# Charter — Enterprise Semantic Architecture

This document is the canonical grounding of **Enterprise Semantic Architecture (ESA)** within the OpenDEA federation. It defines ESA's core meaning, scope, and the boundary with its sibling discipline (Enterprise Ontology).

> **Status:** Phase 1 of [CR-ESA-01](./change-requests/CR-ESA-01.md). Full prose; derived from the Enterprise Concept Framework ([ECF](https://github.com/technehub-labs/dea-metaframework)).

## 1. Core meaning

**Enterprise Semantic Architecture (ESA)** is the discipline of how an enterprise **organises meaning** — its vocabularies, taxonomies, concept graphs, semantic layers, and knowledge-graph architectures, together with the governance rules that keep them coherent over time.

ESA is *not* a data-modelling discipline (that is a data-engineering concern). It is *not* an ontology-modelling discipline (that is [Enterprise Ontology](https://github.com/technehub-labs/dea-ontology) — EO's domain). It is *not* a knowledge-graph runtime concern (that is the [OpenDEA runtime](https://github.com/technehub-labs/dea-metamodel)'s domain). It is the **architectural discipline** that decides *how meaning is structured, layered, and governed* across the enterprise — leaving *what is formally asserted* to EO and *how it is executed* to the runtime.

ESA is the answer to the question: **when an enterprise has many products, sectors, organisational units, and decades of accumulated vocabulary — how does it keep "what we mean" coherent, traceable, and governed?**

## 2. Position in OpenDEA

ESA sits as one of two conceptual pillars between the OpenDEAM root (`technehub-labs/dea-architecture-framework`) and the conceptual layer (`technehub-labs/dea-concepts-model`). Its sibling is Enterprise Ontology (EO). The two pillars instantiate specific dimensions of the architecture:

```
OpenDEAM (root authority)
   │
   ├── ECF (dea-metaframework) — 7×7 axiom-derived matrix
   ├── ESA (this repo) ← semantic dimension: HOW meaning is organised
   ├── EO (dea-ontology) ← ontological dimension: WHAT is formally asserted
   │
   ├── Concepts Model (dea-concepts-model, CR-CM-001) — the concept graph
   │       │
   │   Metamodel (dea-metamodel, CR-8; 1.0.0) — entity + relationship types
   │       │
   │   Catalog repos (dea-catalog-*) — L1 typed content
   │       │
   │   └── dea-catalog-ontologies ← EO umbrella content
   │
   └── Assessment-Models/assessment-registry — registers all OpenDEA-compatible assets
```

ESA's outputs reference EO's axioms and the concepts model's graph. The concepts model in turn cites ESA's patterns. EO's axioms cite ESA's vocabulary-governance patterns. The cycle is intentional and cyclic — each discipline owns one layer of the meaning stack.

## 3. Scope and non-scope

### 3.1 In scope

- **Semantic layer architectures.** The layered organisation of meaning from raw terms through vocabularies, taxonomies, thesauri, ontologies, and knowledge graphs. ESA governs *how* these layers are structured, what each layer's contract is, and how layers compose.
- **Concept graphs.** The topology of how concepts relate — broader/narrower, related, equivalent, mapped-from — and the cardinality rules that govern each edge kind. ESA owns the *topology*; the concepts model (`dea-concepts-model`) owns the *concrete concept entries*.
- **Vocabulary governance.** Versioning, deprecation, mapping, and retirement policies for vocabularies. ESA governs the *rules*; individual vocabulary repos implement them.
- **Semantic interoperability patterns.** How concepts are exchanged across organisational, sector, and ecosystem boundaries — naming, namespace policy, identifier policy, mapping declaration.
- **Knowledge-graph architecture.** The structural patterns and reference topologies for federated knowledge graphs (which is distinct from any specific knowledge-graph runtime).
- **Sector ESA assets.** The discipline of authoring sector-, industry-, and sub-sector-specific ESA assets (e.g. telecom operator semantic-layer architecture, cloud service provider concept graph). Authored under [CR-ESA-02](./change-requests/CR-ESA-01.md#phase-plan) onward.

### 3.2 Out of scope

- **Formal ontology axioms** (OWL/RDF classes, properties, restrictions, reasoning) — owned by [EO](https://github.com/technehub-labs/dea-ontology).
- **Operational data models** (database schemas, ETL pipelines, table layouts) — data-engineering concern.
- **AI / agent knowledge bases at runtime** — governed by [CR-012 Enterprise Intelligence](https://github.com/technehub-labs/dea-metamodel/blob/main/change-requests/CR-012.md).
- **Knowledge-graph query, traversal, mutation** — the OpenDEA runtime's domain.
- **Specific concept definitions** — the concepts model's domain (CR-CM-001).

## 4. Relationship to sibling disciplines

| Discipline | Owner | Boundary with ESA |
|---|---|---|
| Enterprise Ontology (EO) | [`technehub-labs/dea-ontology`](https://github.com/technehub-labs/dea-ontology) | EO asserts; ESA organises. ESA patterns cite EO axioms; EO axioms cite ESA vocabulary-governance patterns. |
| Concepts Model (CM-001) | [`technehub-labs/dea-concepts-model`](https://github.com/technehub-labs/dea-concepts-model) | ESA governs concept-graph topology; CM-001 owns the concrete concept entries. |
| Metamodel (CR-8) | [`technehub-labs/dea-metamodel`](https://github.com/technehub-labs/dea-metamodel) | ESA assets conform to metamodel entity/relationship types (via CM-001). |
| OpenDEAM (root) | [`technehub-labs/dea-architecture-framework`](https://github.com/technehub-labs/dea-architecture-framework) | OpenDEAM cites ESA as the authority for the semantic dimension of architecture. |
| Assessment Registry (CR-AR-01) | [`Assessment-Models/assessment-registry`](https://github.com/Assessment-Models/assessment-registry) | ESA assets register with the registry under `asset_class: semantic`. |

## 5. Authority boundaries

This repository (`technehub-labs/dea-semantic-architecture`) is **the** canonical authority for ESA within the OpenDEA federation. Concretely:

- **What this repo owns.** The grounding documents (CHARTER, TENETS, axioms), the pattern library, the sector content (under sector-content CRs), the BUILD playbook, and the governance rules for ESA assets.
- **What this repo defers.**
  - Formal ontology axioms → EO (referenced, not owned).
  - Concrete concept definitions → Concepts Model (referenced, not owned).
  - Specific vocabulary content → individual vocabulary repos implementing the patterns (referenced, not owned).
  - ESA Maturity Assessment → `Assessment-Models/dea-catalog-assessment-tools` (CR-ESA-05).

## 6. Reversibility

ESA assets are designed for **reversible** evolution. Every asset declares:

- Its **lifecycle status** (`proposed` → `candidate` → `active` → `legacy` → `deprecated` → `retired`).
- Its **deprecation path** — what asset replaces it when retired, and what mappings make the transition lossless.
- Its **retention policy** — how long archived copies are kept, and where they are referenced from.

Reversibility is non-negotiable. A sector ESA asset that cannot be deprecated losslessly is a liability, not an asset. See [TENETS.md](./TENETS.md) §3 for the operational rule.

## 7. Naming taste

ESA vocabulary follows the user's standing preference: **digital-native nomenclature over archaic CMMI-era vocabulary**. Examples:

- **Use** *taxonomy*, *concept graph*, *semantic layer*, *vocabulary*, *mapping*. **Avoid** *controlled vocabulary*, *business glossary*, *metadata repository* (when describing an architecture pattern).
- **Use** *concept* as the unit of meaning (per CM-001). **Avoid** *term* except when referring to raw lexical items (the bottom of the semantic-layer stack).
- **Use** *sector*, *industry*, *sub-sector* as the three-level sector taxonomy. **Avoid** *vertical*, *domain*, *LOB* (line of business) — these have ambiguous meanings.
- **Use** *activate*, *retire*, *migrate*, *sunset* (the ECF stage names) when describing lifecycle transitions. **Avoid** *decommission*, *deprecate without replacement*, *kill* — these are imprecise.

The full naming glossary lives in [CR-ESA-01](./change-requests/CR-ESA-01.md) and is refined as sector content lands.

## 8. ECF derivation

ESA is axiom-derived from the Enterprise Concept Framework. The derivation chain:

1. **The ECF grounding axiom** — "An enterprise is any bounded entity that persists by exchanging value with its environment." — generates the 7 domains and 7 stages of the ECF matrix.
2. **ESA's three tenets** ([TENETS.md](./TENETS.md)) each derive from one or more ECF cells. The derivation tables are in the axiom files.
3. **ESA's sector assets** derive from sector tenet extensions (CR-ESA-02 onward) and cite the ECF matrix cells they populate.
4. **ESA's pattern library** (Phase 4) cites the ECF matrix as the structural backbone for sector semantic-layer architectures.

The ECF axiom-derived bottom-up methodology is the reason ESA can be **universal** — it fits any enterprise because it derives from what an enterprise is, not from a specific industry's practices.

---

*Phase 1 of [CR-ESA-01 — Enterprise Semantic Architecture](./change-requests/CR-ESA-01.md).*