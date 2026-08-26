# CR-ESA-01 — Enterprise Semantic Architecture

## Status

- **State:** Proposed — awaiting explicit "Merge" approval.
- **Series tag:** `CR-ESA` (Enterprise Semantic Architecture). New umbrella series.
- **Numbering convention:** subsequent ESA CRs use compliant numbering (e.g. `CR-ESA-02` for sector content, `CR-ESA-03` for governance evolution).
- **Primary repo:** `technehub-labs/dea-semantic-architecture` *(new, created in this proposal)*
- **Visibility:** Private at land; promoted to public after Phase 1 ships.
- **Sibling CRs:** `CR-EO-01` (Enterprise Ontology — same architectural pillar, complementary discipline); `CR-AR-01` (assessment-registry scope extension — parallel proposal, different repo).
- **Predecessors:** none — this is a foundational pillar CR.
- **Successors (parked):** CR-ESA-02 (sector content — telecom + cloud service providers, first pair); CR-ESA-03 (semantic layer reference architecture); CR-ESA-04 (vocabulary governance playbook); CR-ESA-05 (ESA maturity assessment, lands in `Assessment-Models/dea-catalog-assessment-tools`).

## Primary objective

Establish `technehub-labs/dea-semantic-architecture` as the **canonical grounding repository for Enterprise Semantic Architecture (ESA)** in the OpenDEA federation — defining its core meaning, tenets, axioms, and the means by which sector-, industry-, and sub-sector-specific Semantic Architecture assets are authored and offered.

## Why now

OpenDEAM (the root authority in `technehub-labs/dea-architecture-framework`) governs architecture *layers and building blocks* but is silent on how an enterprise **organises meaning** — vocabularies, concept graphs, semantic layers, knowledge-graph architectures, and the governance of meaning. Three consequences:

1. Catalog authors (e.g. `dea-catalog-ontologies`, `dea-catalog-concepts`, `dea-catalog-tenets`) currently invent vocabulary conventions locally, producing drift across the federation.
2. Sector-specific assets (telecom operator semantic models, cloud service provider concept graphs, etc.) have no shared grounding — every tenant of OpenDEAM reinvents semantic-architecture practice.
3. The "Enterprise Ontology" discipline (CR-EO-01) needs a discipline-of-architecture sibling that owns **how semantic assets are structured**, while EO owns **what the assets formally assert**. Without this split, the two collapse into one repo and neither is grounded properly.

CR-ESA-01 creates the pillar that complements CR-EO-01; together they replace ad-hoc semantic-architecture practice with a single, federated, grounded discipline.

## Architectural principle

**ESA is a discipline of architecture, not a sub-discipline of data engineering.**

ESA governs:

- **Semantic layers** — the layered organisation of meaning (raw terms → vocabulary → taxonomy → thesaurus → ontology → knowledge graph).
- **Concept graphs** — how concepts relate (broader/narrower, related, equivalent, mapped-from), and the cardinality rules that govern them.
- **Vocabulary governance** — how vocabularies are versioned, deprecated, mapped, and retired.
- **Semantic interoperability patterns** — how concepts are exchanged across organizational, sector, and ecosystem boundaries.
- **Knowledge-graph architecture** — the structural patterns and reference topologies for federated knowledge graphs.

ESA does **not** govern:

- **Ontological commitments** (formal OWL/RDF axioms) — that is EO's domain.
- **Data models** in the operational sense (schemas, tables, ETL) — that is a data-engineering concern.
- **AI/agent knowledge bases** at runtime — governed by CR-012 (Enterprise Intelligence).

The boundary with EO is sharp: ESA owns *how meaning is organised architecturally*; EO owns *what is formally asserted*. ESA's outputs reference EO's outputs; EO's outputs cite ESA's patterns.

## Scope

In scope:

- Repository scaffold + grounding documents (CHARTER, TENETS, axioms).
- Pattern library (`patterns/`) for semantic layer architectures, concept-graph topologies, vocabulary governance, semantic-interoperability patterns.
- Build guide (`BUILD-A-SPECIALIZED-ASSET.md`) — the playbook for authoring sector- or industry-specific ESA assets.
- Sectors index (`sectors/`) with the first two sector entries: `telecom-operator` and `cloud-service-providers`.
- Cross-references to OpenDEAM, ECF (`dea-metaframework`), concepts model (`dea-concepts-model`), metamodel (`dea-metamodel`), and the sibling EO repo.
- A `registry-manifest.yaml` declaring registration with `Assessment-Models/assessment-registry` (subject to CR-AR-01 landing).

Out of scope (handled by sibling CRs):

- Formal ontology axioms (CR-EO-01).
- Registry scope extension (CR-AR-01).
- Sector asset *content* (CR-ESA-02 and later).
- ESA Maturity Assessment (CR-ESA-05, lands in `dea-catalog-assessment-tools`).

## Boundaries with sibling CRs

| Concern | Owner | Cross-ref |
|---|---|---|
| Semantic layer architecture (patterns) | ESA | — |
| Vocabulary governance patterns | ESA | — |
| Concept-graph topology patterns | ESA | — |
| Ontology axioms (OWL/RDF classes, properties, restrictions) | EO | ESA patterns reference EO axioms |
| Ontology versioning, packaging, distribution | EO | ESA vocabulary-governance pattern applies |
| Registry scope extension (semantic + ontological) | AR | ESA + EO both register through AR |
| Concept definition (CR-CM-001, `dea-concepts-model`) | CM-001 | ESA + EO axioms reference Concept entries; Concept entries reference ESA patterns |
| Metamodel entities (CR-8, `dea-metamodel`) | CR-8 | ESA + EO assets conform to `dea-metamodel.yaml` entity/relationship types |

The non-overlap table prevents future phases from duplicating or contradicting EO, AR, or CM-001.

## Design constraints

1. **Grounding is the deliverable, not the patterns.** The proposal PR ships CHARTER + TENETS + axioms as the "grounding documents." Pattern library, sectors, and BUILD guide ship as scaffolding (placeholder + index). Sector content ships in Phase 2.
2. **No dependency on CR-EO-01 or CR-AR-01 for landing.** This proposal is independently shippable. Cross-references are forward-pointing only; if EO or AR PRs land first, ESA updates its cross-references post-merge.
3. **No silent OWL/RDF content.** ESA never ships formal ontology axioms. All semantic assets are *architectural* (patterns, topologies, governance rules), never *ontological* (classes, properties, restrictions). If a phase needs to assert a formal ontology axiom, it routes to CR-EO-01.
4. **Tenets are axiom-derived, not invented.** Every ESA tenet traces to the ECF 7×7 axiom grid (`dea-metaframework`) or is explicitly flagged as a sector-specific extension (deferred to CR-ESA-02).
5. **Sectors are referenced, not authored.** The first two sectors (telecom operator, cloud service provider) appear as **index entries** in Phase 1 with placeholder `sectors/<name>/` sub-folders. Authoring sector content is CR-ESA-02.
6. **Registry manifest ships but registration is conditional.** `registry-manifest.yaml` is present at land; actual registration through `Assessment-Models/assessment-registry` waits on CR-AR-01 landing (mirrors how CR-AM-01 paired with the assessment-CI repo).
7. **Land-as-authored.** This CR doc ships verbatim into `change-requests/CR-ESA-01.md`. No silent re-writes.

## Phase plan

Each phase is one future PR. The user picks the first phase after this proposal merges; later phases may shift but the boundaries hold.

| Phase | Scope | First deliverable |
|---|---|---|
| **1** | Grounding docs + axioms (full CHARTER, full TENETS, three axioms, axiom derivation table to ECF) | `CHARTER.md` + `TENETS.md` + `axioms/` |
| **2** | Sector content — telecom operator pair (ESA + EO) | `sectors/telecom-operator/` with ESA-sector-tenets + sector-concept-graph |
| **3** | Sector content — cloud service provider pair (ESA + EO) | `sectors/cloud-service-providers/` |
| **4** | Pattern library (semantic layer architecture, vocabulary governance, concept-graph topology) | `patterns/PATTERN-INDEX.md` + ≥3 patterns |
| **5** | ESA Maturity Assessment prototype | Lands in `Assessment-Models/dea-catalog-assessment-tools` (cross-repo PR) |
| **6** | Additional sectors (banking, healthcare, gov — queued from Pick 7) | `sectors/banking/`, `sectors/healthcare/`, `sectors/government/` |

**Recommended first phase:** Phase 1 (Grounding docs). Without the grounding, sector content (Phase 2–6) would lack the foundational tenets it cites.

## Definition of Done for this proposal PR

The proposal PR ships ONLY:

1. Repository `technehub-labs/dea-semantic-architecture` (private, scaffolded).
2. `README.md` (top-level index + pointer to this CR + pointer to CHARTER).
3. `CHARTER.md` (placeholder section stubs — full prose in Phase 1).
4. `TENETS.md` (placeholder section stubs — full prose in Phase 1).
5. `axioms/` directory with three placeholder axiom files.
6. `patterns/PATTERN-INDEX.md` (placeholder + structural outline).
7. `sectors/SECTOR-INDEX.md` listing telecom-operator + cloud-service-providers as queued (no content yet).
8. `BUILD-A-SPECIALIZED-ASSET.md` (high-level outline — full prose in Phase 4).
9. `change-requests/CR-ESA-01.md` (this doc, verbatim).
10. `change-requests/README.md` row linking this CR.
11. `GOVERNANCE.md` (placeholder — full prose in Phase 4).
12. `CHANGELOG.md` (initial entry).
13. `.github/workflows/ci.yml` (manifest + structural lint, no schema validation).

**Not shipped in this PR:** full CHARTER/TENETS prose, axioms derivation table, pattern bodies, sector content, registry entries, ESA Maturity Assessment.

## Risks

1. **Drift from EO.** ESA and EO must remain complementary; if EO axioms emerge that contradict ESA patterns, federation convergence suffers. Mitigation: Phase 1 in each repo explicitly cross-references the other; CR-ESA-02 / CR-EO-02 are *paired* sector-content CRs.
2. **Concept-model overlap.** `dea-concepts-model` (CR-CM-001) already owns concept definitions. ESA must not redefine concepts; it cites them. Mitigation: Phase 1 axiom derivation explicitly lists which Concept entries each axiom references.
3. **Naming collision with industry terms.** "Enterprise Semantic Architecture" has multiple informal meanings in industry (semantic web, knowledge graph, data fabric). The CHARTER must define ESA's specific scope in OpenDEA — not the industry umbrella. Mitigation: Phase 1 places a "Scope and non-scope" section in CHARTER upfront.
4. **Empty Phase 0 perception.** A proposal PR with placeholders can look like a shell. Mitigation: the README explicitly states "this is the proposal PR; full grounding lands in Phase 1" and points at the CR doc's Definition of Done.

## Decision points deferred to later phases

- Tenet wording and final axiom set (Phase 1).
- Sector partner selection for telecom + cloud (Phase 2–3 — needs design partners).
- ESA Maturity scoring model (Phase 5 — separate CR on `dea-catalog-assessment-tools`).
- Cross-federation ranking of sectors (Phase 6 — needs user input).

## References

- OpenDEAM: `technehub-labs/dea-architecture-framework` (root authority).
- ECF: `technehub-labs/dea-metaframework` (axiom grid source).
- Concepts Model: `technehub-labs/dea-concepts-model` (CR-CM-001).
- Metamodel: `technehub-labs/dea-metamodel` (CR-8; 1.0.0).
- Sibling: CR-EO-01 (Enterprise Ontology).
- Parallel: CR-AR-01 (assessment-registry scope extension).