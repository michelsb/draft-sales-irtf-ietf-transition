---
title: "A Method for Tracing IRTF Research Contributions to IETF Work"
abbrev: "IRTF-to-IETF Research Method"
category: info
workgroup: RASPRG

docname: draft-sales-irtf-ietf-transition-latest
submissiontype: IRTF
date:
v: 3
ipr: trust200902
stand_alone: true
pi: [toc, sortrefs, symrefs]
keyword:
 - IRTF
 - IETF
 - research contribution
 - research transfer
 - documentary analysis
 - reproducibility
venue:
  github: "michelsb/draft-sales-irtf-ietf-transition"
  latest: "https://michelsb.github.io/draft-sales-irtf-ietf-transition/draft-sales-irtf-ietf-transition.html"

author:
 -
    ins: "M. Sales"
    fullname: "Michel Sales"
    organization: "Federal University of Ceará (UFC), Quixada Campus"
    street: "Av. José de Freitas Queiroz, 5003, Cedro"
    city: "Quixadá"
    region: "Ceará"
    code: "63902-580"
    country: "Brazil"
    email: "michelsb@ufc.br"
 -
    ins: "M. Santos"
    fullname: "Marcelo Santos"
    organization: "Federal Institute of Education, Science and Technology of the Sertão Pernambucano (IFSertãoPE), Salgueiro Campus"
    street: "BR 232, Km 504, sentido Recife, Zona Rural"
    city: "Salgueiro"
    region: "Pernambuco"
    code: "56000-000"
    country: "Brazil"
    email: "marcelo.santos@ifsertao-pe.edu.br"

normative: {}

informative:
  RFC2014:
  RFC3967:
  RFC5743:
  RFC7841:
  DATATRACKER-API:
    title: "Datatracker API Notes"
    target: "https://datatracker.ietf.org/api/"
    author:
      org: "IETF"
    date: false
  RELATIONSHIP-CATALOG:
    title: "Datatracker Document Relationship Names"
    target: "https://datatracker.ietf.org/api/v1/name/docrelationshipname/"
    author:
      org: "IETF"
    date: false
  RFC-INDEX:
    title: "RFC Index in XML Format"
    target: "https://www.rfc-editor.org/rfc-index.xml"
    author:
      org: "RFC Editor"
    date: false

...

--- abstract

This document describes a reproducible method for investigating whether
and how Internet Research Task Force (IRTF) research contributes to
Internet Engineering Task Force (IETF) work. The method combines a
versioned study plan, preservation of source material, typed discovery
of documentary, organizational, and human mediation hypotheses, and
independent human review of located evidence. It distinguishes discovery
signals from confirmed contributions and defines separate
classifications for transfer mechanisms, transferred objects, and
evidence observations. It also describes coverage audits, reporting
requirements, and limits on interpreting citations, document continuity,
group relationships, shared authorship, and event dates. Discovery
identifies hypotheses for inspection; conclusions about research use
require the applicable evidence and independent review.

--- middle

# Introduction {#intro}

The IRTF organizes research on Internet-related topics, while the IETF
develops engineering specifications and standards. Their different roles
are described in {{RFC2014}}. Research can contribute to IETF work
through document continuity, use of a technical solution, adoption of a
concept or experimental result, organizational processes, or mediation
by participants. These mechanisms need not coincide with publication of
a document or creation of a working group.

The research question addressed by this method is:

> Which identifiable IRTF research outputs or agendas contributed to
> IETF work, through which documented mechanisms, and with what
> observed reach?

Answering this question requires more than counting references or
matching draft names. An RFC number identifies a publication, not an
IETF contribution. The IRTF has its own document stream {{RFC5743}}, and
publication streams and standards status are distinct {{RFC7841}}.
Similarly, working-group adoption without a verified IRTF origin does
not establish a research contribution.

This document provides an operational method for constructing and
reviewing contribution hypotheses. Its main design principle is to
preserve a trace from each conclusion to the source version, passage,
chronology, and review decision supporting it. Automated discovery
identifies material for inspection; human review establishes whether the
mechanism-specific conditions are met.

## Scope and Status {#scope}

This is an individual methodological proposal. It does not claim
research-group adoption, IRTF consensus, or IRSG approval. The intended
submission stream in the source metadata does not establish any of those
conditions. The proposed classifications and procedures require
empirical evaluation of their reliability and coverage as described in
{{validation}}.

The method covers documentary, organizational, and human mediation
inquiries using recoverable historical sources. Each study declares its
source coverage, acquisition procedures, and search limitations.
Documentary records and complementary process evidence can both be
needed to confirm a case.

This document specifies the research procedure and its interpretive
limits independently of any particular software or collection system. It
reports no completed corpus, confirmed transfers, coverage estimate, or
measured reviewer agreement. Each empirical application needs its own
registered study plan and results.

## Method Overview {#method-overview}

Follow the investigation in the sequence below. Each stage produces a
record used by the next stage. Record unresolved checks rather than
assuming that completion of a stage confirms a contribution.

| Stage | Input | Actions | Output |
| --- | --- | --- | --- |
| Plan | Research question and eligible universe | Declare scope, sources, criteria, reviewers, sampling, and event unit | Registered study plan and coding manual |
| Collect and preserve | Declared source scope | Retrieve records, retain versions and provenance, document gaps | Preserved source collection |
| Normalize and discover | Preserved collection and declared screening rules | Reconcile identities, classify relationships, propose hypotheses | Candidates with signals, paths, and source references |
| Inspect and classify | Candidate and supporting sources | Check eligibility and context, identify the contribution, assess alternatives | Evidence record and proposed mechanism and object labels |
| Review and adjudicate | Inspected evidence and criteria | Record independent judgments, compare decisions, resolve disagreements | Consolidated decision or explicit pending status |
| Consolidate events | Reviewed hypotheses and grouping criteria | Establish which records concern the same contribution episode | Reviewed event mappings and unresolved groupings |
| Audit and report | Sources, candidate decisions, and event mappings | Assess coverage and agreement, distinguish counts and estimates | Findings, uncertainty, and reproducibility package |

~~~ ascii-art
                 Registered study plan
                          |
                          v
              Collect and preserve sources
                          |
                          v
          Normalize identities and relationships
                          |
        +-----------------+-----------------+
        v                 v                 v
  Documentary      Organizational     Human mediation
   hypotheses        hypotheses         hypotheses
        |                 |                 |
        +-----------------+-----------------+
                          v
             Inspect evidence and classify
                          |
                          v
         Independent review and adjudication
                          |
                          v
              Consolidate contribution events
                          |
                          v
              Audit and report findings
~~~
{: #fig-method-overview title="Stages and records of the research procedure"}

Design the audit before selecting its sample. Source-coverage checks and
complementary searches can proceed during the investigation;
{{validation}} specifies how they reach beyond the candidate queue.
A new source or corrected judgment can require revisiting an earlier
stage. Retain both the preceding record and the reason for revision.
Human mediation leads may start without a base, while T6 confirmation
depends on an independently confirmed T1--T5 event.

## Four Analytical Layers {#analytical-layers}

Keep the following concepts separate throughout the record:

| Layer | Question answered | Example |
| --- | --- | --- |
| Typed relationship | What connection was observed? | An IETF draft cites an earlier document |
| Discovery signal | Why inspect this hypothesis? | CIT flags an eligible cited-to-citing pair |
| Mechanism | How did the contribution occur? | T2 requires evidence of identifiable technical use |
| Object | What was continued or used? | O7 identifies an algorithm |

A source passage supplies evidence for a claim; the classification
records the reviewer's interpretation under the confirmation criteria.
The worked example in {{worked-example}} connects these layers to review
and event consolidation.

# Terminology and Units of Analysis {#terms}

The words "requires" and "confirmation condition" below describe the
research procedure. This document does not define a network protocol or
use BCP 14 requirement keywords.

Research contribution:
: An identifiable IRTF research output or agenda carried into IETF
  activity through a mechanism supported under {{mechanisms}}.
  Documentary continuity (T1), substantive use (T2--T4), and an
  organizational process (T5) are distinct findings. T6 describes
  mediation of an established contribution. The transfer labels below
  refer to these operational classifications.

Typed relationship:
: A source-supported connection with identified endpoints, direction,
  and type, such as a citation or documentary succession. Record
  whether it is explicit in the source or derived by a stated rule.

IRTF research group (RG):
: A research group whose eligibility and historical identity are
  established in the study inventory.

IETF working group (WG):
: A working group relevant to an observed IETF destination or process.
  A current affiliation is not automatically a historical affiliation.

Origin and destination:
: The research-side and IETF-side endpoints of a proposed contribution.
  An endpoint can be a document or a group, depending on the inquiry.

Candidate:
: A hypothesis selected for review. Documentary candidates concern
  document pairs, organizational candidates concern RG/WG processes,
  and human mediation candidates concern an observed person/address
  hint and its possible connection to a contribution.

Discovery signal:
: A recorded reason for proposing a candidate. Several signals and
  paths can support the same candidate. Signals are not findings.

Evidence observation:
: A located observation in an identified source version, with
  provenance, integrity information, date information, and a stated
  relationship to the hypothesis.

Review:
: A person's justified decision about a candidate and its evidence.
  Corrections retain the preceding decision in the review history.

Consolidated decision:
: Agreement between independent review roles, or an adjudicated
  decision under the study plan. This is distinct from consolidating
  several document pairs into one scientific event.

Confirmed contribution event:
: A contribution meeting the applicable confirmation conditions after
  review. A single event can carry multiple mechanism and object
  labels. Related candidates need an explicit event-consolidation
  decision before they can be counted as one event.

Event consolidation:
: A reviewed grouping of hypotheses concerning the same contribution,
  destination activity, and episode under the declared event unit.
  Its mapping and rationale are separate from reviewer agreement.

Study execution:
: An investigation associated with a frozen study-plan version,
  historical cutoff, inventory, and reviewer assignments. Sources and
  derived snapshots can accumulate within that fixed scope.

Discovery records, reviewed decisions, and consolidated events are
distinct units. Use their names and denominators explicitly in reports.

# Study Design and Eligibility {#design}

Start from the research question and the proposed origin and destination
universe. Establish the choices below before collecting evidence. The
output is a versioned plan that another team can follow and audit.

## Versioned Study Plan {#plan}

Before collection, register the following study choices:

1. The research question, inclusion and exclusion criteria, and
   intended interpretation of a contribution.
2. The historical observation window, including an explicit upper
   cutoff in UTC and the precision of available event dates.
3. A verified inventory of active and concluded RGs, with acronyms,
   persistent source identifiers where available, historical identity
   evidence, and a documented inventory audit.
4. The publication plan for results, evidence, and limitations.
5. The eligible reviewer and adjudicator pools, the policy for assigning
   an independent pair to each candidate, and conflict-of-interest
   exclusions, or explicit limitations where those roles cannot be
   assigned.
6. Procedures for coverage auditing, independent review, disagreement
   resolution, and assessment of agreement before adjudication.
7. The selection design if only part of the eligible universe will
   receive inspection or independent review, and which findings that
   design can support.
8. The contribution-event unit, grouping rules, and intended measures,
   including the numerator and denominator for any rate.
9. The discovery routes, source-specific screening conventions, and
   procedures for recording exclusions and rule changes.

Freeze these choices before beginning the investigation. Specify whether
the documentary scope includes all recoverable history, drafts and RFCs
in all states, and all recoverable IETF destinations, or a justified
subset. The cutoff is an upper bound, not the beginning of the search
period; record any lower bound separately.

Dividing acquisition or screening into operational batches does not
constitute scientific sampling. If the question, eligibility scope, or
scientific confirmation criteria change, register a new plan version and
a separately identified study execution. Applying an updated discovery
rule to preserved sources can enlarge a queue within the existing scope,
provided the rule version, input snapshot, and earlier decisions remain
auditable. Identify the version of this method and register any
deviations or extensions.

## Endpoint Eligibility {#eligibility}

Establish an origin's IRTF affiliation from preserved group, document,
or historical records, checked against the frozen inventory. A name
prefix alone is insufficient. Establish the destination's IETF
affiliation independently; publication as an RFC is insufficient. For
confirmation, also identify the research output or agenda and its
connection to the RG at the relevant time. Document affiliation alone
does not establish that every idea in the document originated there.

Retain ambiguous, unknown, and multiple affiliations explicitly. An
unambiguous current label does not resolve a conflicting history. Where
a single documentary identity appears in both institutional phases,
review the ordered phase observations rather than treating the two
labels as two independent documents.

Known post-cutoff endpoints and intermediates are excluded from eligible
historical paths. Undated material remains temporally pending where its
eligibility cannot be established. Collection time does not substitute
for an event date.

# Sources, Preservation, and Chronology {#sources}

Use the registered scope to acquire the material needed for discovery
and review. The output is a preserved collection with identifiable
versions, provenance, and an acquisition-gap record.

## Source Coverage {#coverage}

Documentary sources include the Datatracker API
{{DATATRACKER-API}} and RFC Editor material, including the RFC index
{{RFC-INDEX}} and preserved document texts.

| Source material | Research purpose |
| --- | --- |
| Document metadata, events, and relationships | Identity, affiliation, continuity, and citation observations |
| RFC index and draft/RFC texts | Publication metadata, references, and passages for content review |
| Group metadata, history, and selected charters | RG/WG screening, institutional observations, and agenda clues |
| Posted draft submissions | Dated author-address observations |

Meeting minutes, BOF records, slides, mailing-list discussions, code,
and development records can provide complementary evidence, as can
participation histories and documented person aliases. Define which of
these sources will be searched and how. Report the sources and
historical periods actually examined, including gaps between planned and
completed searches.

Completing the pagination of a query establishes completion of that
query, not complete institutional history. Missing historical texts,
unavailable revisions, inconsistent pagination, and failed requests
remain visible acquisition gaps.

## Preservation and Provenance {#preservation}

Preserve original response and file bytes separately from normalized
records and derived candidates. Associate artifacts with source URLs,
request parameters where applicable, collection times, source versions,
and SHA-256 digests. Keep request logs and resumable checkpoints so that
an interrupted acquisition can be distinguished from an empty result.

Derived observations retain their source references, transformation or
rule identifiers, and analytical snapshot. Reanalysis preserves
candidate identifiers, investigator annotations, and review history. A
lead not proposed by a newer snapshot can remain as a historical
candidate; report that condition rather than silently deleting it.

A checksum verifies equality with the preserved bytes. It does not prove
that the source statement is true, historically complete, or independent
of another source. Copies of the same declaration do not constitute
independent corroboration.

## Distinct Dates {#dates}

Keep source-event time, publication time, observation time, and
collection time separate. Preserve the precision supplied by the source,
including year-only or month-only dates and unknown dates.

Charter revision observation, revision publication, and charter approval
are distinct observations. Bind a date to the exact source version it
supports. An approval recorded for another revision needs explicit
evidence connecting those revisions. Missing or ambiguous bindings
remain pending. {{source-dates}} gives a Datatracker-specific example of
a conservative binding convention.

Even a supported charter approval date does not establish when the
originating research became available or when its adoption occurred.
Those are separate chronological questions for review.

# Normalization and Typed Documentary Paths {#normalization}

Starting from preserved sources, establish document identities and
connections before proposing candidates. The output retains both the
observed connection and the screening interpretation.

Normalize document identifiers, explicit aliases, inverse relationship
forms, and definite historical renames while retaining the original
records. Keep documentary succession separate from technical evolution,
series membership, publication stream, and standards status.

Preserve both the factual relationship direction and the projected
direction of a possible research contribution. For example, a source
record can point from a citing document to a cited document, while the
contribution hypothesis is evaluated from cited work to citing work.

Use a preserved relationship vocabulary and record its mapping to the
families below. {{source-relationships}} describes the Datatracker and
RFC-index conventions. These families are methodological screening
categories; confirmation uses the separate T labels.

| Family | Inputs | Contribution projection |
| --- | --- | --- |
| CIT: citation | Normative, informative, or unspecified references; possible references retained separately | Cited to citing work |
| CONT: continuity | Definite replacement, draft-to-RFC succession, or historical rename; possible replacement retained separately | Earlier work to successor |
| EVOL: technical evolution | Update or obsolescence relationships | Updated or obsoleted work to later work |
| FASE: institutional phase | Explicit stream-change events or ordered affiliation observations of one identity or definite lineage | IRTF phase before IETF phase |

Normative and informative references serve different purposes
{{RFC3967}}. Preserve that distinction without treating either subtype
as automatic proof that a particular research object was used.

## Admissible Paths {#paths}

Let C denote a definite succession connection, B a cited-to-citing
connection, E an update/obsolescence connection from earlier to later
work, and M membership from an RFC to an STD or BCP series. The symbol
`*` permits zero or more connections; `+` requires at least one.

| Family | Admissible pattern |
| --- | --- |
| CONT | `C+` |
| CIT | `C* B C*`, containing exactly one citation |
| EVOL | `E+` |
| CIT through a series | `M B`, pending component and historical-membership review |
| FASE | A same-identity event or ordered observations; alternatively, `C+` with ordered endpoint affiliations |

Direct means one admissible connection. Chain means two or more
connections through intermediate items. A candidate with both direct and
chain signals belongs to the "direct and chain" group. These labels
describe structure, not confidence or confirmation.

{{fig-path-topology}} illustrates these groups using CIT paths. A is
an eligible IRTF origin, D is an eligible IETF destination, and X is an
intermediate document. B and C retain their definitions above. The
examples assume that the displayed paths are the recorded support for
each pair.

~~~ ascii-art
(a) Direct only
    A --------B--------> D

(b) Chain only
    A ---C---> X ---B---> D

(c) Direct and chain: one candidate, two paths
    A --------B--------> D
    A ---C---> X ---B---> D

(d) Excluded as a CIT path: two successive citations
    A ---B---> X ---B---> D
~~~
{: #fig-path-topology title="Illustrative CIT paths and candidate topology"}

Panel (c) has the same endpoints on both lines and is counted as one
candidate. Topology groups are mutually exclusive at candidate level;
individual discovery families and signals can overlap. Panel (d) does
not establish use of A by D and cannot serve as a CIT path.

Possible references and replacements create direct leads only; they do
not serve as transitive bridges. Two successive citations do not
establish use of the earliest work. Shared ancestors, undirected
connectivity, and shared series membership do not establish succession.
Declare whether the search enumerates admissible paths or records
representatives. For representative selection, document traversal
limits, tie-breaking, and which family and topology combinations are
retained. Make the selection reproducible from the preserved input.
Recorded paths describe the search output; they do not establish that
all historical routes have been found.

An RFC-to-series membership can resolve a series citation into a pending
component hypothesis. Present-day membership does not establish
historical composition or which component the citing document used.

Procedural approvals, conflict reviews, and standards-status processes
supply context. They cannot serve as generic technical bridges or
establish a stream transition or use on their own. Preserve those
observations separately from admissible contribution paths.

For FASE, affiliation-derived ordering uses the earliest known IETF
presence; an explicit event supports the local transition it records.
Neither general connectivity nor endpoint ordering dates every link.

# Candidate Discovery {#discovery}

Apply the declared discovery routes to the normalized source record. The
output is a set of hypotheses with stable identifiers, supporting
observations, rule versions, and unresolved checks. Record manual
hypotheses with their own rationale.

The three categories below identify different units of inspection. One
underlying case can generate related candidates in several categories.
The categories do not compete as alternative final labels. Manual
hypotheses can also be recorded, without inventing automated discovery
signals.

## Documentary Candidates {#documentary}

Documentary discovery proposes eligible origin/destination document
pairs using CIT, CONT, EVOL, and FASE. It retains the supporting paths,
relationship subtypes, factual and projected directions, source
locations, and unresolved chronology or affiliation checks.

Review determines whether an identifiable research object was used,
whether documentary continuity is established, or whether the
relationship is only contextual. A citation is a discovery observation,
not an automatic T2, T3, or T4 finding.

## Organizational Candidates {#organizational}

Organizational discovery investigates an RG/WG pair and a possible
process linking research to the creation or change of IETF activity. The
following are derived rules, not additional Datatracker document
relationship codes:

| Signal | Screening observation |
| --- | --- |
| ORG_DOCUMENT_LINKS | A documentary candidate connects an observed RG document and WG document |
| ORG_DOCUMENT_CONTINUITY | That documentary support also carries continuity evidence |
| ORG_CHARTER_REFERENCE | A verified preserved WG charter contains a located RG mention |
| ORG_TYPE_CHANGE | Verified consecutive dated observations show RG then WG for the same persistent group identifier |
| ORG_AGENDA_ADOPTION | A preserved charter contains explicit RG research attribution and a nearby WG work mandate |

Document-supported group signals have chain topology. Verified charter
mentions, same-identifier type changes, and agenda-adoption signals have
direct topology. These structures do not establish group succession or
research adoption.

The origin belongs to the frozen RG inventory. Supporting documentary
candidates and artifacts belong to the same study execution. Declare
whether charter searches cover all eligible groups independently or only
pairs selected by earlier screening. A search restricted to previously
selected pairs cannot establish coverage of all charters.
Different-identifier group succession and BOF or other process routes
require explicit search procedures if included in the study scope.

Agenda-adoption screening seeks an explicit attribution of research to
an RG and a WG mandate concerning that work. Relevant mandates can
include updating, integrating, adopting, standardizing, or adding work
to protocols. Preserve the attribution and mandate passages separately
and record the resulting signal on the RG/WG hypothesis. If lexical
patterns or a proximity threshold select passages, declare their
language coverage, parameters, and version before screening. Textual
distance is a selection criterion, not evidence of a semantic link.

Review checks that both passages concern the same research result, that
the origin predates the relevant mandate, and that process evidence
supports the claimed connection. Textual proximity, a group mention,
cooperation, or thematic similarity is insufficient. Adoption of work is
distinct from succession of organizations.

## Human Mediation Candidates {#human}

Human discovery proposes possible connections between participants and
an identifiable contribution. The two address-based routes below use
dated authorship observations. Declare the sources, matching rule, and
treatment of identities, date precision, and affiliations. An
exact-address screening profile is described in {{source-authorship}}.
An address match remains an identity hint. Preserve source-specific
author lists; RFC authorship requires its own evidence.

### Documentary-Base Shared Authorship

`HUM_SHARED_AUTHOR` compares authorship observations on the exact
endpoint document names of an existing documentary candidate. An address
observed on both sides creates a possible chain through that address
hint, linked to the documentary base. A single author list is not
duplicated into two institutional phases of the same document.

The base can still be pending when discovery occurs. Document whether
the search only checks authorship on the base endpoints or also applies
temporal screening. Report its scope separately from the independent
route; completing one search does not establish completion of the other.

### Independent Author Intersections

`HUM_AUTHOR_INTERSECTION` searches dated authorship observations without
requiring an existing documentary candidate. Establish an eligible
IRTF-side observation before an eligible IETF-side observation under the
declared temporal rule. Date precision and ambiguous affiliations can
prevent ordering. Keep those exclusions distinguishable from a completed
search with no match; {{source-authorship}} describes one conservative
profile for date-only submissions.

Pairs with an existing documentary candidate or a recorded direct
relationship in either direction are separated from this exploratory
queue. Remaining address matches create human mediation leads without a
linked base. The absence of a recorded direct relationship does not
exclude indirect paths or missing evidence. Indirect paths are not
exhaustively searched by this screening step.

One lead represents one address/document-pair observation, not one
verified person or event. Identity, historical group types, continuous
affiliations, actual contribution, and mediation remain unverified. This
route is a separate discovery action; completion of the documentary-base
route does not imply completion of this search.

### Linking and Confirming a Mediation Claim

A human lead can later be associated with a documentary or
organizational base in the same study execution, with a recorded
justification. That association does not confirm the contribution or the
person. T6 confirmation requires an independently consolidated T1--T5
base, verified participation, and a located passage documenting
mediation.

{{fig-mediation-confirmation}} shows the path to T6 confirmation. An
address match can generate a lead but cannot satisfy the identity or
role conditions by itself.

~~~ ascii-art
  Lead without a base             Lead with a base
           |                              |
           +---------------+--------------+
                           v
              Link / check the base event
                           |
                           v
    +---------------------------------------------+
    | All T6 confirmation conditions are required |
    |                                             |
    | Independently confirmed T1-T5 base event     |
    | Verified identity and participation         |
    | Located evidence of a mediation role        |
    +---------------------------------------------+
                           |
                           v
                 Independent T6 review
                           |
                    if confirmed
                           v
             T6 attached to the existing event
~~~
{: #fig-mediation-confirmation title="Confirmation dependencies for human mediation"}

The figure shows confirmation dependencies, not the order of all review
activity. Uncertainty or rejection can be recorded while the base is
unresolved. A confirmed mediation finding adds a mechanism to the
existing event; it does not create another base event.

Changing the base retains history but prevents confirmation about the
former base from being applied to the new association. If the base loses
confirmation, dependent mediation becomes pending without deleting its
reviews.

# Inspection and Classification {#classification}

The input is a candidate with its discovery basis and preserved sources.
Inspection produces a located evidence record, a statement of the
proposed contribution, and assessments against the criteria below.
Independent reviewers evaluate that record under {{review}}.

Inspection and review distinguish activities, not mandatory separate
personnel. Each member of the assigned reviewer pair inspects the
sources and develops an assessment independently within their own
review workflow. A separate inspector is not required. A shared evidence
packet can provide source passages and provenance; each reviewer remains
responsible for checking the context and proposing their own mechanism
and object labels. Keep those proposed labels and judgments concealed
as specified in {{independent-assessments}}.

## Evidence Inspection {#inspection}

1. State the precise hypothesis: origin contribution, destination
   activity, and proposed connection. Read the discovery reason as a
   search lead rather than as a conclusion.
2. Check endpoint identity, historical institutional affiliation,
   source revisions, and eligibility against the observation window.
3. Identify what the origin contributed and locate the destination
   passage or process record showing continuity, use, or adoption.
4. Examine the surrounding context, attribution, chronology, and
   alternative explanations. Record contrary evidence as well as
   support, including whether sources repeat the same declaration.
5. For each proposed mechanism, explain which condition the evidence
   supports, contradicts, or leaves unresolved. Identify the object
   and its exact content, rather than inferring it from a title.
6. Record source locations, dates and precision, evidence codes, gaps,
   and the rationale needed for another reviewer to reassess the claim.

Seek missing sources under a documented complementary-search procedure.
Record its scope and stopping rule; lack of a located passage does not
by itself establish absence of a contribution. A candidate that remains
ambiguous proceeds to review with those limitations visible.

The following codes define the method's analytical taxonomy. Mechanisms,
objects, evidence observations, and discovery signals retain separate
fields as shown in {{analytical-layers}}.

## Transfer Mechanisms {#mechanisms}

| Code | Mechanism | Minimum confirmation condition |
| --- | --- | --- |
| T1 | Documentary | Verified IRTF-to-IETF continuity supported by history or an explicit statement, checked against content and affiliations |
| T2 | Technical | A located passage demonstrates use of an identifiable origin solution |
| T3 | Conceptual | Explicit attribution and use of an origin concept, model, or requirement |
| T4 | Experimental or empirical | An identifiable experimental result is used in a destination decision or specification |
| T5 | Organizational or process | A process record links a research agenda to creation or change of IETF activity |
| T6 | Human-mediated | Verified participation on both sides and a documented mediation role in an independently confirmed T1--T5 event |

For T1, validate each claimed rename, adoption, publication-continuity,
or institutional-phase path. Identify the research content carried
forward and verify its continuity and institutional affiliations. WG
adoption or a metadata relationship alone is insufficient. A T1 finding
establishes documented continuity; it does not confer T2--T4 labels
without their separate evidence of substantive use. For T2, normative
dependence identifies the content actually used; a normative reference
alone is insufficient. Similar terminology or a background citation is
insufficient for T3. Citing an experiment without demonstrated use is
insufficient for T4. Thematic proximity between groups is insufficient
for T5. Authorship, chair status, or participation alone is insufficient
for T6.

T6 is auxiliary: it describes mediation of an established event and
cannot establish the underlying contribution by itself. Mechanisms are
not mutually exclusive. Adding mechanism labels does not multiply the
number of consolidated events.

## Transferred Objects {#objects}

| Code | Object |
| --- | --- |
| O1 | Architecture |
| O2 | Model |
| O3 | Terminology or concept |
| O4 | Requirement |
| O5 | Protocol |
| O6 | Mechanism |
| O7 | Algorithm |
| O8 | Data format or structure |
| O9 | API or interface |
| O10 | Experimental result or measurement |
| O11 | Practice or recommendation |
| O12 | Use case |
| O13 | Threat model or security model |
| O14 | Implementation or prototype |
| O15 | Methodology or tool |
| O16 | Other, with an explicit description |

For a T5 event, a research agenda or problem can be recorded as O16 with
a description. A source format, such as a charter or a slide, is not a
transferred object. O5 means a technical communication protocol, not the
study plan. Multiple object labels can apply to one event. New labels
require a versioned change to the coding manual.

## Evidence Observations {#evidence}

Record observations individually, including contradictory and
insufficient evidence. The code describes what was observed, not a
universal rank of evidential strength.

| Code | Observation |
| --- | --- |
| EV-CIT-NORM | Normative citation |
| EV-CIT-INFO | Informative citation |
| EV-CIT-POSSIBLE | Citation whose classification remains pending |
| EV-LINEAGE | Documentary continuity |
| EV-TEXT-USE | Located use |
| EV-TEXT-DERIVATION | Located derivation |
| EV-ADOPTION | Adoption process |
| EV-MEETING | Meeting statement |
| EV-SLIDE | Slide statement |
| EV-MAIL | Mailing-list statement |
| EV-CHARTER | Charter passage |
| EV-BOF | BOF evidence |
| EV-AUTHOR | Authorship or participation |
| EV-CHAIR | Chair participation or role |
| EV-CODE | Code |
| EV-IMPLEMENTATION | Implementation evidence |
| EV-ISSUE | Issue discussion |
| EV-COMMIT | Commit evidence |
| EV-PR | Pull-request evidence |
| EV-OTHER | Another explicitly described source |

Each observation identifies a source URL, preserved artifact, SHA-256,
source version, excerpt, location, event date, date precision, and
collection time. State whether the connection is indirect, explicit, or
independently corroborated. Record unknown values and why they matter to
the decision; do not fabricate dates or passages.

# Independent Review and Decision History {#review}

The input is the inspection record from {{inspection}}, including
preserved evidence, eligibility checks, and recorded contradictions or
gaps. Each reviewer independently proposes mechanism and object labels
as part of their own assessment. The output is two initial
reviews and either a consolidated decision or an explicitly unresolved
review status. Decision consolidation is separate from grouping
candidates into contribution events, as described in
{{event-consolidation}}.

## Independent Assessments {#independent-assessments}

Assign first and second reviews of each candidate to different people.
A study may have more than two reviewers, with different pairs assigned
to different candidates. The adjudicator for a candidate is a third
person outside its assigned pair; a reviewer may adjudicate other
candidates if the declared conflict-of-interest policy permits it.

Record the candidate identifier, assigned reviewers, their roles, and
the allocation policy. Workload allocation may balance assessment
counts and candidate categories and vary pairs, using a recorded seed
when random tie-breaking is used. Such allocation is not a
probability-sampling design for selecting candidates. Preserve existing
assignments and submitted assessments when allocating new candidates;
record any necessary reassignment and its reason without transferring
one person's judgment to another. Operational allocation changes must
be auditable and consistent with the registered study plan; changes to
the declared review design require an explicit plan amendment.

Each reviewer checks the source passages, eligibility, chronology, and
applicable confirmation conditions, then records a decision, mechanism
and object labels, and a reasoned justification. The review identifies which
observations support the decision and which gaps or contradictions
remain. For T6, also check the confirmed-base and role-evidence
conditions in {{human}}.

Keep the initial assessments concealed from the other reviewer until
both have been recorded. A shared evidence packet supports comparison;
it does not replace each person's assessment of whether the passages
support the claim. If a study reviews a sample, identify the sampled
units and the records that received only one review. One positive review
does not establish independent confirmation.

## Decisions and Process Status {#decision-states}

Apply the following decision meanings to the candidate actually under
review:

| Decision | Condition |
| --- | --- |
| Confirmed | Eligibility and the applicable mechanism-specific conditions are supported by located evidence; the identifiable contribution and object labels are justified, and material contradictions have been addressed |
| Rejected | Located evidence contradicts the proposed contribution, or an established eligibility failure excludes it; record the specific reason |
| Uncertain | The available evidence cannot establish or reject the hypothesis, including unresolved identity, affiliation, chronology, use, or material contradictions |

Assess support for each proposed mechanism separately. Confirm only the
supported mechanism and object labels. Failure to establish T2 does not
reject the whole candidate if the evidence supports T3 or another
applicable mechanism; record unsupported proposals and their limitations
separately.

Failure to locate sufficient evidence supports uncertainty rather than
rejection by itself. Rejection concerns the stated hypothesis; it does
not establish that no contribution occurred through another route. A
decision of uncertain is a substantive review result, not an unfinished
review.

Pending means that no effective consolidated decision exists. Record the
reason separately: missing initial review, disagreement awaiting
adjudication, or disagreement that remains unresolved. Preserve the
individual decisions in each case. Disagreement is a comparison of
reviews, not a fourth substantive decision.

## Comparing and Consolidating Decisions {#decision-consolidation}

After both initial reviews exist, compare their decision states and
their sets of mechanism and object labels. Agreement under this method
requires all three to match. Matching reviews yield a consolidated
confirmed, rejected, or uncertain decision. Record the agreement and its
supporting review identifiers.

Agreement about a mechanism with disagreement about an object remains a
disagreement for the consolidated candidate decision. The study may
report label-level agreement separately, but does not report the
candidate as independently confirmed while that disagreement remains
unresolved. Assess agreement from the initial reviews before
adjudication, as described in {{validation}}.

{{fig-independent-review}} summarizes this sequence.

~~~ ascii-art
          Inspected candidate and evidence
                           |
              +------------+------------+
              v                         v
      +-----------------+       +-----------------+
      | First reviewer  |       | Second reviewer |
      | Initial review  |       | Initial review  |
      +-------+---------+       +-------+---------+
              |                         |
              +------------+------------+
                           v
               Compare state and labels
                     /             \
                  agree          disagree
                    |               |
                    |       Third-person adjudication
                    |           /             \
                    |       resolved       unresolved
                    |           |              |
                    +-----+-----+              v
                          v             Pending, with reason
                 Consolidated decision
~~~
{: #fig-independent-review title="Independent review and decision consolidation"}

## Adjudication {#adjudication}

Assign adjudication to a third person after both initial reviews are
available. Reviewers and adjudicators disclose involvement in the case
or other conflicts of interest. The study plan declares how such
conflicts are managed, including reassignment where needed, and the
decision record identifies any remaining limitation.

The adjudicator:

1. Identifies the disputed eligibility finding, evidence interpretation,
   decision state, or label, using both reviews and their sources.
2. Reassesses those points against the same confirmation conditions
   and coding manual used in the initial reviews.
3. Records a reasoned confirmed, rejected, or uncertain decision,
   including the effective label sets, evidence, and treatment of
   the conflicting interpretations.

The adjudicator can request additional sources or clarification. If new
evidence materially changes the record, preserve a new evidence snapshot
and have both original reviewers reconsider it separately, without
coordinating their revised decisions, before completing adjudication.
Retain the initial and later rounds separately; later judgments do not
replace the original blinded reviews or their agreement measurements. A
change to the confirmation criteria is a coding-manual revision, not an
adjudicator's case-specific exception.

Adjudication can resolve a disagreement by concluding that the
hypothesis is uncertain. If no adjudicator is available or the procedure
cannot produce a reasoned consolidated decision, retain pending status
with the unresolved-disagreement reason. Do not force agreement.
Preserve both initial reviews and the adjudication rationale regardless
of outcome.

## Corrections and Reconsideration {#review-corrections}

Corrections append a new review linked to the preceding decision.
Identify the reason, evidence snapshot, and which decisions are
currently effective. An annotation does not silently rewrite a
scientific judgment. New evidence, changed eligibility, or a changed
mediation-base association can require reconsideration and renewed
comparison or adjudication.

Reassess dependent T6 decisions when the underlying T1--T5 base changes
or loses confirmation. Preserve all affected reviews and explain why a
prior conclusion is no longer effective. A participation code or a
complete evidence record does not establish a mediation role without
substantive assessment of the located passage.

# Contribution-Event Consolidation {#consolidation}

Use reviewed hypotheses and the registered event unit to produce a
versioned event mapping. Unresolved grouping decisions remain separate
from established events.

## Consolidating Contribution Events {#event-consolidation}

Consolidating reviewer decisions establishes the effective judgment
about a hypothesis. Event consolidation determines whether several
hypotheses describe the same contribution. Removing duplicate records
performs neither task by itself.

Declare the event unit and grouping rules in the study plan. A usable
unit is an identifiable origin contribution continued, used, or carried
into a destination activity in a documented episode. A contribution may
include several related objects. Alternative levels of aggregation need
an explicit definition and justification so results can be compared at a
stated level.

Define episode boundaries in the plan: which documented adoption, use,
or process decision begins the episode, what evidence marks completion
or continuation, and what would distinguish a later decision in the
same activity. Repeated mentions or publication of another version do
not create another episode by themselves. Record the sources and any
uncertainty supporting those boundaries.

For the unit above, group hypotheses into one event only when the
evidence establishes all of the following:

1. They concern the same identifiable origin contribution, rather than
   merely the same source document, author, or topic.
2. They concern the same destination activity or a documented joint
   activity, rather than independent uses in separate destinations.
3. Their chronology and process evidence support one contribution
   episode, with a recorded rationale for grouping them.

Apply these distinctions consistently:

| Situation | Consolidation treatment |
| --- | --- |
| A draft and its RFC describe the same continuing use in the same activity | One event; retain both document records as support |
| The same algorithm is independently used in two destination activities | Separate events, unless evidence establishes one joint activity under the declared unit |
| Documentary and organizational hypotheses concern the same contribution and episode | They may support one event with several independently justified mechanism labels |
| A person mediates an already confirmed event | Attach T6 to that event; do not create another base event |

Assign each event a stable identifier. Record the contribution,
destination activity, episode dates and precision, supporting candidate
and evidence identifiers, included mechanism and object labels, and the
grouping rationale. A candidate can support more than one event when
distinct contributions or episodes are separately evidenced. Combining
records does not independently confirm a mechanism or object.

Have grouping decisions checked independently and resolve disagreements
through the declared adjudication procedure. Preserve earlier mappings
when new evidence requires merging or splitting events. Unresolved
grouping must remain visible; report it separately or provide a
justified range rather than a definitive deduplicated event total. Only
events whose contribution and grouping decisions are established under
the method enter confirmed consolidated-event counts.

# Validation and Coverage Auditing {#validation}

## State What Is Being Assessed

Define the assessment question, unit, numerator, denominator, and
historical scope before selecting an audit or review sample.
Distinguish:

* Acquisition coverage: which declared sources, queries, revisions,
  groups, and periods were retrieved, unavailable, or not examined.
* Candidate precision: the proportion of proposed hypotheses that meet
  their applicable confirmation conditions after independent review.
* Discovery omissions: eligible connections found by a separate search
  that were absent from the recorded discovery snapshot.

Completing declared requests measures acquisition progress; it does not
establish complete historical coverage. Candidate review can assess
proposed links but cannot by itself estimate connections that discovery
missed. Report uncertain and pending cases explicitly and state how they
enter any estimate rather than treating them as confirmed or rejected by
default.

## Audit Beyond the Candidate Queue

Audit the eligible origin universe independently of the discovered
queue, including origins with no candidates. For a probability audit,
declare the sampling frame, strata, sample sizes, random seed, inclusion
probabilities, precision targets, and treatment of unavailable records.
Use selection weights when the design requires them, and describe the
estimator and its uncertainty.

Inspect selected origins using complementary searches. Record the
sources, search procedures, eligible connections located, and their
presence or absence in the fixed discovery snapshot. Apply the same
confirmation criteria to audit findings as to other candidates. Document
incomplete inspections and nonresponse. Report purposively selected
difficult or illustrative cases separately from the probability sample.

A complementary search can also miss a connection. Describe how its
reference set was constructed and why it is adequate for the stated
assessment. An observed omission rate is conditional on that search and
sample; it does not establish complete recall of all historical
contributions. State which wider claims the design can support.

## Assess Independent Agreement

Assess reviewer agreement before adjudication. Percentage agreement and
Cohen's kappa can be reported with label prevalence, the reviewed units,
missing decisions, and treatment of multiple labels. State whether
agreement is measured per label, for exact label sets, or both. Report
the sampling design if only a subset received two reviews, and preserve
initial disagreements after adjudication or later corrections.

Document coding-manual revisions and distinguish pilot calibration from
independent evaluation. Check procedural reproducibility, source
coverage, and the reliability of substantive judgments separately.
Reproducing a collection or count does not establish corpus
completeness, validate a passage interpretation, or confirm a scientific
conclusion.

# Analysis and Reporting {#reporting}

## Counts and Denominators {#counts}

Report separately:

* Eligible origin units and audited coverage gaps.
* Unique candidates by category and discovery snapshot.
* Discovery families and signals, allowing for overlap.
* Direct-only, chain-only, direct-and-chain, and unknown-topology
  candidate groups, each candidate appearing once in this partition.
* Individual and consolidated review states, including unresolved
  disagreements and missing reviews.
* Confirmed consolidated events, unresolved event groupings, and their
  mechanism and object labels.

A transfer rate needs a validated denominator of eligible, consolidated
origin units. State whether the numerator counts origins with at least
one event or counts events, and ensure the units match the intended
measure. Candidate counts and citation counts are not substitutes for
that numerator. Label totals can exceed event totals because mechanisms
and objects are multilabel. If only a sample was reviewed, distinguish
findings for that sample from design-supported estimates for the
eligible population.

## Dates and Observed Reach {#time-analysis}

Publication-year charts and approximate destination dates describe the
observed documentary material. They are not validated contribution dates
or transfer-latency estimates. Identify the date basis, precision, and
provenance of each reported series, including fallback approximations.
Preserve intervals and unknown dates rather than assigning unsupported
point dates.

For a time-to-event analysis, predefine the event, origin time, entry
into observation, and follow-up period. Treat an origin with no event by
the end of follow-up as right-censored only when event ascertainment is
sufficiently supported over that period; justify that assumption and
state the censoring date. Missing archives, incomplete searches, and
unresolved eligibility are missing-information conditions, not
automatically temporal censoring. Report them separately and explain any
exclusions or sensitivity analysis. Unequal follow-up and changing
coverage affect comparisons. No observation assigns an origin a
fabricated event date or establishes that it will never contribute.

Observed reach can be described through confirmed destination documents,
objects, or groups where the study has validated those units and
affiliations. Do not interpret raw citation counts as technical use or
research quality. Descriptive association does not establish that IRTF
participation caused a destination outcome.

## Reproducibility Package {#reproducibility}

Publish, subject to the evidence-release plan and privacy decisions:

1. The frozen study plan, inventory audit, and coding-manual version,
   including event-unit and sampling definitions.
2. Collection scope, requests, checkpoints, unavailable sources, and
   integrity manifests for preserved artifacts.
3. Normalization and discovery-rule versions, analytical input
   snapshots, and source-to-candidate provenance.
4. Evidence observations, review histories, adjudication rationales,
   effective decisions, and versioned event-consolidation mappings.
5. Analysis definitions, filters, date bases, estimators, and the
   scripts or procedures needed to reproduce counts and tables.
6. Coverage-audit and agreement results, or an explicit statement that
   these validation steps have not been completed.

Distinguish the historical input of a candidate from newer source
collections and screening reports. Historical snapshot totals and
current study-wide totals can differ because older candidates are
retained and new evidence has been added.

# Worked Example {#worked-example}

All document names, passages, and decisions in this example are
fictional. They illustrate the procedure and are not findings from a
historical study. Assume that the dates and affiliations described as
verified are supported by preserved sources within the study window.

## From Source to Candidate

An eligible RG document A defines algorithm K in Section 3. A later
eligible IETF draft B includes a normative reference to A. The preserved
reference establishes the typed relationship B cites A. Discovery
records a CIT signal for the proposed contribution A to B. The candidate
record identifies both source versions, the reference location, the
rule, and unresolved use checks.

At this point the bibliography supports a citation observation, not a
confirmed T2 or an O7 assignment. Each assigned reviewer independently
examines algorithm K as a proposed object and searches the body of B
for evidence of its use, preserving the context and the search outcome.

## Inspection, Review, and Adjudication

Suppose the first reviewer proposes confirmed T2 with O7 based on the
reference, while the second records uncertain because the evidence
packet lacks a passage establishing actual use. The proposed
confirmation fails the T2 condition at that stage. The initial reviews
disagree, so the consolidated candidate remains pending; the initial
agreement assessment records that disagreement.

The adjudicator requests the full preserved revision of B. Inspection
locates a passage in its Section 4 stating, in this fictional example,
"Key derivation follows algorithm K in A, Section 3." Its context
identifies the relevant computation and confirms the reference's
attribution. This is recorded as a located-use observation with its
version, location, provenance, and date information.

Both reviewers then reconsider the new evidence separately as required
by {{adjudication}}. If their revised decisions both confirm T2 and O7,
record the revised agreement and effective decision without replacing
the initial disagreement or its measurement. If the revised decisions
still differ, the third person completes a reasoned adjudication or
records why the disagreement remains unresolved. Documentary succession
has not been established in this example, so T1 is not added.

The same inspection can lead to other outcomes:

| Available evidence for the stated technical-use hypothesis | Review implication |
| --- | --- |
| The use passage and its eligibility are verified, with no unresolved material contradiction | T2 and O7 can be confirmed after the required independent decision process |
| The full revision is unavailable and actual use cannot be established or ruled out | Uncertain; record the missing source and completed search |
| A verified passage explicitly states that B does not use K and discusses A only as a rejected alternative | Reject that technical-use hypothesis; do not infer absence of every possible contribution |

These outcomes depend on the evidence, not on the presence of the CIT
signal. A matching author address would require a separate identity and
mediation-role investigation before adding T6.

## From Decisions to an Event

Suppose a later eligible revision of B and its eligible published RFC
retain the same use of K in the same destination activity and documented episode. After the
required evidence and grouping review, map their supporting candidate
records to one event E1 with T2 and O7. Retain all document versions and
the grouping rationale. Independently demonstrated use of K in a
different destination activity is a separate event under this unit,
unless evidence supports the declared joint-activity rule.

The report distinguishes the candidate records, initial and revised
review decisions, and the consolidated event E1. It does not present the
number of versions or citations as the number of contributions.

# Methodological Limitations {#limitations}

Source acquisition and hypothesis discovery are separate procedures.
Record the coverage and completion status of each discovery route,
together with its input snapshot and rule version. An unfinished search,
missing inputs, unavailable sources, and a completed search with zero
matches are different outcomes. Revised rules require a new documented
screening pass before their results can be compared with earlier
findings.

Discovery does not establish technical, conceptual, or empirical use,
verify person identity, or consolidate hypotheses into scientific
events. These conclusions require the evidence, review, and
consolidation procedures defined above. Probability audits and agreement
assessment require an explicit design and completed observations. Causal
or social-network claims require additional analytical designs and
cannot be inferred from the discovery records alone.

Coverage is limited by mutable metadata, incomplete archives, missing
group histories, unavailable revisions, ambiguous identities, restricted
search universes, language-dependent screening, and undocumented
influence. Declare these limits for each study and assess their possible
effects on the findings. A zero candidate count is not evidence that no
contribution occurred. Any conclusion that no evidence was found must
identify the sources, historical scope, search procedures, and remaining
gaps; it is distinct from a conclusion that no contribution occurred.

# Security Considerations {#security}

This method does not change a network protocol. Its principal security
concerns are the integrity of research artifacts, safe handling of
untrusted source material, and protection of review records. Treat
downloaded texts, API fields, and links as untrusted input. Rendering
evidence should not execute embedded content, and access to collection,
review, correction, and export functions should follow assigned roles.

Verify preserved bytes against their recorded hashes when deriving or
exporting evidence. Retain acquisition and correction history to make
unexpected changes detectable. A matching hash is not authentication of
a historical claim. Exporting first-round reviews before both
independent decisions exist can compromise the study's blinding
procedure.

# Privacy Considerations {#privacy}

Public submissions and process records can contain names, addresses,
affiliations, and statements about individuals. Address matches remain
identity hints until verified; they do not justify assertions about a
person's influence, intent, or responsibility.

The study plan identifies what personal information is needed and what
can be released. Publish only the identifying detail needed to support
the research claim. Separate reviewer access from public release where
appropriate, and document any redaction or restricted artifact together
with its effect on reproducibility. Preserve contradictions and
uncertainty rather than turning an automated address match into a
personal attribution.

# IANA Considerations {#iana}

This document has no IANA actions.

--- back

# Evidence Extraction Record {#extraction}

The following record is a methodological checklist, not a new
interchange format or a claim that every field can be filled
automatically.

| Field | Content |
| --- | --- |
| Study execution | Frozen plan version, cutoff, and inventory |
| Candidate | Stable identifier, category, and endpoint identities |
| Discovery basis | Signal, rule version, path, and input snapshot, or manual origin |
| Contribution | Identifiable object or agenda and proposed mechanism |
| Source | URL, source version, preserved artifact, and SHA-256 |
| Located evidence | Excerpt, section/page/line or other reproducible location, and context |
| Chronology | Event date, precision, observation/publication distinctions, and collection time |
| Interpretation | Supported claim, historical affiliations, contradictions, and missing checks |
| Review | Reviewer role, evidence snapshot and round, decision, mechanism/object labels, rationale, conflict disclosure, and correction history |
| Consolidation | Decision agreement or adjudication; separately reviewed event identifiers, candidate mappings, grouping criteria, and rationale |
| Mediation dependency | Linked T1--T5 base, verified participation, and role-bearing evidence |



# Source-Specific Screening Conventions {#source-conventions}

These conventions describe ways to operationalize the method with
particular sources. Declare which profile a study uses, including any
extensions, before interpreting its search results. Record exclusions
and input versions. These choices do not replace confirmation criteria
or constitute evidence of complete historical coverage.

## Relationship Vocabulary {#source-relationships}

Preserve the Datatracker relationship catalog {{RELATIONSHIP-CATALOG}}
and the RFC index {{RFC-INDEX}} used by the study. One mapping is:

| Source relationship or observation | Family or purpose |
| --- | --- |
| `refnorm`, `refinfo`, `refold`, or parsed bibliographic references | CIT, retaining normative/informative/unspecified subtype |
| `refunk` | Possible direct CIT lead |
| `replaces`, `became_rfc`, or definite historical rename | CONT with factual direction and succession order preserved |
| `possibly-replaces` | Possible direct CONT lead; no transitive bridge |
| `updates`, `obs`, or normalized inverse forms | EVOL from earlier work to later work |
| Explicit stream change or ordered affiliation observations | FASE subject to identity, lineage, and temporal checks |
| `contains` or RFC-index `is-also` | Series membership for pending citation-component resolution |
| `downref-approval` or `conflrev` | Procedural context |
| `tops`, `tois`, `tobcp`, `toexp`, `toinf`, `tohist` | Standards-status process context |

Derived reference extraction, inverse normalization, and historical
rename observations identify their derivation and source. Do not present
them as additional codes in the source catalog. Documentary and group
inventories can use persistent numeric Datatracker IDs; retain
historical identifiers and aliases rather than relying only on current
acronyms.

## Charter Dates {#source-dates}

Preserved Datatracker `new_revision` and `iesg_approved` events can
support revision publication and charter approval respectively. Bind
each event to its named revision. In a conservative screening profile,
an approval recorded under a draft revision may be associated with the
next numbered approved revision only when the preserved records show
consecutive revisions and publication at the exact approval timestamp.
Preserve the original event, revision identifiers, and binding
rationale. A missing or ambiguous association remains pending; a
different binding convention needs explicit source support and a
declared rule.

This convention supports dates of charter events. It does not establish
when research was first available, when adoption occurred, or whether
the attribution and mandate concern the same work.

## Address-Based Authorship Screening {#source-authorship}

An exact-address profile uses authorship in preserved posted draft
submissions within the cutoff. Normalize the address domain while
preserving local-part case. Do not infer aliases or person identity from
similar names. Record the address's source document, revision,
submission date, and historical-affiliation evidence.

For `HUM_SHARED_AUTHOR`, compare exact endpoint document names of a
documentary candidate and preserve their separate author observations. A
base can remain pending. Do not duplicate one author list into two
institutional phases of a same-document case.

For an independent date-only `HUM_AUTHOR_INTERSECTION` profile:

1. Require an unambiguous historical affiliation observed by the start
   of each submission day; retain the source date precision and the
   convention used to interpret that boundary.
2. Require the origin submission to be strictly earlier than the
   destination submission. Exclude same-document pairs and record
   conflicting, unknown, or insufficiently precise dates or phases.
3. Separate pairs with an existing documentary candidate or a recorded
   direct relationship in either direction. Record whether indirect
   paths were searched and the limits of that search.
4. Keep one address/document-pair lead as an observation, not as a
   verified person or contribution event.

The day-boundary convention is conservative screening rather than a
claim that affiliation histories are complete. Studies using other
sources, identity hints, or temporal rules declare those differences and
evaluate their effects on coverage. Confirmation still requires verified
participation and a role-bearing passage in a confirmed base.

# Acknowledgments
{:numbered="false"}

Acknowledgments will be added as contributions to this document are
received and agreed with the people concerned.
