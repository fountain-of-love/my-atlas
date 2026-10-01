---
type: online-presence-transform
subject: "[[Yves Langeraert]]"
status: transform-staged
stage: transform
input: "[[inputs/online-presence-harvest]]"
load-root: "[[source]]"
captured: 2026-09-29
---

# Online presence transform

This file is the transform boundary between harvested observations and the
person-first model. A transform must name the lens it applies, state the
interpretation it makes, preserve the observation IDs it uses, and identify a
proposed load target.

Transform is not extraction. It is also not validation: interpretations that
depend on personal meaning, current status, authorship, or ownership remain
provisional until reviewed.

## Transform contract

```text
observation + explicit lens
    → provisional model candidate
    → validation decision where required
    → load into source/ entry or evidence object
```

Required fields for each transform:

| Field | Meaning |
|---|---|
| `transform-id` | Stable identifier for the interpretation |
| `observation-ids` | Harvest observations used as input |
| `lens` | One of Experience, Identity, Interaction, Growth, Behaviour |
| `interpretation` | Provisional meaning through that lens |
| `confidence` | Provisional confidence and unresolved limits |
| `validation-needed` | Whether subject or independent validation is required |
| `load-target` | Intended `source/` or evidence destination |
| `load-status` | `proposed`, `validated`, or `loaded` |

## Current transform queue

| Transform ID | Observation IDs | Lens | Provisional interpretation | Validation needed | Load target | Status |
|---|---|---|---|---|---|---|
| `T-001` | `O-002` | Learning | LinkedIn lists education, certifications, and courses in data, programming, security, and architecture. | credential and significance review; category interpretation | `source/evidence/education/linkedin-education.md` and `source/contexts/learning/` | loaded as observed-unvalidated |
| `T-002` | `O-003` | Experience / Interaction | LinkedIn exposes public articles and activity across technical, organizational, privacy, and relational topics. | inspect linked items and subject meaning | `source/contexts/experiences/linkedin-public-activity.md` | loaded as observed-unvalidated |
| `T-003` | `O-006`, `O-007`, `O-008`, `O-009`, `O-010` | Experience / Behaviour | Public sources describe a healthcare-data and primary-care technology context connected with Doclr, Vioras, monitoring, reporting, and visualization. | contribution and authorship scope review | `source/contexts/experiences/business-contexts.md` and evidence objects | loaded as observed-unvalidated |
| `T-004` | `O-013`, `O-014`, `O-015`, `O-016`, `O-017` | Experience | Public sources establish company and partnership contexts; they do not establish Yves's current participation or personal purpose. | current role and participation review | `source/contexts/experiences/business-contexts.md` | loaded as observed-unvalidated |
| `T-005` | `O-018`–`O-019` | Interaction / Identity | Fountain of Love material is an organizational and repository context that may require separate personal attribution analysis. | authorship, ownership, and personal relation review | future evidence object | proposed |
| `T-006` | `O-020` | Behaviour | The public comment is a concrete instance of engagement with dependency injection and repository architecture. | attribution and context review | future evidence object | proposed |

## Load rule

Only validated or explicitly marked observed-unvalidated candidates may be
loaded into `source/`, and the load must preserve the observation IDs and
original URLs. A load updates the model; it must never update the source
register or rewrite the harvest to make the model fit.
