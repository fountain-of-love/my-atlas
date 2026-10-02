# My Atlas System

This folder is the system-facing layer of My Atlas. It is beginning to show
its own shape through reusable concepts, processing capabilities, and domain
applications, while still carrying the foundations from which it emerged.

The system is not a second source of truth about Yves. The canonical material
about Yves lives in [`source/`](../source/README.md). The system describes how
that material can be understood, developed, connected, processed, and
expressed.

## System map

```text
foundations        → inherited field, vocabulary, and working grammar
atlas-system.md    → observations about the system becoming itself
dictionary.md      → shared semantic vocabulary
skills/            → reusable processing capabilities
online-presence/   → first domain-specific system application
```

The recent education work has exposed another system concern: the Atlas must
track both where a claim came from and how a context may have contributed to
the person. These are related but different lineages.

```text
source lineage:
source → extraction → evidence → context → claim

developmental lineage:
context → formative contribution → tension or reinforcement → capability → identity
```

## Foundations

The documents in [`foundations/`](foundations/) are the retained bootstrap
layer. Their content remains relevant, but they are not treated as the final
system architecture. They describe the field in which the newer system has
started to emerge:

- [Ontology](foundations/ontology.md) — possible concepts and relationships;
- [Process](foundations/process.md) — the working loop for developing the Atlas;
- [Ingestion](foundations/ingestion.md) — bringing existing material into the source model;
- [Self-model](foundations/self-model.md) — the five person-level lenses;
- [Direction](foundations/direction.md) — why and how the Atlas moves;
- [Tensions](foundations/tensions.md) — the pressures held open in the field;
- [Dances](foundations/dances.md) — movements observed across those tensions.

These are connected foundations, not a discarded archive. When the emerging
system develops a clearer form, it should refine, absorb, split, or supersede
them through explicit links and preserved lineage.

## Emerging system

- [Atlas system observations](atlas-system.md) — harvested observations, provisional capabilities, operating principles, and questions about what is emerging;
- [Dictionary](dictionary.md) — shared vocabulary for Yves, Enigma, readers, and tools;
- [Processing skills](skills/README.md) — reusable capabilities for source cartography, signal extraction, and provenance weaving;
- [Online Presence Meta-System](online-presence/README.md) — a domain application for observing public presence and routing evidence into the person-first model.

## Boundary and flow

```text
inputs/ → foundations/ingestion.md + skills/ → source/ → outputs/
                         ↑
                 atlas-system.md
```

Inputs remain evidence-bearing material until they are processed and
validated. The source remains canonical. Outputs are views. The system learns
from this flow and from the repository’s own revisions, but should not turn
every useful observation into a fixed component prematurely.

The system should use the person-facing material to produce efficient,
inspectable synthesis. It should not give equal weight to every input: a
foundational degree, a short tool course, a work context, and a current
reflection may play different developmental roles. Weight and decay belong to
interpretation, not to source extraction, and must remain visible as
provisional judgement.

## How to work here

Read the smallest connected set of documents needed for the task. Use the
foundations to understand inherited meaning, `atlas-system.md` to understand
what is currently emerging, and the domain folders for concrete applications.
Keep observations, interpretations, validated knowledge, and system design
decisions distinct. Let recurring use and evidence earn further formalisation.
