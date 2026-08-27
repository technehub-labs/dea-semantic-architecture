# Changelog

## [Unreleased]

### Phase 2 proposal (CR-ESA-02) — Telecom-Operator Enterprise Semantic Architecture

#### Added
- **`change-requests/CR-ESA-02.md`** — Telecom-Operator Enterprise Semantic Architecture (Phase 2) spec. Implements the 2026-08-27 directive: two-axis split (business-area / technology-area) + technology-area sub-split (natively-reusable big topics / technology-type / domain-specific). Includes the explicit **Phasing rule** (PR-1 visible deliverable, PR-2 visible evolution path, PR-3 visible split, PR-4 visible evolution path before content lands) per the directive's "methodical and incremental" requirement. Paired with CR-EO-02 (cross-pillar lock-step). The semantic-layer stack (vocab / taxonomy / thesaurus / kg) is duplicated per-area and per-reusability-subset, mirroring the formal ontology split on the EO side.

### Pending (per CR-ESA-02 phase plan)

- Phase 2.1 — Sector README + sector-declaration tenet (area + reusability framework; no semantic-layer content).
- Phase 2.2 — Sector tenet extensions (extensions to base Tenets 1, 2, 3 with ECF derivation; vocabulary governance declaration).
- Phase 2.3a — Business-area semantic-layer stack (vocab, taxonomy, thesaurus, kg).
- Phase 2.3b — Technology-area reusable semantic layers (referenced from EO-02's `ontology/technology/reusable/`).
- Phase 2.3c — Technology-area telecom-type semantic layers (referenced from EO-02's `ontology/technology/type/`).
- Phase 2.3d — Technology-area domain-specific stubs (namespace + README only).
- Phase 2.4 — Concept-graph edge-kind inventory + cardinality rules.
- Phase 2.5 — Per-vocabulary lifecycle declarations.
- Phase 2.6 — `registry-entry.yaml` + AR entry (cross-repo PR).
- Phase 2.7 — Paired EO-02 formal ontology (cross-repo PR).

### Phase 1 (CR-ESA-01) — Grounding docs — MERGED (`4ffff6a`, PR #1)

#### Added
- **Full `CHARTER.md`** — core meaning, OpenDEA placement, scope and non-scope, sibling relationships, authority boundaries, reversibility, naming taste, ECF derivation (§1–8).
- **Full `TENETS.md`** — three tenets with full ECF derivation tables:
  - Tenet 1 — Semantic layers are architectural, not accidental (6 ECF cells; Operations × Design, Product × {Build, Activate, Operate, Improve}, Governance × Operate).
  - Tenet 2 — Vocabulary governance is a first-class discipline (5 ECF cells; Governance × {Conceive, Design, Activate, Improve, Retire}).
  - Tenet 3 — Concept graphs admit multiple edge kinds, not just hierarchies (5 ECF cells; Customer × Activate ★, Product × {Design, Operate, Improve}, Operations × Build ★).
- **Three axiom files** with ECF derivation tables + operational rules + anti-patterns:
  - `axioms/axiom-01-semantic-layer-discipline.md`
  - `axioms/axiom-02-vocabulary-governance.md`
  - `axioms/axiom-03-concept-graph-topology.md`
- **Updated `axioms/README.md`** — derivation table, sector-extension methodology, pattern/registry cross-references.

### Pending (per CR-ESA-01 phase plan)

- Phase 2: First sector pair (telecom operator — paired with CR-EO-02).
- Phase 3: Cloud service provider sector (paired with CR-EO-03).
- Phase 4: Pattern library + full BUILD-A-SPECIALIZED-ASSET.md + GOVERNANCE.md.
- Phase 5: ESA Maturity Assessment (cross-repo PR on `Assessment-Models/dea-catalog-assessment-tools`).
- Phase 6: Additional sectors (banking, healthcare, government).