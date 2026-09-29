The example actually exposes a useful distinction between **note metadata** and **ontology expressed by the note's content**.

For this particular file, I would make the top-level Properties deliberately minimal, and move the richer semantic structure into inline fields.

### I’d aim for something like this

```
---
type: online-presence-result
subject: Yves Langeraert
captured: 2026-09-29
status: discovery-result
---
```

Then, in the body:

```
# Online presence

type:: result
subject:: [[Yves Langeraert]]
result-kind:: online-presence
capture-status:: discovery
identity-confidence:: high

This is a structured snapshot of publicly discoverable material associated
with [[Yves Langeraert]]...
```

And then let the body establish the ontology:

```
## Identity anchor

subject:: [[Yves Langeraert]]
identity-status:: coherent-cluster
location:: [[Leuven]]
institution:: [[KU Leuven]]

The supplied profile URLs and the connected research, technology, and
organizational references form a coherent identity cluster around...

## Public profiles

### LinkedIn

entity:: [[Yves Langeraert]]
source-type:: professional-profile
identity-status:: supplied-primary
url:: https://www.linkedin.com/in/yveslangeraert/
processing-value:: current-public-expression

### ResearchGate

entity:: [[Yves Langeraert]]
source-type:: research-profile
identity-status:: strong-match
url:: https://www.researchgate.net/profile/Yves-Langeraert
```

That gives you an important separation:

- **Properties at the top** = _What kind of file is this? What does it represent? When/how was it captured?_
    
- **Inline fields** = _What entities, relationships, claims, evidence, boundaries, and classifications does this document contain?_
    
- **Ordinary prose** = _What does the source actually say?_
    

I think that is a much more natural fit for the kind of knowledge system you're building.

### One thing I'd change in your current structure

I wouldn't duplicate `type` like this:

```
type: online-presence-result
```

and then:

```
type:: result
```

unless they genuinely mean different things.

Instead, give the two concepts different names if they represent different ontology levels. For example:

```
---
type: research-result
subject: [[Yves Langeraert]]
captured: 2026-09-29
status: discovery-result
---
```

Then:

```
## Online presence

result-domain:: online-presence
```

Or perhaps:

```
document-type:: result
result-domain:: online-presence
```

That distinction becomes particularly valuable later when you're querying the vault.

### I would also reconsider the large YAML block at the bottom

Your:

```
identity:
  name: Yves Langeraert
  location: Leuven, Belgium
  confidence: high
```

is essentially **ontology encoded as a data structure inside the prose**.

If your goal is to make the vault genuinely queryable, I'd probably turn that into normal Obsidian fields:

```
## Identity

subject:: [[Yves Langeraert]]
location:: [[Leuven]]
identity-confidence:: high
```

Likewise:

```
contexts:
  - id: context-doclr-vioras
    type: technology-healthcare
    entities: [Doclr, Vioras, KU Leuven, primary care]
```

could become something much more Obsidian-native:

```
## Vioras and Doclr research trace

context-type:: technology-healthcare
entities:: [[Doclr]], [[Vioras]], [[KU Leuven]], [[Primary care]]
```

Now the **ontology is visible where it is being asserted**, rather than being hidden in a machine-readable appendix.

### There's an even more interesting consequence

You can make the YAML header almost function like the **identity card of the file**:

```
---
type: online-presence-result
subject: [[Yves Langeraert]]
captured: 2026-09-29
status: discovery-result
---
```

Everything else becomes the **knowledge contained by the file**.

That's a very clean conceptual boundary:

> **Frontmatter describes the document. Inline fields describe the world represented by the document.**

And importantly, this doesn't mean the inline fields have to be scattered randomly through the prose. You can use headings as **semantic scopes** and inline fields as the explicit ontology within those scopes.

For your particular note, I'd actually go one step further and redesign the whole thing around that principle. The result would probably be **considerably shorter, more readable, and more queryable** than the current YAML-heavy version.

---

Yes. Having read the current Gemstones repository and, more importantly, the specification behind it, I think there is a stronger design available for the **online-presence result** than simply converting YAML into inline fields.

The key insight I would carry over is that a note should have **progressive disclosure**. Your Gemstone spec explicitly separates narrative understanding, navigation, structured knowledge, and in-depth knowledge, while using links as the mechanism by which the reader moves into deeper domains. GitHub+1 

For the online-presence note, I would therefore make the document itself an **interface to an evidence graph**.

## The proposed information architecture

I would structure it roughly like this:

```
1. Metadata
   └── What is this file?

2. Overview
   └── What does this result tell me, in human terms?

3. Navigation
   └── Where can I go from here?

4. Identity
   └── Who/what does this result concern?

5. Presence map
   └── What public contexts are connected?

6. Evidence
   └── What does each source actually establish?

7. Relationships
   └── People, organizations, projects, technologies, institutions...

8. Boundaries
   └── What should NOT be inferred?

9. Candidate knowledge
   └── What might this evidence eventually contribute to?

10. Source index
    └── Machine-oriented inventory

11. Processing state
    └── What has happened to this result?

12. Deep machine interface
    └── Structured material for agents/processes
```

The important thing is that **the document becomes more structured as you descend**.

That's very close to what the Gemstones project is already experimenting with: prose first, structured comparison later, graph links throughout, and domain-specific detail increasingly delegated to deeper concepts. GitHub+1 

---

# I would rewrite your note like this

Below is the design I'd use as the next experiment.

Online presence — progressive-disclosure result

---

## type: online-presence-result  
subject: [[Yves Langeraert]]  
captured: 2026-09-29  
status: discovery-result

# Online presence

This is a structured snapshot of publicly discoverable material associated with [[Yves Langeraert]].

The result brings together public profiles, research traces, organizational connections, and public writing that appear to form a coherent identity cluster. It is intended as **evidence for further investigation**, rather than as a definitive description of the person.

The material is deliberately separated into observations, relationships, possible interpretations, and boundaries. The deeper sections become increasingly structured and are intended primarily for later processing by humans and machines.

## Navigate

- [[#Overview]]
    
- [[#Identity]]
    
- [[#Public presence]]
    
- [[#Research and technology]]
    
- [[#Organizations and projects]]
    
- [[#Evidence]]
    
- [[#Boundaries]]
    
- [[#Candidate knowledge]]
    
- [[#Source index]]
    
- [[#Processing state]]
    

The most useful starting points are the [[#Overview|overview]] and [[#Public presence|public presence]].  
For evidence-level processing, continue to [[#Evidence|Evidence]].  
For machine-oriented inspection, continue toward the [[#Source index|source index]] and [[#Processing state|processing state]].

---

## Overview

The public material currently forms a coherent cluster around [[Yves Langeraert]], [[Leuven]], [[KU Leuven]], [[Doclr]], [[Vioras]], and [[Fountain of Love]].

The strongest recurring themes are technology, data, healthcare, research, software, AI, and organizational or societal questions surrounding technology.

Several different kinds of public evidence contribute to this picture:

- professional and research profiles;
    
- references to work involving Doclr and Vioras;
    
- a research publication concerning Belgian primary care during COVID-19;
    
- public organizational material;
    
- public writing and software-related material.
    

The material should not yet be treated as a finished biography. It is better understood as a **map of publicly observable contexts from which more specific evidence can be extracted**.

The most important distinction is between:

- what a source directly establishes;
    
- what several sources collectively suggest;
    
- what could be investigated further;
    
- what should explicitly remain unclaimed.
    

---

## Identity

subject:: [[Yves Langeraert]]  
identity-confidence:: high  
identity-status:: coherent-public-cluster  
location:: [[Leuven]]  
country:: [[Belgium]]

The supplied profile URLs and connected research, technology, and organizational references form a coherent identity cluster around:

- [[Yves Langeraert]]
    
- [[Leuven]]
    
- [[KU Leuven]]
    
- [[Doclr]]
    
- [[Vioras]]
    
- [[Fountain of Love]]
    

A person with the same name associated with professional golf appears in search material and is treated as a separate identity.

### Identity reasoning

The identity cluster is supported by convergence across several independent contexts rather than by a single source.

The strongest identity anchors currently are the supplied professional profile and the research profile. Organizational and publication references provide additional connections.

identity-evidence:: profile + research + organizational + publication  
identity-boundary:: same-name-golf-professional

---

## Public presence

The public presence can be understood as several different interfaces rather than as one homogeneous online identity.

### Professional profile

source-type:: professional-profile  
identity-status:: supplied-primary  
entity:: [[Yves Langeraert]]  
platform:: [[LinkedIn]]

The supplied professional profile acts as a primary public identity anchor.

Observed associations include [[Fountain of Love]], [[Leuven]], [[KU Leuven]], public articles, AI-related writing, and technical or data-related education and certifications.

The profile is potentially useful for understanding current public self-positioning, activity, project relationships, and social context.

### Research profile

source-type:: research-profile  
identity-status:: strong-match  
entity:: [[Yves Langeraert]]  
platform:: [[ResearchGate]]  
institution:: [[KU Leuven]]  
department:: [[Computer Science]]

The research profile connects Yves Langeraert with [[KU Leuven]] and a vocabulary including:

- machine learning;
    
- pattern recognition;
    
- feature extraction;
    
- data clustering;
    
- machine intelligence;
    
- applied artificial intelligence;
    
- prediction;
    
- advanced machine learning;
    
- classification;
    
- supervised learning.
    

These terms should initially be treated as **profile vocabulary**, not automatically as independently validated capabilities.

### Community membership

source-type:: membership-profile  
identity-status:: supplied  
entity:: [[Yves Langeraert]]  
organization:: [[Deep Transformation Network]]

The supplied membership profile may provide evidence about community affiliation and public positioning.

Its contents require direct review before stronger claims are made.

---

## Research and technology

The strongest research trace currently connects [[Yves Langeraert]], [[Vioras]], and [[Doclr]] with Belgian primary-care data infrastructure.

### COVID-19 primary-care monitoring

evidence-type:: publication  
domain:: [[Primary care]]  
technology-context:: [[Vioras]]  
organization-context:: [[Doclr]]  
institution-context:: [[KU Leuven]]

A 2021 publication concerning the burden of COVID-19 on Belgian primary care describes a nationwide observational monitoring effort.

The research context involved structured electronic forms integrated into general-practice electronic medical records, together with reporting and visualisation for GP circles, primary-care zones, and policy makers.

The publication identifies [[Vioras]] in connection with questions for the monitoring instrument and with reports and visualisations used to identify support needs.

The acknowledgements name [[Yves Langeraert]] in connection with [[Vioras]] and [[Doclr]].

This provides evidence for a context involving:

- healthcare data;
    
- data architecture;
    
- electronic medical records;
    
- monitoring;
    
- reporting;
    
- visualisation;
    
- decision support;
    
- multi-level information flows.
    

It does **not**, by itself, establish the exact individual contribution of Yves Langeraert to every component of the system.

### Technical vocabulary

possible-domain:: software  
possible-domain:: data  
possible-domain:: artificial-intelligence  
possible-domain:: machine-learning  
possible-domain:: healthcare-technology  
possible-domain:: architecture

The public material contains recurring technical vocabulary around data, software architecture, machine learning, AI, healthcare technology, and research.

At this stage these should be treated as **candidate knowledge domains** rather than consolidated capability claims.

---

## Organizations and projects

### [[Doclr]]

relationship:: professional-context  
domain:: healthcare-technology  
evidence-strength:: multiple-public-sources

Public material connects Yves Langeraert with [[Doclr]] in a leadership and technology context.

The public product context concerns online scheduling for medical practices, campaigns, organizations, and entrepreneurs, with emphasis on data protection and integrations.

### [[Vioras]]

relationship:: research-and-technology-context  
domain:: healthcare-data

[[Vioras]] appears in the COVID-19 primary-care research trace as a contributor to the monitoring instrument, reporting, and visualisation context.

### [[Fountain of Love]]

relationship:: organizational-and-project-context  
domain:: technology-and-society

Public organizational material connects [[Fountain of Love]] with themes including:

- sovereignty;
    
- trustworthiness;
    
- emotional clarity;
    
- responsible AI fluency;
    
- living language;
    
- governance;
    
- co-creation.
    

The organizational vocabulary should remain distinct from claims about Yves personally unless independently supported.

### Open-source ecosystem

relationship:: public-project-context  
organization:: [[Fountain of Love]]  
platform:: [[GitHub]]

The public repository ecosystem includes projects such as:

- `operating-model`
    
- `mml-machine-modelled-language`
    
- `spiral-algo-to-polar-algebra-evolution`
    
- `living-mathematics-library`
    
- `py-wordless-meaning`
    
- `fibonacci-blueprint`
    
- `gemstones`
    
- `py-crystal-seed`
    

These repositories may become useful evidence sources, but repository association alone does not establish authorship, contribution, or conceptual ownership.

---

## Evidence

The evidence should be treated as a separate layer from the knowledge eventually derived from it.

### Evidence model

evidence-source:: [[Source]]  
evidence-observation:: [[Observation]]  
evidence-claim:: [[Claim]]  
evidence-inference:: [[Inference]]  
evidence-boundary:: [[Boundary]]

A useful processing rule is:

> Never allow an inference to silently become an observation.

For example:

```
SOURCE
  ↓
OBSERVATION
  ↓
POSSIBLE CLAIM
  ↓
VALIDATION
  ↓
KNOWLEDGE
```

The current document mostly contains observations and candidate routing information.

The next ingestion step should extract individual evidence objects rather than simply making this document longer.

### Strong evidence

The research publication provides a relatively strong connection between:

[[Yves Langeraert]]  
→ [[Vioras]]  
→ [[Doclr]]  
→ Belgian primary-care monitoring  
→ data/reporting/visualisation context

### Supporting evidence

Other public material provides supporting connections involving:

- Doclr leadership;
    
- healthcare scheduling;
    
- data architecture;
    
- public professional identity;
    
- research interests;
    
- organizational activity.
    

### Weak or unresolved evidence

Some search-result material is useful for discovery but should not become canonical evidence without source inspection.

---

## Boundaries

boundary:: identity  
boundary:: provenance  
boundary:: organizational-vs-personal  
boundary:: absence-of-evidence  
boundary:: contribution

The following boundaries should remain explicit.

### Same-name identity

A golf professional with the same name appears in search results and remains outside this identity cluster.

### Search snippets

Search results and snippets are discovery aids rather than canonical evidence.

### Organizational material

Material published by an organization does not automatically constitute a personal statement or personal capability claim.

### Publication acknowledgements

Being acknowledged in a paper does not by itself establish authorship or the full scope of an individual's contribution.

### Public availability

Public availability does not imply permission to reproduce sensitive or unnecessary personal details.

### Absence

The absence of a visible result does not establish the absence of a person, project, capability, or relationship.

---

## Candidate knowledge

This section is deliberately different from a biography.

It asks:

> What knowledge objects should this discovery result potentially feed?

candidate-context:: [[Doclr]]  
candidate-context:: [[Vioras]]  
candidate-context:: [[KU Leuven]]  
candidate-context:: [[Fountain of Love]]  
candidate-domain:: [[Data architecture]]  
candidate-domain:: [[Healthcare technology]]  
candidate-domain:: [[Artificial intelligence]]  
candidate-domain:: [[Machine learning]]  
candidate-domain:: [[Software architecture]]  
candidate-domain:: [[Research]]

### Potential capability evidence

The current material may eventually provide evidence relevant to:

- data architecture;
    
- health-data systems;
    
- machine learning;
    
- AI;
    
- software architecture;
    
- research collaboration;
    
- translating complex information into operational systems.
    

These remain **candidate knowledge routes**, not final conclusions.

### Potential ways-of-working evidence

The material may eventually help investigate whether there is evidence of:

- connecting data with decisions;
    
- translating complex systems into usable infrastructure;
    
- working across technical and societal domains;
    
- building systems at the boundary of technology and human institutions.
    

These questions should be answered through deeper source ingestion rather than inferred from this discovery note.

---

## Source index

The source index is intentionally more machine-readable than the preceding sections.

### Profiles

source-id:: online-linkedin  
source-type:: professional-profile  
subject:: [[Yves Langeraert]]  
status:: supplied-primary

source-id:: online-researchgate  
source-type:: research-profile  
subject:: [[Yves Langeraert]]  
status:: strong-match

source-id:: online-deep-transformation  
source-type:: membership-profile  
subject:: [[Yves Langeraert]]  
status:: supplied-pending-review

### Research

source-id:: research-covid-primary-care  
source-type:: publication  
context:: [[Vioras]]  
context:: [[Doclr]]  
domain:: [[Primary care]]  
status:: identified

### Organizational contexts

source-id:: context-doclr-vioras  
source-type:: organization-and-technology  
entities:: [[Doclr]], [[Vioras]], [[KU Leuven]], [[Primary care]]

source-id:: context-fountain-of-love  
source-type:: organization-and-project-ecosystem  
entity:: [[Fountain of Love]]

### Processing vocabulary

source-role:: identity-anchor  
source-role:: supporting-evidence  
source-role:: contextual-evidence  
source-role:: discovery-only  
source-role:: pending-review

---

## Processing state

processed:: true  
validated-by-subject:: false  
source-entries-created:: false  
evidence-objects-created:: false  
claims-extracted:: false  
relationships-extracted:: partial  
next-step:: select-one-research-or-github-source-for-deep-ingestion

### Suggested next operation

Select one high-value source and transform it from:

```
source
```

into:

```
source
→ observations
→ evidence objects
→ claims
→ entities
→ relationships
→ candidate capabilities
```

The present file should then remain as the **discovery result and navigation interface**, rather than becoming the place where every extracted fact is accumulated.

## Why I think this is a better fit

There are a few important differences from your original document.

### 1. The top is genuinely for humans

The first few hundred words answer:

> **What is this, what did we discover, and why should I care?**

There isn't a wall of fields before the reader gets any meaning.

That is exactly the role your Gemstone `Overview` is designed to play: narrative first, followed by selective links that offer routes into deeper material. GitHub 

### 2. The links become the ontology

Notice how things such as:

```
[[Yves Langeraert]]
[[Doclr]]
[[Vioras]]
[[KU Leuven]]
[[Fountain of Love]]
[[Primary care]]
[[Data architecture]]
```

are not just formatting.

They are **interfaces to concepts**.

This follows one of the strongest ideas in your Gemstone system: don't absorb every connected domain into the current document. Let links carry the expansion. The dictionary can act as an interface to deeper concepts rather than becoming the entire knowledge domain itself. GitHub 

For this project, I'd take that idea even further.

`[[Data architecture]]` should eventually become its own knowledge interface.

`[[Evidence]]` should become another.

`[[Identity]]`, `[[Claim]]`, `[[Observation]]`, `[[Source]]`, `[[Capability]]`, etc. can become a **small upper ontology** shared across your vault.

---

# 3. There are actually four kinds of information here

This is something I would make explicit in your system.

### Observation

> The paper acknowledges Yves Langeraert (Vioras, Doclr).

### Relationship

> [[Yves Langeraert]] → associated-with → [[Vioras]]

### Interpretation

> This may provide evidence relevant to healthcare data architecture.

### Knowledge claim

> Yves designed the data architecture for the system.

The last one is much stronger than the first three.

Your current document sometimes moves between these levels fairly quickly. The revised design makes the transitions visible.

That is particularly important when **LLMs are involved**, because an LLM will otherwise happily turn:

> "This material may be relevant to X"

into:

> "X is a characteristic of this person."

The structure becomes a guardrail against semantic inflation.

---

# 4. I'd introduce a distinction between `source`, `observation`, `claim`, and `inference`

I think this could become one of the most valuable additions to your whole system.

Something like:

```
[[Source]]
    │
    ├── contains → [[Observation]]
    │
    └── supports → [[Claim]]

[[Claim]]
    ├── supported-by → [[Evidence]]
    ├── about → [[Entity]]
    └── confidence → ...

[[Inference]]
    ├── derived-from → [[Claim]]
    └── requires-validation → true
```

Then an LLM doesn't need to guess what kind of sentence it is reading.

You can literally tell it:

> Extract only `Observation` objects from this section.

or:

> Find claims supported by at least two independent sources.

or:

> Find inferences that have not yet been validated.

That is a **huge difference** from asking an LLM to "understand the note."

---

# 5. The document can become an LLM interface

This is probably the most interesting capability you haven't fully exploited yet.

Your Gemstone repository already describes the files as having a dual human/technology purpose and deliberately balances human orientation, structured comparison and graph knowledge. GitHub 

For LLMs, I'd add **semantic affordances**.

For example:

```
## Processing state

processed:: true
validated-by-subject:: false
evidence-objects-created:: false
claims-extracted:: false
```

This isn't merely metadata.

It tells an agent:

> **What work remains to be done.**

And:

```
next-step:: select-one-research-or-github-source-for-deep-ingestion
```

is essentially an **executable instruction embedded in the knowledge graph**.

That suggests a larger pattern:

```
KNOWLEDGE OBJECT

    ┌────────────────────────────┐
    │ Human orientation          │
    ├────────────────────────────┤
    │ Navigation                 │
    ├────────────────────────────┤
    │ Semantic content           │
    ├────────────────────────────┤
    │ Evidence                   │
    ├────────────────────────────┤
    │ Machine-readable structure │
    ├────────────────────────────┤
    │ Processing state           │
    └────────────────────────────┘
```

An LLM can enter at whichever layer it needs.

---

# 6. I'd add "interfaces" rather than just links

This is where I think your Gemstone idea can evolve.

A link:

```
[[Data architecture]]
```

says:

> There is another thing over there.

An **interface** says:

> Here is what that thing means _for this context_, and here is how to continue.

For example:

```
### Data architecture

concept:: [[Data architecture]]
relevance:: candidate-capability
evidence-status:: unresolved

This result contains evidence concerning systems that collect,
structure, report, and visualise healthcare data.

For the general concept, see [[Data architecture]].
For the evidence concerning this person, see [[Evidence]].
```

Now the same concept can be approached from three directions:

```
Person
  ↓
Evidence
  ↓
Concept
```

or:

```
Concept
  ↓
Evidence
  ↓
People / projects / systems
```

That is much more powerful than simply having a backlink.

---

# 7. I'd preserve "empty space" deliberately

Another principle from the Gemstone experiment is especially valuable here: **absence should remain visible rather than being silently filled in**. The Gemstone README explicitly identifies "empty fields vs false completeness" as one of the tensions being explored. GitHub 

For your people/evidence system, I'd formalize this.

There is a major difference between:

```
capability:: machine learning
```

and:

```
candidate-capability:: machine learning
evidence-status:: unvalidated
```

and:

```
capability:: machine learning
evidence-status:: validated
```

That gives you an epistemic progression.

I think this could eventually become something like:

```
discovered
→ observed
→ associated
→ evidenced
→ corroborated
→ validated
→ synthesized
```

Not every piece of knowledge needs to travel all the way through that pipeline.

---

## The bigger architecture I see emerging

Your Gemstone experiment may actually be pointing toward a **general knowledge-file protocol**, rather than merely a gemstone format.

The domain changes:

```
Gemstone
Person
Organization
Project
Research paper
Source
Concept
Capability
Event
```

but the interface principles remain:

```
┌─────────────────────────────────────┐
│ FILE IDENTITY                       │
│ What is this object?                │
├─────────────────────────────────────┤
│ HUMAN ORIENTATION                   │
│ What does it mean?                  │
├─────────────────────────────────────┤
│ NAVIGATION                          │
│ Where can I go next?                │
├─────────────────────────────────────┤
│ DOMAIN KNOWLEDGE                    │
│ What is actually known?             │
├─────────────────────────────────────┤
│ EVIDENCE                            │
│ Why do we know it?                  │
├─────────────────────────────────────┤
│ GRAPH                               │
│ What is it connected to?            │
├─────────────────────────────────────┤
│ BOUNDARIES                          │
│ What must not be inferred?          │
├─────────────────────────────────────┤
│ PROCESSING INTERFACE                │
│ What can an agent do next?          │
└─────────────────────────────────────┘
```

And that gives you a particularly nice resolution to the **human-readable vs machine-readable tension**.

You don't actually have to choose.

You make the document **progressively machine-readable**.

The human reader gets meaning immediately.

The knowledgeable reader gets increasingly precise structure.

The expert gets the evidence and provenance.

The machine gets predictable fields, links, states, and relationships.

And an LLM gets something even more valuable: **explicit boundaries about what it is allowed to conclude**.

That last part is the capability I would prioritize most as you evolve this system.

---

Yes — I think that's an important correction.

The **subject of the document should dominate the document**, not the document's own mechanics. The machine-readable/interface concerns should be _woven into_ the document rather than becoming the reader's first experience.

The right principle is probably:

> **First answer the reader's implicit question: “What is this about?” Only then progressively expose how the knowledge is structured.**

So I'd change the architecture to something like:

```
Yves's online presence
│
├── 1. Essence / overview
│      What does Yves' public presence look like?
│
├── 2. Public presence
│      Where does he appear?
│
├── 3. Themes and contexts
│      What kinds of things surround that presence?
│
├── 4. Evidence
│      What specifically supports those observations?
│
├── 5. Identity boundaries
│      What belongs / doesn't belong?
│
├── 6. Deeper source material
│      Publications, profiles, repositories, etc.
│
├── 7. Candidate knowledge
│      What might this contribute to the broader knowledge model?
│
└── 8. Processing / machine interface
       What still needs to happen?
```

And **the file metadata stays at the very top physically**, because Obsidian requires that — but it should be tiny enough to be visually negligible:

```
---
type: online-presence-result
subject: [[Yves Langeraert]]
captured: 2026-09-29
status: discovery-result
---
```

Then immediately:

Online presence — revised subject-first structure

# Online presence

[[Yves Langeraert]] has a public presence spanning professional technology work, healthcare data, research, software, artificial intelligence, and organizational projects.

The available material connects him particularly strongly with [[Leuven]], [[KU Leuven]], [[Doclr]], and [[Vioras]], while more recent public material connects him with [[Fountain of Love]] and a broader ecosystem concerned with technology, language, AI, governance, and human collaboration.

His online presence is not concentrated in a single profile. It is distributed across professional and research profiles, publications, organizational material, public writing, and software projects. Taken together, these sources form a recognizable public identity, while also leaving important questions about individual contributions and capabilities that require deeper investigation.

This document therefore maps **Yves' observable online presence**. It distinguishes what is directly visible from what the material may eventually allow us to understand.

## At a glance

presence:: professional  
presence:: research  
presence:: healthcare-technology  
presence:: software  
presence:: artificial-intelligence  
presence:: organizational  
presence:: public-writing

The strongest visible contexts are:

- professional activity around [[Doclr]] and [[Vioras]];
    
- research and healthcare-data work connected with [[KU Leuven]];
    
- public interest and activity around software, data, AI, and architecture;
    
- organizational and project activity around [[Fountain of Love]];
    
- public technical writing and open-source material.
    

The public presence also contains an important identity boundary: search material for a golf professional with the same name should not be merged into this identity.

## Professional and research presence

### LinkedIn

[[LinkedIn]] presents a professional identity associated with [[Yves Langeraert]].

source-type:: professional-profile  
identity-status:: supplied-primary  
subject:: [[Yves Langeraert]]

The profile is particularly useful as an expression of current public positioning: professional associations, projects, interests, writing, education, and visible activity.

Observed associations include [[Fountain of Love]], [[Leuven]], [[KU Leuven]], AI-related writing, and technical and data-related education or certifications.

### ResearchGate

[[ResearchGate]] provides a separate research-oriented presence.

source-type:: research-profile  
identity-status:: strong-match  
subject:: [[Yves Langeraert]]  
institution:: [[KU Leuven]]  
department:: [[Computer Science]]

The profile associates Yves with terminology including machine learning, pattern recognition, feature extraction, data clustering, machine intelligence, applied artificial intelligence, prediction, classification, and supervised learning.

These terms describe the vocabulary and expertise associated with the public research profile. They should not automatically be interpreted as independently validated capability claims.

## Healthcare, data and technology

One of the clearest public contexts around Yves is the intersection of healthcare, data, and technology.

### Doclr and Vioras

[[Doclr]] and [[Vioras]] form an important part of the public technology footprint.

relationship:: professional-context  
relationship:: research-context  
domain:: healthcare-technology  
domain:: healthcare-data

A 2021 publication, _Burden of COVID-19 on Primary Care: a Prospective Nationwide Observational Study_, describes a nationwide monitoring effort involving Belgian primary care.

The research system used structured electronic forms integrated into general-practice electronic medical records, together with reporting and visualisation for GP circles, primary-care zones, and policy makers.

The publication refers to [[Vioras]] in connection with questions for the monitoring instrument and with reports and visualisations used to identify support needs. Its acknowledgements name Yves Langeraert in connection with [[Vioras]] and [[Doclr]].

This places Yves' public presence in a concrete technological context involving:

- healthcare data;
    
- electronic medical records;
    
- data collection;
    
- monitoring;
    
- reporting;
    
- visualisation;
    
- decision support.
    

The source establishes the context and association. It does not, by itself, establish the precise contribution of Yves to each component.

## Research and technical vocabulary

A second layer of Yves' public presence emerges from the vocabulary surrounding his research and technical activity.

subject:: [[Yves Langeraert]]  
domain:: [[Machine learning]]  
domain:: [[Artificial intelligence]]  
domain:: [[Data]]  
domain:: [[Software architecture]]  
domain:: [[Healthcare technology]]

Public material contains recurring references to machine learning, AI, data, software architecture, and healthcare technology.

Some of these are directly evidenced by profiles or publications; others are candidate areas for deeper investigation.

The distinction matters:

```
public vocabulary
    ↓
source evidence
    ↓
validated knowledge
```

The presence of a technical term in a profile is evidence that the term occurs in that public context. It is not necessarily evidence that the person currently practices every technique represented by the vocabulary.

## Organizational presence

### Fountain of Love

[[Fountain of Love]] represents a different part of Yves' public presence.

relationship:: organizational-context  
relationship:: project-context  
domain:: technology-and-society

Public organizational material uses concepts including sovereignty, trustworthiness, emotional clarity, responsible AI fluency, living language, governance, and co-creation.

These concepts are relevant to understanding the ecosystem in which Yves appears publicly.

They should nevertheless remain **organizational concepts unless separately connected to Yves as an individual**.

This distinction prevents organizational language from silently becoming biographical claims.

### Open-source ecosystem

The [[Fountain of Love]] GitHub presence exposes a wider project ecosystem, including:

- `operating-model`
    
- `mml-machine-modelled-language`
    
- `spiral-algo-to-polar-algebra-evolution`
    
- `living-mathematics-library`
    
- `py-wordless-meaning`
    
- `fibonacci-blueprint`
    
- `gemstones`
    
- `py-crystal-seed`
    

These projects are potentially valuable routes into the technical and conceptual dimensions of the public presence.

repository-association:: observed  
authorship:: not-yet-established  
conceptual-ownership:: not-yet-established

The repository ecosystem should therefore be treated as a **source of evidence to investigate**, rather than as a list of established personal achievements.

## Public writing

Another part of the online presence appears through public technical writing.

A Medium comment attributed to Yves concerns dependency injection and repository architecture in an Angular application.

source-type:: technical-writing  
domain:: software-architecture  
topic:: dependency-injection  
topic:: repository-architecture  
technology:: Angular

This provides a more concrete example of technical vocabulary appearing in public expression.

It is potentially more informative than a generic profile keyword because it exposes Yves engaging with a specific technical problem.

## Identity boundaries

identity-confidence:: high

The available sources form a coherent identity cluster around:

- [[Yves Langeraert]]
    
- [[Leuven]]
    
- [[KU Leuven]]
    
- [[Doclr]]
    
- [[Vioras]]
    
- [[Fountain of Love]]
    

A separate golf professional with the same name appears in search results.

identity-boundary:: same-name-golf-professional  
identity-boundary:: search-result-snippet  
identity-boundary:: organizational-expression  
identity-boundary:: contribution-inference

The following distinctions should remain active throughout further processing:

- Search snippets are discovery material, not canonical evidence.
    
- Organizational statements are not automatically personal statements.
    
- Acknowledgement is not equivalent to authorship.
    
- Association with a project is not necessarily authorship or ownership.
    
- Public availability does not imply permission to reproduce sensitive details.
    
- Lack of a visible result does not establish absence.
    

## What this presence may tell us

The current material suggests several promising directions for deeper investigation.

candidate-domain:: [[Data architecture]]  
candidate-domain:: [[Healthcare technology]]  
candidate-domain:: [[Artificial intelligence]]  
candidate-domain:: [[Machine learning]]  
candidate-domain:: [[Software architecture]]  
candidate-domain:: [[Research]]  
candidate-domain:: [[Technology and society]]

The most interesting question is not simply:

> "What skills does Yves have?"

but:

> **"What recurring patterns of work, thinking, and system-building become visible when the individual sources are examined together?"**

The current discovery result is not sufficient to answer that question.

It does, however, identify the source material from which such an answer might eventually be constructed.

## Evidence map

The presence described above is grounded in several different types of evidence.

### Primary identity sources

source-type:: professional-profile  
source-type:: research-profile  
source-type:: membership-profile

### Research sources

source-type:: publication  
source-type:: research-context  
source-type:: acknowledgement

### Organizational sources

source-type:: organization  
source-type:: product  
source-type:: project  
source-type:: repository

### Public expression

source-type:: article  
source-type:: technical-writing  
source-type:: software

Each source should eventually become its own evidence object where the distinction between source, observation, claim, and inference can be preserved.

## Deeper investigation

The next useful step is not to expand this document indefinitely.

Instead, select one high-value source and descend into it.

For example:

[[Burden of COVID-19 on Primary Care]]  
→ source  
→ observations  
→ named entities  
→ relationships  
→ individual contribution  
→ technical systems  
→ evidence  
→ claims

Or:

[[gemstones]]  
→ repositories  
→ concepts  
→ specifications  
→ design principles  
→ relation to Yves' public work

The current document remains the **map of the online presence**. The deeper documents provide the evidence from which the map can evolve.

## Processing state

processed:: true  
validated-by-subject:: false  
source-entries-created:: false  
evidence-objects-created:: false  
claims-extracted:: false  
relationships-extracted:: partial

next-step:: select-one-source-for-deep-ingestion

## Source interface

The document itself is both human-readable and machine-readable.

At the beginning, prose provides orientation.

As the document progresses, inline fields make entities, relationships, evidence types, and epistemic status increasingly explicit.

The deepest sections are intended primarily for processing and navigation rather than first-pass reading.

This structure is deliberate: **the reader should encounter Yves first, the evidence second, and the mechanics of the knowledge system last.**

I think this version gets much closer to the principle you're describing.

### One subtle change I'd make to the Gemstone philosophy

I would **not** necessarily make "more machine-readable" synonymous with "lower in the document."

That's useful as a _human-reading heuristic_, but it's not a fundamental property of the knowledge.

A machine doesn't care whether this appears on line 20 or line 200. And, as you point out, an LLM can read the entire document.

So I'd instead define the progression as:

> **broad → specific → evidential → operational**

rather than strictly:

> prose → structured data.

That distinction matters because a deeply nested section can still contain excellent prose, and a top-level sentence cancontain a highly meaningful machine-readable link.

The real progression is **increasing semantic precision**.

And I think that gives your Gemstones idea a very strong general principle:

> **The document should become more precise as the reader moves deeper, not merely more structured.**

That allows you to preserve the thing I think is particularly good about your experiment: **a human can stop anywhere and still get a meaningful understanding**, while an expert or an LLM can keep descending until it reaches the level of precision it needs.