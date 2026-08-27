# CR-ESA-02 — Telecom-Operator Enterprise Semantic Architecture (Phase 2)

> **Paired with [CR-EO-02](./CR-EO-02.md)** — telecom-operator sector content lands in lock-step across both pillars. The two CRs share Phase boundaries and a single phase-pick menu; review both before proceeding.

## Status

- **State:** Proposed — awaiting explicit Proceed / numbered picks.
- **Series tag:** `CR-ESA` (Enterprise Semantic Architecture).
- **Sibling CR:** `CR-EO-02` (telecom-operator Enterprise Ontology) — same phase boundaries; this CR's semantic-layer architecture references CR-EO-02's area + reusability split.
- **Predecessors:** `CR-ESA-01` (Phase 1 MERGED — `4ffff6a` on `technehub-labs/dea-semantic-architecture`); `CR-AR-01` (Phase 1 MERGED — assessment-registry scope extension runtime enables `asset_class: semantic` registration).
- **Successors (parked):** CR-ESA-03 (cloud service provider sector — paired with CR-EO-03); CR-ESA-04 (Phase 4 promotion of `dea-catalog-ontologies` — fintech + healthcare semantic-architecture parallel); CR-ESA-05 (Phase 6 ESA Maturity Assessment on `Assessment-Models/dea-catalog-assessment-tools`).
- **Visibility target:** Private at land; promoted to public after this Phase ships (mirroring ESA-1 / EO-1 promotion pattern).

## Primary objective

Deliver the first sector-specific **Enterprise Semantic Architecture asset** under [`technehub-labs/dea-semantic-architecture`](https://github.com/technehub-labs/dea-semantic-architecture) — for the **telecom operator** sector — with a structural separation between the **business-area** and the **technology-area** of the sector, and within the technology-area an explicit subset of **natively-reusable big topics** that are referenced (not redefined) from the EO shared primitives (CR-EO-02's `reusable/` subset).

The deliverable establishes the pattern every future sector semantic-asset follows; the telecom choice is the proving ground for the area + reusability split on the semantic-architecture side.

## Why now

ESA-01 Phase 1 grounded the discipline (CHARTER + TENETS + three axioms with ECF derivation). Without a first sector, the discipline has no concrete instantiation. Telecom was chosen as the first pair because:

1. The sector has the deepest existing semantic-asset ecosystem in industry (TMForum SID/ODA, GSMA, ONF, 3GPP, MEF, ETSI ZSM).
2. The reuse-from-existing is highest here, and the cross-sector reuse case for the technology-area is strongest here (telecom radio/RAN, OSS/BSS, charging, identity, network-as-a-service primitives are reused by other sectors).
3. ESA must demonstrate it can organise meaning around the same area + reusability axes that EO formalises — otherwise the two pillars drift.

The user's 2026-08-27 directive specified the architectural split:
> "For the telecom ontology we need to separate business-area from technology-area in order to manage the evolution. Also within technology area there will be the key big topics that are natively reusable, and those that are technology type and domain specific."

This CR implements that directive on the semantic-architecture side, paired with CR-EO-02 on the ontology side.

## Architectural principle

**The telecom-operator Enterprise Semantic Architecture asset is organised along the same two orthogonal axes that CR-EO-02 uses: area (business / technology) and reusability (reusable / type / domain).**

### Axis 1 — area (business / technology)

The semantic-layer stack (vocabulary → taxonomy → thesaurus → ontology → knowledge graph) is duplicated *within each area*, not collapsed into a single asset. This mirrors EO-02's `ontology/business/` vs `ontology/technology/` split.

| Area | Semantic layers | ESA asset |
|---|---|---|
| **business-area** | `vocab/business/`, `taxonomy/business/`, `thesaurus/business/`, `kg/business/` (the ontology layer is imported from EO-02's `ontology/business/`) | `sectors/telecom-operator/business/` |
| **technology-area** | `vocab/technology/reusable/`, `vocab/technology/type/`, `vocab/technology/domain/`, plus the same taxonomy / thesaurus / kg split | `sectors/telecom-operator/technology/` |

### Axis 2 — reusability (within technology-area only)

The reusable big-topic vocabularies / taxonomies are referenced (not redefined) from the EO shared primitives in `eo-shared-technology-primitives` (sibling repo, per Pick 4 of CR-EO-02). The technology-type vocabularies are sector-internal (reused across operators but not promoted cross-sector). The domain-specific vocabularies are operator-private extensions.

| Subset | ESA-side role | EO-side parallel |
|---|---|---|
| **natively-reusable big topics** | Vocabularies / taxonomies / thesauri referencing the EO shared primitives (skos:Concept + skos:broader + skos:related edges referencing the EO `owl:Class` and `owl:ObjectProperty` definitions). | EO axioms in `ontology/technology/reusable/`. |
| **technology-type** | Vocabularies / taxonomies for telecom-type concerns (3GPP NFs, TMForum SID entities, GSMA identifiers) — referenced from EO axioms in `ontology/technology/type/`. | EO axioms in `ontology/technology/type/`. |
| **domain-specific** | Operator-private vocabularies — placeholder namespace + README; populated by individual operators. | EO stubs in `ontology/technology/domain/` only. |

### Why the split (mirrored from CR-EO-02)

1. **Evolution management.** Business-area semantic assets change slowly (vocabulary additions for new products); technology-area semantic assets change faster (vocabulary additions for new network functions). Conflating them creates noisy change logs. Separating them lets each area evolve at its own cadence.
2. **Reuse factoring.** The natively-reusable subset is the *prime candidate* for cross-sector promotion on the ESA side (vocabularies that span sectors). Until you explicitly separate it, you cannot factor it out.
3. **Cross-discipline discipline.** ESA must mirror the same axes as EO. If ESA collapsed them and EO split them, the semantic-layer architecture would drift from the formal ontology. Paired CRs prevent drift.

## Scope

### In scope

- **Phase 2.1 — `sectors/telecom-operator/` directory tree.** Per the `SECTOR-INDEX.md` convention, the directory contains `README.md`, `vocab/`, `taxonomy/`, `thesaurus/`, `kg/`, `tenets/`, `registry-entry.yaml`. Content, not scaffolding.
- **Phase 2.2 — `tenets/` content.** Sector-specific tenet extensions to all three base ESA tenets, mirroring the area + reusability classification scheme of CR-EO-02. Each tenet extension cites the same ECF cells as CR-EO-02's parallel extensions (cross-pillar coherence).
- **Phase 2.3 — semantic-layer content.** Per-axis:
  - `vocab/business/` — business-area vocabularies (Product, Service, Customer, Order, Bill, Regulatory Obligation, …).
  - `taxonomy/business/` — broader/narrower edges between the business-area vocabularies.
  - `thesaurus/business/` — related edges between the business-area vocabularies.
  - `kg/business/` — knowledge-graph assertions (instances + relationships, referencing EO axioms).
  - `vocab/technology/reusable/` — vocabularies for natively-reusable big topics (referenced from EO shared primitives).
  - `taxonomy/technology/reusable/`, `thesaurus/technology/reusable/`, `kg/technology/reusable/` — same layers, reusable subset.
  - `vocab/technology/type/` — telecom-type vocabularies (3GPP NFs, TMForum SID entities, GSMA identifiers).
  - `taxonomy/technology/type/`, `thesaurus/technology/type/`, `kg/technology/type/` — same layers, type subset.
  - `vocab/technology/domain/` — domain-specific stubs (operator-private extensions; placeholder namespace + README only).
- **Phase 2.4 — concept-graph topology declaration.** The sector's concept graph declares its edge-kind inventory per Axiom 3 (broader / narrower / related / equivalent / mapped-from), with cardinality rules. The edge-kind inventory cites the ECF cells per Axiom 3.
- **Phase 2.5 — vocabulary governance declaration.** Per Axiom 2, every vocabulary declares its lifecycle policy (proposed → candidate → active → legacy → deprecated → retired), owner, and deprecation path. The vocabulary's status is auditable via the assessment-registry's `status` field.
- **Phase 2.6 — `registry-entry.yaml`.** Registration record for `Assessment-Models/assessment-registry` under `asset_class: semantic`, with `compatibility` block declaring axes per `axes/catalog.yaml`.
- **Phase 2.7 — paired EO sector content.** CR-EO-02 ships the parallel formal ontology for the same sector, with the same area + reusability split.

### Out of scope (handled by sibling CRs)

- EO-side formal axioms for the same sector → CR-EO-02 (paired).
- Cloud service provider sector → CR-EO-03 / CR-ESA-03 (next pair).
- `dea-catalog-ontologies` promotion (fintech + healthcare) → CR-EO-04 / CR-ESA-04 (Phase 4).
- Pattern library (semantic layer architectures, vocabulary governance patterns, concept-graph topology patterns) → EO-01 / ESA-01 Phase 4.
- `BUILD-A-SPECIALIZED-ASSET.md` full prose → ESA-01 Phase 4.
- ESA Maturity Assessment → CR-ESA-05 (Phase 6).
- Additional sectors (banking, healthcare, government) → Phase 7.

## Boundaries with sibling CRs

| Concern | Owner | Cross-ref |
|---|---|---|
| Telecom semantic-layer architecture (this CR) | ESA-02 | EO-02 axioms implement ESA-02 semantic-layer architecture |
| Telecom formal OWL/RDF axioms + area + reusability split | EO-02 | ESA-02 semantic-layer architecture references EO-02 area split |
| Sector upper-ontology choice + reasoning profile | EO-02 | ESA-02 vocabulary governance respects EO-02 profile |
| Sector lifecycle policy (semver + mapping-to-replacement) | EO-02 | ESA-02 vocabulary lifecycle policy aligns with EO-02 ontology lifecycle |
| Cross-sector reusable technology primitives | EO-02 (extracted to `eo-shared-technology-primitives` or EO `axioms/reusable/` per Pick 4) | ESA-02 vocabularies / taxonomies / thesauri reference the shared primitives |
| Cross-ontology mappings (TMForum SID, 3GPP, GSMA, …) | EO-02 | ESA-02 `kg/` instances reference the EO-02 mappings |
| Registry entry for telecom sector | EO-02 + ESA-02 (paired) | Both register through AR (CR-AR-01) |
| Phase 4 promotion of `dea-catalog-ontologies` (fintech + healthcare) | CR-EO-04 / CR-ESA-04 | Telecom patterns inform promotion mechanics |

## Design constraints

1. **Two-axis split is non-negotiable.** Per the 2026-08-27 directive (same as CR-EO-02). Every vocabulary / taxonomy / thesaurus / KG file declares its area and reusability classification in the asset's frontmatter / metadata.
2. **No conflation across the split.** Business-area semantic assets must not import technology-area semantic assets; technology-area semantic assets may import business-area semantic assets only when the technology serves the business. The directionality is one-way: business-area is upstream.
3. **Reusable subset is referenced, not redefined.** Per Pick 4 of CR-EO-02, the natively-reusable big topic vocabularies are *references* to the EO shared primitives — never copies. Violations (i.e. redefined vocabularies that mirror EO primitives) are non-conformant.
4. **Concept-graph edge-kind inventory per Axiom 3.** Every sector concept graph declares its edge-kind inventory with cardinality rules. Concept graphs with no edge-kind discipline are non-conformant.
5. **Vocabulary governance per Axiom 2.** Every vocabulary declares its lifecycle policy (proposed → candidate → active → legacy → deprecated → retired), owner, deprecation path.
6. **Methodical + incremental.** Per the 2026-08-27 directive. Each phase lands in a single PR with full scorecard + verification; no big-bang rollouts.
7. **No content outside the telecom sector.** This CR ships telecom content only. Cloud-service-provider and other sectors are deferred to CR-EO-03+.
8. **Land-as-authored.** This CR doc ships verbatim into `change-requests/CR-ESA-02.md`. Sector content lands in paired ESA/EO sector folders; both go through a phase-pick review before any Phase 2.x PR is opened.

## Phasing rule (per the 2026-08-27 directive)

Every Phase 2.x PR for the telecom-operator sector MUST satisfy four explicit, visible conditions before it can be merged. These conditions are non-negotiable; they exist to ensure the area + reusability split and the evolution path are *demonstrable* in every PR, not merely declared in the CR doc. The ESA side mirrors the EO side verbatim (Constraint 9 in CR-EO-02); both CRs enforce the same rule on their respective sides.

| # | Condition | What it produces (visible artifact) | Why |
|---|---|---|---|
| **PR-1** | **Visible deliverable.** Each PR ships a checked-in artifact (file, manifest, registry entry, diagram) — not merely a doc or plan. | The diff for the PR is the deliverable; reading the diff shows the split in action. | Splits that live only in docs drift. The artifact is the proof. |
| **PR-2** | **Visible evolution path.** Each PR's `CHANGELOG.md` entry in `sectors/telecom-operator/` shows the prior state → new state delta in tabular form, naming every vocabulary / taxonomy / thesaurus / KG assertion / edge-kind rule that changed. | A row per PR with columns `what`, `where` (ECF cell / tenet / edge kind / vocabulary), `area` (business / technology-reusable / technology-type / technology-domain), `why`, `impact on reusable subset` (none / added / reclassified / deprecated). | Evolution cannot be managed if it is not visible. The table makes the split auditable. |
| **PR-3** | **Visible split.** The PR diff must demonstrate the area + reusability classification for every new artifact: the frontmatter / metadata block on every semantic-layer file declaring the area + reusability; the directory placement under `vocab/{business,technology/{reusable,type,domain}}/`, `taxonomy/{...}/`, `thesaurus/{...}/`, `kg/{...}/`. | One PR cannot add a business-area vocabulary that *also* declares itself technology-reusable — the split is enforced by the directory + the frontmatter, not by convention. | Conflation across the split is the failure mode the directive targets; making it visible prevents it. |
| **PR-4** | **Visible evolution path before content lands.** Phase 2.1 (sector README + sector declaration tenet) explicitly shows the evolution path of the sector: the order in which subsequent phases add content, the reusability-subset boundary that gates Phase 2.3b, the cross-sector candidate list. Phase 2.2 (tenet extensions) explicitly shows the evolution path of each tenet extension: which base axiom it extends, which ECF cells it populates, what triggers a reclassification. | A reader of `sectors/telecom-operator/README.md` + `tenets/` files can answer "what changes next, and why" without reading the CR doc. | Evolution managed visibly is evolution managed. The CR is a planning artifact; the sector folder is the running record. |

### PR-gate checklist (every Phase 2.x PR)

Each PR's description MUST include:

```
## PR-gate checklist (CR-ESA-02 / CR-EO-02 Phasing rule)

- [ ] PR-1 — Visible deliverable: list every new file under `sectors/telecom-operator/...` with a one-line summary
- [ ] PR-2 — Visible evolution path: include a CHANGELOG.md delta table (what / where / area / why / impact on reusable subset)
- [ ] PR-3 — Visible split: confirm every new artifact has its area + reusability classification declared in frontmatter / directory placement
- [ ] PR-4 — Visible evolution path before content lands: confirm the previous phase's evolution-path declaration is updated by this PR (cite the file + line)
- [ ] Cross-pillar coherence: confirm any vocabulary / taxonomy / thesaurus that references an EO axiom declares the cross-reference (so the EO-02 paired PR can pick it up)
```

A PR that fails any of the four conditions is non-conformant; review is blocked until the conditions are met. The CR-EO-02 paired CR applies the same rule on the formal-ontology side.

### Reclassification protocol (Constraint 6 + Phasing rule)

When a sector semantic asset moves between reusability classifications (e.g. a vocabulary originally in `vocab/technology/type/` is later identified as cross-sector reusable and moves to `vocab/technology/reusable/`), the move is itself a Phase. It triggers:

1. A sector-tenet amendment citing the new ECF cells populated.
2. A CHANGELOG.md delta row with `impact on reusable subset: reclassified`.
3. A mapping-to-replacement declaration (Axiom 2 of ESA-01 — vocabulary governance) on the original location, so consumers that referenced the old vocabulary continue to resolve.
4. A registry entry update (CR-AR-01 §Phase 1 axes coherence).

Reclassification is **not** a silent rename; it is a first-class lifecycle event under the phasing rule. The paired EO-side reclassification follows the same protocol on the formal-ontology side.



## Phase plan

Each phase is one future PR. Phase 2.1 lands first; Phase 2.7 (paired EO content) lands last in this CR cycle.

| Phase | Scope | First deliverable |
|---|---|---|
| **2.1** | `sectors/telecom-operator/` directory + `README.md` declaring the area + reusability split (mirroring CR-EO-02) | Sector README + `tenets/01-sector-declaration.md` |
| **2.2** | Sector tenet extensions (extensions to base Tenets 1, 2, 3 of ESA-01 with ECF derivation, area + reusability classification per tenet) | `tenets/02-tenet-extensions.md` + `tenets/03-vocabulary-governance-declaration.md` |
| **2.3a** | Business-area semantic-layer stack: vocab, taxonomy, thesaurus, kg | `vocab/business/*.ttl`, `taxonomy/business/*.ttl`, `thesaurus/business/*.ttl`, `kg/business/*.ttl` |
| **2.3b** | Technology-area reusable semantic layers (referenced from EO-02's `ontology/technology/reusable/`) | `vocab/technology/reusable/*.ttl` etc. |
| **2.3c** | Technology-area type semantic layers (referenced from EO-02's `ontology/technology/type/`) | `vocab/technology/type/*.ttl` etc. |
| **2.3d** | Technology-area domain-specific stubs (placeholder namespace + README only) | `vocab/technology/domain/README.md` |
| **2.4** | Concept-graph edge-kind inventory + cardinality rules | `tenets/04-edge-kind-inventory.md` |
| **2.5** | Per-vocabulary lifecycle declarations | `governance/vocabulary-lifecycle.yaml` |
| **2.6** | `registry-entry.yaml` + sector entry on `Assessment-Models/assessment-registry` under `asset_class: semantic` | PR on AR repo (cross-repo) |
| **2.7** | **Paired CR-EO-02 deliverable** — telecom-operator formal ontology with area + reusability split | Cross-repo PR on `technehub-labs/dea-ontology` |

**Recommended first phase:** Phase 2.1 (sector README + sector-declaration tenet) — establishes the area + reusability classification framework for ESA without committing to specific semantic-layer content yet. Subsequent phases layer content on top.

## Definition of Done for this proposal PR

This proposal PR ships ONLY:

1. Repository state — `technehub-labs/dea-semantic-architecture` at Phase 1 merged state (currently `4ffff6a`).
2. `change-requests/CR-ESA-02.md` (this doc, verbatim).
3. `change-requests/README.md` row linking this CR.

**Not shipped in this PR:** sector content (lives in Phase 2.1–2.7); vocabulary governance declarations (Phase 2.5); registry entry (Phase 2.6); EO-side sector content (CR-EO-02, parallel).

## Risks

1. **Over-decomposition of the reusable subset.** Risk: the natively-reusable set becomes so large it is no longer "minimal at first." Mitigation: hard cap of 5–8 topics for Phase 2.3b; selection criteria must clear "used in at least one other sector candidate" bar or be on a documented cross-sector roadmap (mirrored from CR-EO-02).
2. **Concept-graph cardinality drift.** Risk: the edge-kind inventory declared in Phase 2.4 diverges from how operators actually model their telecom-domain concepts. Mitigation: edge-kind inventory cites the same ECF cells as Axiom 3; cross-checked with TMForum SID concept-graph conventions.
3. **Reusable-reference vs redefinition.** Risk: sector semantic assets redefine vocabularies that should have referenced EO shared primitives. Mitigation: explicit Constraint 3; CI lint that flags vocabularies whose labels match EO primitive labels without a reference declaration.
4. **Cross-sector vocabulary scope creep.** Risk: TMForum SID, GSMA, ONF, 3GPP, MEF, ETSI ZSM, ODA — too many vocabularies to reference in one cycle. Mitigation: Phase 2.3b references the three Pick-3 selections only; additional references ship in Phase 7+ per sector.
5. **Drift from EO side.** Risk: ESA-02 area + reusability split diverges from EO-02 area + reusability split. Mitigation: paired CRs with shared Pick 1 (area + reusability classification scheme); the two sectors mirror each other.
6. **Empty Phase 2.1 perception.** Risk: Phase 2.1 (sector README + sector declaration tenet) looks trivial. Mitigation: the sector README carries the area + reusability classification framework, which is the structural foundation — every subsequent semantic-layer file inherits from it.

## Decision points deferred to later phases

- Specific reusable big topics (Phase 2.3b — picks must match EO-02's Pick 4 reusable subset).
- Vocabulary governance owner (Phase 2.1 — needs a design partner; placeholder `tbd`).
- Concept-graph edge-kind inventory (Phase 2.4 — picks must respect EO-02's mapped axioms).
- Lifecycle policy owner per vocabulary (Phase 2.5).

## References

- [CR-ESA-01 — Enterprise Semantic Architecture umbrella](https://github.com/technehub-labs/dea-semantic-architecture/blob/main/change-requests/CR-ESA-01.md) (MERGED Phase 1).
- [CR-EO-02 — Telecom-Operator Enterprise Ontology (paired)](./CR-EO-02.md).
- ECF: [`technehub-labs/dea-metaframework`](https://github.com/technehub-labs/dea-metaframework).
- Concepts Model: [`technehub-labs/dea-concepts-model`](https://github.com/technehub-labs/dea-concepts-model).
- Metamodel: [`technehub-labs/dea-metamodel`](https://github.com/technehub-labs/dea-metamodel) (CR-8; 1.0.0).
- Sibling: CR-ESA-01 (Enterprise Semantic Architecture grounding — MERGED Phase 1).
- Parallel: CR-AR-01 (assessment-registry scope extension runtime — MERGED Phase 1).
- Predecessor (Phase 4 promotion target): [`technehub-labs/dea-catalog-ontologies`](https://github.com/technehub-labs/dea-catalog-ontologies).
