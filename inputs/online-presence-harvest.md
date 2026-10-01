---
type: online-presence-harvest
subject: "[[Yves Langeraert]]"
status: extraction-result
stage: harvest
source-register: "[[inputs/online-presence]]"
interpretation-status: not-performed
captured: 2026-09-29
---

# Online presence harvest

This file contains observations extracted from the sources in
[`online-presence.md`](online-presence.md). Each observation is source-bound:
it records what a source contains, not what that content means about Yves.

The harvest is intentionally separate from both the source register and the
person-first model. It can be refreshed when a source changes without changing
the source inventory or silently rewriting model entries.

## Extraction rules

- Preserve the source's wording and context.
- Record retrieval limitations and missing context as observations.
- Keep organizational language separate from personal statements.
- Do not infer capability, authorship, ownership, motivation, or identity.
- Do not assign a person-model lens here; that belongs to the transform stage.

## Observations

| Observation ID | Source ID | Extracted observation | Status |
|---|---|---|---|
| `O-001` | `online-linkedin` | The indexed profile uses the name Yves Langeraert and the public handle `yveslangeraert`; it lists profile, education, credentials, articles, and public activity. | observed; direct profile unavailable |
| `O-002` | `online-linkedin` | The indexed snapshot lists [[KU Leuven]] education and credentials or courses concerning data, programming, security, and architecture. | observed; independently unvalidated |
| `O-003` | `online-linkedin` | The indexed snapshot lists articles and activity concerning AI, software projects, privacy, responsible disclosure, information asymmetry, integrity, leadership, and humane interaction. | observed; linked material not individually inspected |
| `O-004` | `online-researchgate` | The profile lists terms including machine learning, pattern recognition, feature extraction, data clustering, machine intelligence, applied AI, prediction, classification, and supervised learning. | observed vocabulary |
| `O-005` | `online-deep-transformation` | The membership page is associated with Yves Langeraert, but the page was not substantially readable during retrieval. | observed association; unresolved |
| `O-006` | `research-burden-covid-primary-care` | The publication describes a nationwide Belgian primary-care monitoring effort involving electronic medical records, data collection, reporting, visualization, and decision support. | publication observation |
| `O-007` | `research-burden-covid-primary-care` | The publication refers to [[Vioras]], [[Doclr]], and Yves Langeraert in its source context and acknowledgements. | association observed; contribution scope open |
| `O-008` | `covid-barometer` | The barometer document contains a healthcare-data and monitoring context and describes Yves Langeraert as data architect in the source material. | source wording observed |
| `O-009` | `belgian-parliament-doclr` | The public record contains a Doclr context and names Yves Langeraert in a director and shareholder relationship at the time described. | historical public-record observation |
| `O-010` | `doclr-primary-care-article` | The article contains a Doclr context involving primary-care technology, online scheduling, data, privacy, and AI-supported routing. | context observed |
| `O-011` | `doclr-website` | The website presents Doclr as an online scheduling and appointment system for medical practices. | product observation |
| `O-012` | `paronella-smals-record` | The public record connects Paronella and Doclr with a 2021 Smals procurement concerning an appointment platform for vaccination. | company and contract observation |
| `O-013` | `docleas-partnership` | The Docleas page names a partnership involving Partheas, Doclr, Syrinx, and 3S. | partnership observation |
| `O-014` | `partheas-contract` | The Partheas announcement describes a Flemish Government framework contract for appointments, customer support, and digital reception. | contract observation |
| `O-015` | `impute-company-record` | The public company record lists Impute consulting as an active Belgian commanditaire vennootschap founded in 2018 for business and management consultancy. | company observation |
| `O-016` | `helleborus-company-record` | The public company record lists Helleborus as an active Belgian commanditaire vennootschap founded in 2022. | company observation; purpose open |
| `O-017` | `vioras-company-record` | The public record connects Vioras with Fun to work with and records a historical statutory-manager relationship. | historical company observation |
| `O-018` | `fountain-of-love-linkedin` | The organization profile uses language concerning sovereignty, trustworthiness, emotional clarity, responsible AI fluency, living language, governance, and co-creation. | organizational language only |
| `O-019` | `fountain-of-love-github` | The organization profile exposes repositories including `operating-model`, `mml-machine-modelled-language`, `gemstones`, and `py-crystal-seed`. | repository association observed; authorship open |
| `O-020` | `medium-di-comment` | The comment attributed to Yves Langeraert discusses dependency injection and repository architecture in an Angular context. | attributed public expression |

## Boundaries carried forward

- A same-name golf professional is not part of this harvest.
- Search snippets and indexed snapshots are discovery or retrieval evidence,
  not substitutes for inspecting the underlying source.
- Organizational language is not a personal statement.
- Acknowledgement or association is not automatically authorship, ownership,
  contribution, or capability.
- A missing or inaccessible source does not establish absence.

## Handoff

The next stage is [online-presence transform](online-presence-transform.md),
which may interpret selected observations through an explicitly named lens and
identify a proposed load target. No observation becomes a model entry merely by
being listed here.
