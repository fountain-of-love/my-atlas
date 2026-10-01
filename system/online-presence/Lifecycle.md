# Online Presence Input Lifecycle

The lifecycle of processing an online-presence input should remain distinct
from the person-first model and from the outputs generated from that model.

A controlled lifecycle is:

```text
discover search routes
→ crawl and register sources
→ inspect source
→ record observations
→ map optional topic/lens routes
→ review boundaries and gaps
→ validate meaning where required
→ route validated material to source ingestion
```

These are operational stages for creating and processing an evidence-bearing
input. Person-level interpretation, validation of personal meaning, and
integration into `source/` happen after this input stage.

## Stage boundaries

### 1. Discover search routes

Identify names, domains, platforms, repositories, documents, and links that may
lead to relevant public sources. Search results are candidates, not evidence.

### 2. Crawl and register sources

Follow public links and record URLs, titles, source types, dates, access status,
and linked entities. The crawler may expand the field but may not explain what
the field means about the person.

### 3. Inspect source

Read the source itself where possible. Record what it says, shows, lists, or
links. Preserve the source's wording and context; do not upgrade an
acknowledgement into authorship or an association into ownership.

### 4. Record observations

Write source-bound observations. Each observation must answer “what does this
source contain?” and point back to the source. Retrieval limitations and
unreadable sections are observations too.

### 5. Map optional topic/lens routes

Add search topics or possible routes to Experience, Identity, Interaction,
Growth, or Behaviour only as processing metadata. A route says where to inspect
next; it does not say what the person is like.

### 6. Review boundaries and gaps

Check same-name identities, missing context, search snippets, stale pages,
organizational language, privacy limits, and contradictions. Record unresolved
questions rather than resolving them narratively.

### 7. Validate meaning where required

Ask the subject or another designated validator to confirm identity, current
status, personal meaning, or sensitive context. Validation is a separate act
from crawling and must be recorded separately.

### 8. Route validated material to source ingestion

Only the source-integration stage may create claims, model candidates, or
canonical person-first entries. The crawl remains reversible evidence and is
never backfilled with the resulting interpretation.

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
