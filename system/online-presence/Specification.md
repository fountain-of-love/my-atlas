# Online Presence Specification

## Required document shape

The document should become more semantically precise as it goes deeper. It
does not need to become less readable or turn into a database dump.

### 1. File identity

Use minimal front matter to describe the file itself:

```yaml
---
type: online-presence-result
subject: "[[Person]]"
captured: YYYY-MM-DD
status: discovery-result
---
```

Front matter answers: “What kind of file is this, what does it concern, and
when was it captured?” Do not repeat `type` in the body unless the second use
names a genuinely different concept.

### 2. Orientation

Begin with a short subject-first overview. State:

- who or what the result concerns;
- the broad shape of the public presence;
- the strongest recurring contexts;
- what remains uncertain;
- how the result should be used.

The first screen should answer “What is this about?” before asking the reader
to understand the processing machinery.

### 3. Field and presence map

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

### 4. Evidence and interpretation

Keep these levels visibly distinct:

```text
source → observation → claim → inference → validated knowledge
```

- **Source**: where the material came from.
- **Observation**: what the source directly contains or establishes.
- **Claim**: a statement the Atlas may tentatively make.
- **Inference**: a meaning or pattern derived across observations.
- **Validated knowledge**: a claim accepted after appropriate checking, ideally
  including validation by the subject where personal meaning is involved.

Never let an inference silently become an observation. Use qualifiers such as
`candidate`, `possible`, `unresolved`, `corroborated`, and `validated` where
they materially change the meaning.

### 5. Program, process, and execution

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

### 6. Lessons and candidate knowledge

Describe what the field reveals about the subject, but keep conclusions
proportional to the evidence. This section may contain:

- recurring themes or patterns;
- candidate capabilities, interests, values, or ways of working;
- relationships worth investigating;
- contradictions or changes over time;
- lessons about the source material itself;
- questions that cannot yet be answered.

Phrase these as routes into the canonical model, not as a finished biography.
For example, prefer `candidate-domain:: data architecture` over an
unsupported definitive capability claim.

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
broad → contextual → evidential → interpretive → operational
```

A reader may stop after the overview; an investigator can continue into
evidence; an agent can use the source index and processing state.

### Prose and structure together

Prose carries meaning and nuance. Inline fields make important entities,
relationships, provenance, and state inspectable. Neither should be allowed to
replace the other.

### Reversible interpretation

Keep candidate interpretations easy to revise or withdraw. Prefer links to
deeper concepts over absorbing every concept into this file. Preserve empty or
unknown fields rather than manufacturing completeness.

### One source of truth

The result maps and routes evidence. Once material is validated and integrated,
the person-first source entries become canonical. Outputs such as profiles,
CVs, or portfolio pages should be views generated from that source.

## Minimal template

```markdown
---
type: online-presence-result
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

## Evidence and interpretation

Separate sources, observations, claims, inferences, and validated knowledge.

## Program, process, and execution

Record scope, priority, stage, roles, skills, permissions, and the next
scheduled actions.

## Lessons and candidate knowledge

Record recurring patterns, promising routes, changes, contradictions, and open
questions.

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
