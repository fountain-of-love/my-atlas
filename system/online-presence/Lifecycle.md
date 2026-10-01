# Online Presence Input Lifecycle

The lifecycle of processing an online-presence input should remain distinct
from the person-first model and from the outputs generated from that model.

A controlled ETL lifecycle is:

```text
discover search routes
→ register online sources
→ harvest source-bound observations
→ transform observations through an explicit lens
→ review and validate model candidates
→ load validated material into source/
```

The artifacts have separate responsibilities:

| Stage | Artifact | Responsibility |
|---|---|---|
| Extract input | [`inputs/online-presence.md`](../../inputs/online-presence.md) | Source URLs, identity boundaries, and retrieval status |
| Extract output | [`inputs/online-presence-harvest.md`](../../inputs/online-presence-harvest.md) | Observations that point back to registered sources |
| Transform | [`inputs/online-presence-transform.md`](../../inputs/online-presence-transform.md) | Lens-specific interpretation and proposed model targets |
| Load | `source/` | Canonical or explicitly provisional model entries and evidence objects |

These are operational stages for creating and processing an evidence-bearing
input. Person-level interpretation, validation of personal meaning, and
integration into `source/` happen after this input stage.

## Stage boundaries

### 1. Discover search routes

Identify names, domains, platforms, repositories, documents, and links that may
lead to relevant public sources. Search results are candidates, not evidence.

### 2. Register online sources

Follow public links and record URLs, titles, source types, dates, access status,
and linked entities. The crawler may expand the field but may not explain what
the field means about the person.

### 3. Harvest observations

Read the source itself where possible. Record what it says, shows, lists, or
links. Preserve the source's wording and context; do not upgrade an
acknowledgement into authorship or an association into ownership.

### 4. Transform through a lens

Interpret selected observations through one explicitly named person-level lens.
The result is a provisional model candidate, not a validated claim. Preserve
the observation IDs and the intended load target.

### 5. Review and validate

Review transformation boundaries, currentness, authorship, personal meaning,
and any other uncertainty before loading into the model.

### 6. Load into the model

Load only candidates that have passed the required validation gate. Preserve the
observation IDs, source URLs, transform ID, and validation decision in the
resulting model entry or evidence object.

Only the load stage creates or updates person-first source entries and evidence
objects. The source register and harvest remain reversible and are never
backfilled with the resulting interpretation.

## Stop conditions

Stop and mark the boundary when:

- the source cannot be inspected directly;
- a page exposes only a search snippet or profile summary;
- identity is ambiguous;
- a source uses organizational or third-person language without personal attribution;
- a statement would require motive, capability, ownership, authorship, or meaning;
- private or sensitive context is supplied without an explicit publication decision.

In each case, record the limitation and create a bounded follow-up route.

They are governed through **Orchestration / Program**, carried out through
**Execution / Actors**, connected and transformed through **Coordination /
Process**, informed through **Inference / Input**, and expressed through
**Design / Output**.

The lifecycle therefore operates through the five-element system. It is not a
replacement for it.

The canonical mapping remains stable:

```text
Input   ↔ Inference
Output  ↔ Design
Process ↔ Coordination
Program ↔ Orchestration
Actors  ↔ Execution
```

What changes across levels is not the grammar, but the field being observed and
the content occupying each position. The input lifecycle must not be mistaken
for the person's Interaction, Growth, or Behaviour.
