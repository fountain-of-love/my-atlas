# Online Presence Meta-System

The Online Presence Meta-System defines how a person's publicly observable presence is discovered, observed, structured, validated, and routed into the person-first source model.

It does not itself describe a person's public presence, and an online-presence input is not itself the person model. It governs how public evidence can enter the Atlas without allowing source material, processing mechanics, or provisional observations to become a finished interpretation.

The following boundaries should remain distinct:

1. **Public Presence Field**  
    The distributed public reality being observed: profiles, repositories, publications, performances, websites, organisations, communities, interactions, chronology, metadata, relationships, and other observable traces.
    
2. **Online Presence Input**
    A source register for the public field. It lists sources, identity boundaries, provenance, and retrieval state. It does not contain extracted observations or interpret the person.

3. **Online Presence Harvest**
    An extraction artifact containing source-bound observations from the
    registered sources. It preserves provenance and uncertainty but does not
    interpret the person.

4. **Online Presence Transform**
    A staged interpretation of selected observations through an explicitly
    named person-level lens. It produces provisional model candidates and
    proposed load targets; it is not itself canonical knowledge.
    
5. **Person-first Model**
    The canonical source model of the person. Validated material from inputs is integrated here under the person-level lenses: Experience, Identity, Interaction, Growth, and Behaviour.

6. **Outputs**
    Views generated from the person-first model for a particular audience or purpose, such as a profile, portfolio, CV, website, or context package.

7. **Online Presence Meta-System**
    The reusable system that defines how online-presence inputs are produced, governed, evaluated, improved, and routed into the model.

The core ETL flow is:

```text
public presence field
        ↓ register
online-presence source register
        ↓ harvest
source-bound observations
        ↓ transform
provisional lens-specific candidates
        ↓ validate and load
person-first model
        ↓ select and express
outputs
```
    

The canonical model remains person-first. An input is evidence about a person's public field, not a definitive biography, CV, or statement of capability. It should preserve room for the subject's source model to evolve and support different forms of public expression later.

## Input principles

The source register and its downstream artifacts should:

- identify the public contexts in which the subject appears;
- distinguish sources, observations, transformations, and processing state;
- preserve provenance, uncertainty, and explicit boundaries;
- support relationships between observations and underlying evidence;
- indicate which person-level lenses an observation may contribute to;
- expose enough structure for later human or machine processing;
- remain inputs rather than becoming a second source of truth.
    

Interpretation and model formation happen after harvesting, during the
transform and load stages. The source register and harvest must not silently
turn a source or observation into a claim about the person.

## Extract contract

The online-presence source register is an inventory, not an interpretation. The
harvest is an extraction record, not an interpretation.

Its job is to grow the searchable field by recording:

- URLs, profiles, repositories, publications, organizations, and linked entities;
- what each inspected source visibly contains;
- source dates, access dates, provenance, and retrieval limitations;
- repeated names, topics, terms, relationships, and routes for further search;
- contradictions, missing pages, ambiguous identities, and unresolved questions;
- possible lens destinations, explicitly marked as routing only.

The input must not:

- describe the person as having a capability, value, trait, motivation, or identity;
- convert a profile label into a validated role, ownership, authorship, or contribution;
- synthesize recurring topics into a person-level pattern;
- resolve ambiguity by intuition or narrative coherence;
- use phrases such as “this shows that Yves...” or “Yves is...” unless the source
  is a direct, attributable self-statement and the wording remains an observation;
- create claims, model candidates, or canonical source entries.

The operational rule is simple:

```text
register identifies the source
harvest records what it contains
transform states what it may mean through a lens
validation checks the candidate
load creates or updates model knowledge
```

If a sentence cannot be supported by pointing to the inspected source itself,
it does not belong in the source register or harvest. It belongs in the
transform stage, a validation record, `source/`, or the separate subject-
supplied `inputs/harvest.md`, depending on what kind of statement it is.

## Roles, skills, and permissions

Roles describe work performed on the input. They must not be confused with
roles or identities found in the public sources.

| Role | Responsibility | Required skills | May do | Must not do |
| --- | --- | --- | --- | --- |
| Crawler | Expand the public search field | Web search, browsing, URL tracing, access logging | Find links, follow source trails, record retrieval status | Interpret the person or validate a claim |
| Source inspector | Read an individual source | Close reading, provenance capture, source comparison | Record direct observations and exact source context | Generalize beyond the source |
| Evidence curator | Normalize the crawl | Information architecture, deduplication, uncertainty handling | Group sources, preserve boundaries, mark contradictions | Turn repeated observations into person-level conclusions |
| Subject | Validate personal meaning and identity | First-person context, correction, consent judgment | Confirm, reject, qualify, or contextualize observations | Be treated as automatically validating public evidence |
| Source integrator | Process validated material into `source/` | Domain modeling, claim construction, traceability | Create model candidates and canonical source entries after validation | Backfill interpretations into the crawl |
| Reviewer / gatekeeper | Enforce the contract | Boundary review, epistemic hygiene, audit discipline | Block semantic drift and require provenance | Quietly rewrite evidence as narrative |

### Stage gate

Every transition must leave an inspectable artifact:

| Transition | Required artifact | Gate |
| --- | --- | --- |
| Discover → Crawl | Search routes and candidate URLs | No candidate is treated as evidence yet |
| Crawl → Inspect | Source register with access status | A source must be identifiable and retrievable, or marked unavailable |
| Inspect → Observe | Observation record with source pointer | Wording stays source-bound |
| Observe → Route | Optional lens/topic route | Route is not a conclusion |
| Route → Validate | Review queue | Subject or designated validator sees what requires confirmation |
| Validate → Integrate | Validation decision and provenance | Only then may source integration create person-level knowledge |

## The canonical five-element system

The Online Presence architecture uses one canonical five-element system expressed through two equivalent lenses.

| Structural view | Functional view   |
| --------------- | ----------------- |
| **Input**       | **Inference**     |
| **Output**      | **Design**        |
| **Process**     | **Coordination**  |
| **Program**     | **Orchestration** |
| **Actors**      | **Execution**     |

These mappings remain invariant across system levels.

The content occupying each element may change depending on whether we are looking at the Meta-System or at the person-first Model, but the relationship between the structural and functional views does not change.

A useful diagnostic lens is:

|Functional view|Structural view|Guiding question|
|---|---|---|
|**Inference**|**Input**|What enters the system and what can be sensed from it?|
|**Design**|**Output**|What form does the system create?|
|**Coordination**|**Process**|How are things related, transformed, compared, or validated?|
|**Orchestration**|**Program**|What governs, directs, prioritises, and constrains the work?|
|**Execution**|**Actors**|Who or what performs the work?|

## Meta-System instantiation

At the Meta-System level, the five elements describe how the Online Presence system itself learns and evolves.

| Structural view | Functional view   | Online Presence Meta-System meaning                                                                                                                                                                            |                                   |
| --------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| **Input**       | **Inference**     | Experience generated by operating the system: processed inputs, recurring patterns, reviewer feedback, uncertainty, edge cases, failures, successful approaches, new source types, and lessons learned. |                                   |
| **Output**      | **Design**        | The evolving form of the system: schemas, specifications, templates, heuristics, evidence models, validation structures, reusable patterns, and design changes.                                                | [specification](specification.md) |
| **Process**     | **Coordination**  | The ways observations, lessons, feedback, specifications, and proposed changes are related, compared, evaluated, validated, and integrated.                                                                    | [lifecycle](lifecycle.md)         |
| **Program**     | **Orchestration** | The governing logic that directs how inputs are created and how the Meta-System evolves: principles, priorities, boundaries, routing rules, validation policies, dependencies, and cadence.            |                                   |
| **Actors**      | **Execution**     | The humans and machine capabilities that operate and evolve the system: subject, researcher, curator, reviewer, agent, crawler, parser, API, validator, and other executable capabilities.                     |                                   |

At this level, inference concerns the system itself.

For example:

```
several processed inputs reveal that
repository activity alone can misrepresent a person's public presence

→ meta-system inference:
source importance depends on context and presence type

→ meta-system design:
introduce a source-selection heuristic and broader corroboration rules
```

The resulting heuristic becomes part of the Meta-System and influences future inputs and model integrations.

## Input-level lens contribution

The online-presence pipeline does not instantiate a second person model. Its
harvest records observations and its transform routes provisional candidates
toward the existing person-level lenses.

|Person lens|What an online-presence observation may contribute|
|---|---|---|
| **Experience** | Observed history, contexts, prior roles, education, projects, influences, and recurring material across time. |
| **Identity** | Explicit self-description, roles, values, worldview, positioning, style, and forms of expression. |
| **Interaction** | Observed relationships, collaborations, communities, audiences, communication, and movement between contexts. |
| **Growth** | Explicit direction, current pursuits, recurring questions, priorities, or trajectories visible in the material. |
| **Behaviour** | Demonstrated work, capabilities in context, methods, tools, practices, contributions, and ways of working. |

These are contribution routes, not conclusions. The input records what is visible and where it may be useful; the person-first model determines what it means after comparison, validation, and integration.

## Input is a field, not merely a document

Within this model, Input should not be interpreted too narrowly as a file or document.

Input represents what enters the system boundary and becomes available for inference.

For an online-presence input, this may include:

- individual source documents;
    
- repositories and their structure;
    
- publication histories;
    
- interactions between sources;
    
- chronology;
    
- recurring themes;
    
- relationships between people and organisations;
    
- community participation;
    
- metadata;
    
- repetition;
    
- absence;
    
- contradictions;
    
- contextual signals;
    
- changing patterns over time.
    

A document is therefore one possible carrier of input, not the definition of Input itself.

Likewise, at the Meta-System level, individual public sources are generally not the primary Input. The relevant Input is the experience generated through producing, reviewing, maintaining, and comparing online-presence inputs and model integrations.

## System boundaries

The person-first Model is the canonical place where validated observations become statements about Yves. The online-presence input remains evidence-bearing and reversible. The Meta-System learns from processing experience, not by treating each input as a self-contained model.

Outputs are downstream views. They may compress, select, and express the model differently, but they do not replace it.

```
many processed inputs
        ↓
experience and recurring patterns
        ↓
Meta-System Inference
        ↓
Meta-System Design
        ↓
improved specifications, heuristics, and governance
        ↓
future inputs and model integrations
```
