# Sectors — Index

> **Status:** placeholder. Sector content lands in Phase 2–3 (telecom operator + cloud service provider), Phase 6 (banking, healthcare, government).

## Queued sectors

| Sector | Status | Phase |
|---|---|---|
| `telecom-operator/` | queued | Phase 2 (paired with CR-EO-02) |
| `cloud-service-providers/` | queued | Phase 3 (paired with CR-EO-03) |
| `banking/` | queued | Phase 6 |
| `healthcare/` | queued | Phase 6 |
| `government/` | queued | Phase 6 |

Each sector sub-folder (when content lands) will contain:

- `README.md` — sector scope, audience, design partners.
- `tenets/` — sector-specific tenets (the base tenets + sector extensions).
- `semantic-architecture/` — ESA-sector assets for the sector.
- `registry-entry.yaml` — registration record (subject to CR-AR-01 landing).

Sector content is **authored via a sector-content CR** (e.g. `CR-ESA-02` for telecom operator), not directly into this repo without a CR.