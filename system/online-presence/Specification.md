# Online Presence Specification

## Required document shape

The document should become more semantically precise as it goes deeper. It
does not need to become less readable or turn into a database dump.

The online-presence process is an ETL pipeline. The source register lists
online sources, the harvest records source-bound observations, the transform
interprets selected observations through an explicit lens, and the load stage
updates the person-first model. None of these stages is a biography, profile
interpretation, capability assessment, or automatic person-first source entry.

### 1. File identity

Use minimal front matter to describe the file itself:

```yaml
---
type: online-presence-source-register
subject: "[[Person]]"
captured: YYYY-MM-DD
status: source-inventory
---
```

Front matter answers: “What kind of file is this, what does it concern, and
when was it captured?” Do not repeat `type` in the body unless the second use
names a genuinely different concept.

### 2. Source register

The source register contains URLs, source types, identity boundaries, access
status, and retrieval limitations. It must not contain extracted observations.
Use one row per distinct online source and give each source a stable ID.

### 3. Harvest

The harvest reads the source register and records observations that point back
to a source ID. An observation states what the source contains, including
retrieval limitations and unresolved identity boundaries. It must not interpret
the person or assign a model meaning.

### 4. Transform

The transform selects observations and interprets them through an explicitly
named person-level lens. Every transformation records its observation IDs,
lens, provisional interpretation, confidence, validation requirement, and
proposed load target.

### 5. Load

The load stage writes validated or explicitly provisional model entries and
evidence objects to `source/`. It preserves the source IDs, observation IDs,
original URLs, transform ID, and validation state. It must not rewrite the
source register or harvest to fit the model.

### 6. Orientation

Begin with a short subject-first overview. State:

- who or what the result concerns;
- the broad shape of the public presence;
- the strongest recurring contexts;
- what remains uncertain;
- how the result should be used.

The first screen should answer “What is this about?” before asking the reader
to understand the processing machinery.

### 7. Field and presence map

Describe the input field and the public entities visible within it. Keep these
entities distinct from the execution roles that process the result. Include
only entities relevant to the current result, such as:

- profiles and platforms;
- people and identity anchors;
- organisations and institutions;
- projects, repositories, publications, performances, or works;
- technologies, domains, audiences, and communities.

For each important context, record the relationship to the subject without
silently upgrading association into authorship, ownership, employment, or
capability.

Useful inline fields include:

```text
source-id::
source-type::
source-url::
subject::
entity::
relationship::
domain::
status::
```

The vocabulary is open enough to support different media. For example,
`source-type:: repository-profile`, `source-type:: artist-profile`,
`source-type:: publication`, and `source-type:: portfolio` may all be valid.

### 8. Evidence and lens contribution

Keep the input observational. Record what the source contains and which
person-level lenses it may contribute to, without forming the person-level
claim in the input itself.

Keep these levels visibly distinct:

```text
source → observation → lens contribution → model candidate → validated knowledge
```

- **Source**: where the material came from.
- **Observation**: what the source directly contains or establishes.
- **Lens contribution**: the person-level lens or lenses to which an observation may be relevant.
- **Model candidate**: a provisional statement created later during ingestion into `source/`.
- **Validated knowledge**: a claim accepted after appropriate checking, ideally
  including validation by the subject where personal meaning is involved.

Never let a lens contribution silently become a claim. Use qualifiers such as
`possible`, `unresolved`, `corroborated`, and `validated` where they materially
change the meaning.

For crawl work, “lens contribution” is optional routing metadata only. Prefer
search topics, linked entities, and follow-up routes when a lens label would
invite interpretation. A crawl may say “this source contains the term
`software architecture`” or “review for a possible Behaviour route”; it may not
say “the person is a software architect” or “this demonstrates a capability.”

### 9. Program, process, and execution

Make the work plan and its enactment inspectable. The program states what is
in scope and what should happen; the process orders and schedules that work;
execution records the roles and skills that perform it.

Useful fields include:

```text
review-scope::
priority::
dependency::
stage::
role::
skill::
permission::
```

For example, a source may be assigned to a researcher for inspection, a
subject for validation, and a curator for integration. An agent may extract
observations but not validate personal meaning. These are execution contracts,
not claims about the subject's public identity.

The minimum execution contract is:

| Role | Output |
| --- | --- |
| Crawler | Candidate URLs, source register, retrieval status, search routes |
| Source inspector | Source-bound observations with provenance |
| Evidence curator | Normalized entities, duplicates, contradictions, and boundaries |
| Subject / validator | Confirmation, correction, qualification, or rejection |
| Source integrator | Validated model candidates and canonical source entries |
| Reviewer / gatekeeper | Boundary decision and release approval |

No role may silently perform the next role's work. In particular, a crawler or
inspector may not perform source integration.

### 6. Lens contribution map

Map observations to the person-level lenses without interpreting the person.
This section may contain:

- observations that may contribute to **Experience**;
- explicit expressions that may contribute to **Identity**;
- observed relationships or collaborations that may contribute to **Interaction**;
- explicit directions or recurring time-based signals that may contribute to **Growth**;
- demonstrated work or practices that may contribute to **Behaviour**;
- uncertainty, contradiction, or missing evidence affecting the route.

Use fields such as `lens-contribution:: Experience` or
`lens-contribution:: Behaviour` next to the relevant observation. Phrase the
entry as an observation and route, not as a finished biography or capability
claim. Interpretation belongs in the person-first model during ingestion.

### 7. Boundaries and uncertainty

State what must not be inferred. Typical boundaries include:

- same-name identities;
- search snippets versus inspected sources;
- organisational language versus personal claims;
- acknowledgement versus authorship or contribution;
- repository association versus authorship or ownership;
- public availability versus permission to reproduce sensitive detail;
- absence of evidence versus evidence of absence.

Boundaries are part of the result, not an appendix. They protect the subject
and keep later agents from producing semantic inflation.

### 8. Source index and processing state

End with a compact source index and an operational state. The index is the
machine-oriented inventory; the earlier sections remain the human-facing map.

Recommended processing fields:

```text
processed::
validated-by-subject::
source-entries-created::
evidence-objects-created::
claims-extracted::
relationships-extracted::
next-step::
```

`next-step` should describe one useful, bounded action, such as selecting one
publication for deep ingestion or reviewing one portfolio source. It makes the
result executable without making it autonomous or final.

## Design principles

### Living variety with sufficient structure

The schema should be invariant at the level of meaning, not at the level of
media. A GitHub portfolio, SoundCloud page, research profile, and personal
website can all be represented as public contexts and source objects, while
their local fields describe the medium-specific evidence.

Use shared fields for cross-domain concepts (`subject`, `source-type`,
`relationship`, `evidence-status`, `boundary`) and local prose or scoped fields
for domain-specific detail.

### Progressive disclosure

The recommended order is:

```text
broad → contextual → evidential → lens-routed → operational
```

A reader may stop after the overview; an investigator can continue into
evidence; an agent can use the source index and processing state.

### Prose and structure together

Prose carries meaning and nuance. Inline fields make important entities,
relationships, provenance, and state inspectable. Neither should be allowed to
replace the other.

### Reversible routing

Keep lens contributions easy to revise or withdraw. Prefer links to deeper
concepts over absorbing interpretation into this file. Preserve empty or
unknown fields rather than manufacturing completeness.

### One source of truth

The result maps and routes evidence. Once material is validated and integrated,
the person-first source entries become canonical. Outputs such as profiles,
CVs, or portfolio pages should be views generated from that source.

## Minimal template

```markdown
---
type: online-presence-input
subject: "[[Person]]"
captured: YYYY-MM-DD
status: discovery-result
---

# Online presence

Short subject-first overview: what is visible, where, and with what degree of
confidence.

## Presence map

Describe platforms, works, organisations, projects, audiences, and domains.
Keep relationship and identity status explicit.

## Evidence and lens contribution

Separate sources, observations, lens contributions, and processing state.

## Program, process, and execution

Record scope, priority, stage, roles, skills, permissions, and the next
scheduled actions.

## Lens contribution map

Record which observations may contribute to Experience, Identity, Interaction,
Growth, or Behaviour. Do not form the person-level interpretation here.

## Boundaries

Record identity, provenance, contribution, privacy, and absence boundaries.

## Source index

List source IDs, types, URLs, subjects, contexts, and statuses.

## Processing state

processed:: false
validated-by-subject:: false
source-entries-created:: false
evidence-objects-created:: false
claims-extracted:: false
relationships-extracted:: false
next-step::
```
