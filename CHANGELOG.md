# Changelog

## [Unreleased]

### Phase 1 (CR-ESA-01) — Grounding docs

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