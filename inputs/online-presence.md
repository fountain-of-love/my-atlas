---
type: online-presence-source-register
subject: "[[Yves Langeraert]]"
status: source-inventory
stage: extract-ready
captured: 2026-09-29
harvest: "[[inputs/online-presence-harvest]]"
transform: "[[inputs/online-presence-transform]]"
next-step: inspect-or-refresh-registered-sources
---

# Online presence

This file is the source register for the public online presence of
[[Yves Langeraert]]. It lists online sources and their retrieval status. It does
not contain extracted observations, interpretations, or model entries.

The register is deliberately narrower than the processing pipeline:

```text
online sources
    ↓
harvest: source-bound observations
    ↓
transform: lens-specific interpretation
    ↓
load: validated material into source/
```

## Source register

| Source ID | Type | Source | Identity / relation status | Retrieval status |
|---|---|---|---|---|
| `online-linkedin` | professional profile | [LinkedIn profile](https://www.linkedin.com/in/yveslangeraert/) | supplied primary | indexed snapshot; direct profile unavailable |
| `online-researchgate` | research profile | [ResearchGate profile](https://www.researchgate.net/profile/Yves-Langeraert) | strong match | profile available |
| `online-deep-transformation` | membership profile | [Deep Transformation Network](https://deeptransformation.network/members/35523872) | supplied; pending review | page not substantially readable |
| `research-burden-covid-primary-care` | publication | [Burden of COVID-19 on Primary Care](https://www.researchgate.net/publication/352472298_Burden_of_COVID-19_on_Primary_Care_a_Prospective_Nationwide_Observational_Study) | subject named in source context | publication available |
| `covid-barometer` | technical document | [COVID-19 barometer PDF](https://www.frankrobben.be/wp-content/uploads/2020/03/Dagelijkse-barometer-COVID-19-huisartsen-triageposten-rusthuizen.pdf) | subject named in source context | PDF available |
| `belgian-parliament-doclr` | public record | [Belgian parliament record](https://www.dekamer.be/doc/CCRI/html/55/ic523x.html) | subject named in source context | page available |
| `doclr-primary-care-article` | article | [Doclr primary-care article](https://gbiomed.kuleuven.be/english/research/50000715/spotlightfolder/medischeinnovatie-demorgen-2018.pdf) | subject named in source context | PDF available |
| `doclr-website` | product website | [Doclr](https://www.doclr.be/) | organizational source | website available |
| `paronella-smals-record` | public record | [Belgian parliamentary record](https://www.dekamer.be/doc/CCRI/html/55/ic409x.html) | organizational source | page available |
| `docleas-partnership` | partnership page | [Docleas](https://docleas.eu/over-ons/) | organizational source | page available |
| `partheas-contract` | company announcement | [Partheas contract announcement](https://partheas.com/2024/09/23/partheas-receives-contract-for-appointments-customer-support-and-digital-reception-for-local-authorities-in-flanders/) | organizational source | page available |
| `impute-company-record` | company record | [Impute consulting](https://www.companyweb.be/nl/0716966095/impute-consulting) | organizational source | record available |
| `helleborus-company-record` | company record | [Helleborus](https://amlcompany.com/fr-be/entreprises/0785584588-helleborus) | organizational source | record available |
| `vioras-company-record` | company record | [Fun to work with / Vioras](https://www.pappers.be/nl/company/fun-to-work-with-0736.535.549) | historical context | record available |
| `fountain-of-love-linkedin` | organization profile | [Fountain of Love](https://be.linkedin.com/company/fountain-of-love) | organizational source | profile available |
| `fountain-of-love-github` | repository profile | [Fountain of Love GitHub](https://github.com/fountain-of-love) | repository association observed; authorship open | profile available |
| `medium-di-comment` | technical writing | [Medium comment](https://medium.com/%40tankske/im-particulary-interested-in-how-you-ve-established-the-di-for-the-repository-cddc55405932) | attributed to subject | comment available |

## LinkedIn source locations

The LinkedIn profile is one input source with several meaningful locations.
These locations are not education evidence themselves; they identify where a
claim was communicated and allow extracted evidence to retain its lineage.

| Location ID | Profile location | Used for |
|---|---|---|
| `online-linkedin-education` | Education section | Formal education claims, including KU Leuven |
| `online-linkedin-certifications` | Licenses & Certifications section | Certificates listed through Coursera, UGent IVPV, and The Open Group |
| `online-linkedin-courses` | Courses section | Additional course and training claims |

## Register rules

- Add one row for each distinct online source, even when several sources refer
  to the same organization or project.
- Keep source identity, URL, access date, and retrieval limitation here.
- Do not copy source content into this register.
- Do not record subject-supplied context here; that remains in
  [`harvest.md`](harvest.md).
- Link extracted observations through the harvest artifact, not by expanding
  this file into a narrative.

## Processing state

The source inventory is ready to be read by the harvest stage. The current
observations are recorded in [online-presence harvest](online-presence-harvest.md).
Lens-specific interpretation is staged in [online-presence transform](online-presence-transform.md).
