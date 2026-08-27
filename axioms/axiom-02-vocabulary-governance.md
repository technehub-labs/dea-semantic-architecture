# ESA Axiom 02 — Vocabulary governance is a first-class discipline

**Tenet:** See [../TENETS.md#tenet-2--vocabulary-governance-is-a-first-class-discipline](../TENETS.md#tenet-2--vocabulary-governance-is-a-first-class-discipline).

**Status:** Phase 1 of [../../change-requests/CR-ESA-01.md](../../change-requests/CR-ESA-01.md). Full ECF derivation.

## Statement

Vocabularies are versioned, deprecated, mapped, and retired; they are never silently evolved. The governance rules are explicit, owned, and auditable.

## ECF derivation

**Principles:** Lifecycle continuity (every business object passes through every stage) and Traceability (every cell traces to an owner, a state, and a set of dependencies) — from [dea-metaframework/framework/principles.md §3 and §6](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Vocabulary as an ECF business object:** A vocabulary is an entity (per the Constructs §Entity definition). Its lifecycle is a path through the seven stages. The Governance domain (row 1) owns the lifecycle policy because governance is the precondition for boundedness — and a vocabulary without a bounded lifecycle is not a vocabulary, it is a soup.

| Stage | Vocabulary-governance activity | ECF cell |
|-------|-------------------------------|----------|
| Conceive | Policy intent: declare the vocabulary's purpose + ownership + lifecycle policy | Governance × Conceive (1×1) |
| Design | Controls design: versioning rules, deprecation policy, mapping declaration rules, ownership chain | Governance × Design (1×2) |
| Build | Compliance build: authoring the vocabulary's first candidate version | Governance × Build (1×3) |
| Activate | Enforce: the vocabulary's governance policy goes live; mapping declarations are auditable | Governance × Activate (1×4) |
| Operate | Assurance: ongoing audits for silent evolution; the vocabulary's status is reported via the assessment-registry | Governance × Operate (1×5) |
| Improve | Risk review: detect silent evolution; flag vocabulary governance failures | Governance × Improve (1×6) |
| Retire | Policy retire: deprecation mapping to successor or retirement archive | Governance × Retire (1×7) |

**State values** (from [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) CR-AM-11 §26 + CR-AR-01 Phase 1):
`proposed` → `candidate` → `active` → `legacy` → `deprecated` → `retired`.

## Operational rule

Every vocabulary in a sector ESA asset declares:

1. **Lifecycle policy** — the path through the six state values, with explicit transitions.
2. **Deprecation path** — what asset replaces it when retired; what mappings make the transition lossless.
3. **Owner** — an actor (per the ECF Actor construct) with the authority to declare lifecycle transitions.
4. **Registry status** — registered with `Assessment-Models/assessment-registry` under `asset_class: semantic` (per CR-AR-01 Phase 1).

The vocabulary's lifecycle status is auditable via the assessment-registry's `status` field; the asset's `notes` field carries the deprecation path; the asset's `owner` is declared in its `components` or `notes` block.

## Anti-patterns

- **Silent evolution** — changing a vocabulary's meaning without declaring a version bump. (Governance × Operate assurance failed.)
- **Silent deprecation** — marking a vocabulary deprecated without announcing its successor. (Governance × Improve risk review failed.)
- **Ownerless vocabulary** — a vocabulary without an explicit owner is governance-failed by definition. (Traceability principle violated.)

## Cross-references

- [../TENETS.md §2](../TENETS.md#tenet-2--vocabulary-governance-is-a-first-class-discipline) — the tenet.
- [../CHARTER.md §6](../CHARTER.md#6-reversibility) — reversibility (vocabulary lifecycle enables asset reversibility).
- [CR-ESA-04](./../../change-requests/CR-ESA-01.md#phase-plan) — Pattern family 2 (vocabulary governance patterns) expands this axiom.
