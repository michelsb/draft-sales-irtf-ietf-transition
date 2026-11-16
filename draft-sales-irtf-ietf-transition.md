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
    ins: "M. Bonfim"
    fullname: "Michel Bonfim"
    email: "michelsb@gmail.com"

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
signals from confirmed contributions and defines separate classifications
for transfer mechanisms, transferred objects, and evidence observations.
It also describes coverage audits, reporting requirements, and limits
on interpreting citations, document continuity, group relationships,
shared authorship, and event dates. Discovery identifies hypotheses
for inspection; conclusions about research use require the applicable
evidence and independent review.

--- middle

# Introduction {#intro}

The IRTF organizes research on Internet-related topics, while the IETF
develops engineering specifications and standards. Their different
roles are described in {{RFC2014}}. Research can contribute to IETF work
through document continuity, use of a technical solution, adoption of a
concept or experimental result, organizational processes, or mediation
by participants. These mechanisms need not coincide with publication
of a document or creation of a working group.

The research question addressed by this method is:

> Which IRTF results were demonstrably used in IETF work, through which
> mechanisms, and with what observed reach?

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
identifies material for inspection; human review establishes whether
the mechanism-specific conditions are met.

## Scope and Status {#scope}

This is an individual methodological proposal. It does not claim
research-group adoption, IRTF consensus, or IRSG approval. The intended
submission stream in the source metadata does not establish any of
those conditions.

The method covers documentary, organizational, and human mediation
inquiries using recoverable historical sources. Each study declares
its source coverage, acquisition procedures, and search limitations.
Documentary records and complementary process evidence can both be
needed to confirm a case.

This document specifies the research procedure and its interpretive
limits independently of any particular software or collection system.
It reports no completed corpus, confirmed transfers, coverage estimate,
or measured reviewer agreement. Each empirical application needs its
own registered study plan and results.

## Method Overview {#method-overview}

The procedure separates source acquisition, hypothesis discovery,
scientific review, and reporting, as shown in {{fig-method-overview}}.

~~~ ascii-art
       Versioned plan and eligible universe
                       |
                       v
           Collect and preserve sources
                       |
                       v
       Normalize identities and relationships
                       |
     +-----------------+------------------+
     v                 v                  v
 Documentary     Organizational     Human mediation
 hypotheses        hypotheses        hypotheses
     |                 |                  |
     +-----------------+------------------+
                       |
                       v
       Independent review and adjudication
                       |
                       v
     Manual event consolidation and reporting
~~~
{: #fig-method-overview title="Overview of the research procedure"}

Coverage auditing also searches outside the discovered queue. Human
mediation leads can begin without a documentary or organizational
base, but confirmation remains dependent on an established event.

# Terminology and Units of Analysis {#terms}

The words "requires" and "confirmation condition" below describe the
research procedure. This document does not define a network protocol
or use BCP 14 requirement keywords.

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

Study execution:
: An investigation associated with a frozen study-plan version, historical
  cutoff, inventory, and reviewer assignments. Sources and derived
  snapshots can accumulate within that fixed scope.

An address is not a verified person; a document pair is not a confirmed
event; and a signal count is not a count of contributions.

# Study Design and Eligibility {#design}

## Versioned Study Plan {#plan}

Before collection, register the following study choices:

1. The research question, inclusion and exclusion criteria, and
   intended interpretation of a contribution.
2. An upper historical cutoff, represented by the last instant of a
   selected month in UTC.
3. A verified inventory of active and concluded RGs, including acronyms
   and persistent numeric Datatracker identifiers, with a documented
   inventory audit.
4. The publication plan for results, evidence, and limitations.
5. Separate first-reviewer, second-reviewer, and adjudicator roles,
   or explicit limitations where those roles cannot be assigned.
6. Procedures for coverage auditing, independent review, disagreement
   resolution, and assessment of agreement before adjudication.
7. The selection design if only part of the eligible universe will
   receive manual inspection.

Freeze these choices before beginning the investigation. Specify
whether the documentary scope includes all recoverable history, drafts
and RFCs in all states, and all recoverable IETF destinations, or a
justified subset. The cutoff is an upper bound, not the beginning of
the search period; record any lower bound separately.

Dividing acquisition or screening into operational batches does not
constitute scientific sampling. If the question, eligibility scope, or
scientific confirmation criteria change, register a new plan version
and a separately identified study execution. Applying an updated
discovery rule to preserved sources can enlarge a queue within the
existing scope, provided the rule version,
input snapshot, and earlier decisions remain auditable.

## Endpoint Eligibility {#eligibility}

Establish an origin's IRTF affiliation from preserved group, document,
or historical records, checked against the frozen inventory. A name
prefix alone is insufficient. Establish the destination's IETF
affiliation independently; publication as an RFC is insufficient.

Retain ambiguous, unknown, and multiple affiliations explicitly. An
unambiguous current label does not resolve a conflicting history.
Where a single documentary identity appears in both institutional
phases, review the ordered phase observations rather than treating
the two labels as two independent documents.

Known post-cutoff endpoints and intermediates are excluded from
eligible historical paths. Undated material remains temporally
pending where its eligibility cannot be established. Collection time
does not substitute for an event date.

# Sources, Preservation, and Chronology {#sources}

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
participation histories and documented person aliases. Define which
of these sources will be searched and how. Report the sources and
historical periods actually examined, including gaps between planned
and completed searches.

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

Derived observations retain their source references, transformation
or rule identifiers, and analytical snapshot. Reanalysis preserves
candidate identifiers, investigator annotations, and review history.
A lead not proposed by a newer snapshot can remain as a historical
candidate; report that condition rather than silently deleting it.

A checksum verifies equality with the preserved bytes. It does not
prove that the source statement is true, historically complete, or
independent of another source. Copies of the same declaration do not
constitute independent corroboration.

## Distinct Dates {#dates}

Keep source-event time, publication time, observation time, and
collection time separate. Preserve the precision supplied by the
source, including year-only or month-only dates and unknown dates.

Charter revision observation, revision publication, and charter
approval are distinct observations. Preserved Datatracker
`new_revision` and `iesg_approved` events can support the latter dates. Binding an approval recorded under a draft
revision to the next numbered approved revision requires a matching
publication timestamp; missing or ambiguous events leave the binding
pending.

Even a supported charter approval date does not establish when the
originating research became available or when its adoption occurred.
Those are separate chronological questions for review.

# Normalization and Typed Documentary Paths {#normalization}

Normalize document identifiers, explicit aliases, inverse relationship
forms, and definite historical renames while retaining the original
records. Keep documentary succession separate from technical evolution,
series membership, publication stream, and standards status.

Preserve both the factual relationship direction and the projected
direction of a possible research contribution. For example, a source
record can point from a citing document to a cited document, while the
contribution hypothesis is evaluated from cited work to citing work.

The relationship vocabulary is taken from the preserved Datatracker
catalog {{RELATIONSHIP-CATALOG}}. The following families are local
screening categories, not an IETF taxonomy of scientific transfer.

| Family | Inputs | Contribution projection |
| --- | --- | --- |
| CIT: citation | `refnorm`, `refinfo`, `refold`, parsed references; possible `refunk` | Cited to citing work |
| CONT: continuity | `replaces`, `became_rfc`, definite historical renames; possible `possibly-replaces` | Earlier work to successor |
| EVOL: technical evolution | `updates`, `obs`, and normalized inverse forms | Updated or obsoleted work to later work |
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
connections through intermediate items. A candidate with both direct
and chain signals belongs to the "direct and chain" group. These
labels describe structure, not confidence or confirmation.

{{fig-path-topology}} illustrates these groups using CIT paths. A is
an eligible IRTF origin, D is an eligible IETF destination, and X is
an intermediate document. B and C retain their definitions above.
The examples assume that the displayed paths are the recorded support
for each pair.

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
individual discovery families and signals can overlap. Panel (d)
does not establish use of A by D and cannot serve as a CIT path.

Possible references and replacements create direct leads only; they
do not serve as transitive bridges. Two successive citations do not
establish use of the earliest work. Shared ancestors, undirected
connectivity, and shared series membership do not establish succession.
The engine selects representative admissible paths, not every path or
a generic transitive closure of the graph.

An RFC-to-series membership from `contains` or RFC-index `is-also`
can resolve a series citation into a pending component hypothesis.
Present-day membership does not establish historical composition or
which component the citing document used.

The relationships `downref-approval`, `conflrev`, and the status-process
codes `tops`, `tois`, `tobcp`, `toexp`, `toinf`, and `tohist` supply
context. They are not independent technical-transfer signals or
generic bridges. Approval, conflict review, and standards-status
changes do not by themselves establish a stream transition or use.

For FASE, affiliation-derived ordering uses the earliest known IETF
presence; an explicit event supports the local transition it records.
Neither general connectivity nor endpoint ordering dates every link.

# Candidate Discovery {#discovery}

The three categories below identify different units of inspection.
One underlying case can generate related candidates in several
categories. The categories do not compete as alternative final labels.
Manual hypotheses can also be recorded, without inventing automated
discovery signals.

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
process linking research to the creation or change of IETF activity.
The following are derived rules, not additional Datatracker document
relationship codes:

| Signal | Screening observation |
| --- | --- |
| ORG_DOCUMENT_LINKS | A documentary candidate connects an observed RG document and WG document |
| ORG_DOCUMENT_CONTINUITY | That documentary support also carries continuity evidence |
| ORG_CHARTER_REFERENCE | A verified preserved WG charter contains a located RG mention |
| ORG_TYPE_CHANGE | Verified consecutive dated observations show RG then WG for the same persistent group identifier |
| ORG_AGENDA_ADOPTION | A preserved charter contains explicit RG research attribution and a nearby WG work mandate |

Document-supported group signals have chain topology. Verified charter
mentions, same-identifier type changes, and agenda-adoption signals
have direct topology. These structures do not establish group
succession or research adoption.

The origin belongs to the frozen RG inventory. Supporting documentary
candidates and artifacts belong to the same study execution. Declare
whether charter searches cover all eligible groups independently or
only pairs selected by earlier screening. A search restricted to
previously selected pairs cannot establish coverage of all charters.
Different-identifier group succession and BOF or other process routes
require explicit search procedures if included in the study scope.

Agenda-adoption screening seeks an explicit attribution of research
to an RG and a WG mandate concerning that work. Relevant mandates can
include updating, integrating, adopting, standardizing, or adding work
to protocols. Preserve the attribution and mandate passages separately
and record the resulting signal on the RG/WG hypothesis. If lexical
patterns or a proximity threshold select passages, declare their
language coverage, parameters, and version before screening. Textual
distance is a selection criterion, not evidence of a semantic link.

Review checks that both passages concern the same research result,
that the origin predates the relevant mandate, and that process
evidence supports the claimed connection. Textual proximity, a group
mention, cooperation, or thematic similarity is insufficient. Adoption
of work is distinct from succession of organizations.

## Human Mediation Candidates {#human}

Human discovery uses usable author addresses in preserved, posted
draft submissions within the cutoff. Domain normalization preserves
local-part case. Matching is by exact resulting address, not by name
similarity or inferred aliases. RFC authorship is not automatically
inherited from predecessor drafts.

### Documentary-Base Shared Authorship

`HUM_SHARED_AUTHOR` compares authorship observations on the exact
endpoint document names of an existing documentary candidate. An
address observed on both sides creates a possible chain through that
address hint, linked to the documentary base. A single author list is
not duplicated into two institutional phases of the same document.

The base can still be pending when discovery occurs. This route does
not apply the independent route's stricter historical-phase and
submission-order screening. Its output therefore has a different
screening scope.

### Independent Author Intersections

`HUM_AUTHOR_INTERSECTION` searches preserved submissions without
requiring an existing documentary candidate. Each usable authorship
observation requires an unambiguous historical phase observed by the
start of its submission day. The origin submission is strictly earlier
than the destination submission. Same-document pairs and conflicting
or unknown phases are excluded.

Pairs with an existing documentary candidate or a recorded direct
relationship in either direction are separated from this exploratory
queue. Remaining address matches create human mediation leads without
a linked base. The absence of a recorded direct relationship does not
exclude indirect paths or missing evidence. Indirect paths are not
exhaustively searched by this screening step.

One lead represents one address/document-pair observation, not one
verified person or event. Identity, historical group types, continuous
affiliations, actual contribution, and mediation remain unverified.
This route is a separate discovery action; completion of the
documentary-base route does not imply completion of this search.

### Linking and Confirming a Mediation Claim

A human lead can later be associated with a documentary or
organizational base in the same study execution, with a recorded
justification. That association does not confirm the contribution or the person.
T6 confirmation requires an independently consolidated T1--T5 base,
verified participation, and a located passage documenting mediation.

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

The figure shows confirmation dependencies, not the order of all
review activity. Uncertainty or rejection can be recorded while the
base is unresolved. A confirmed mediation finding adds a mechanism
to the existing event; it does not create another base event.

Changing the base retains history but prevents confirmation about the
former base from being applied to the new association. If the base
loses confirmation, dependent mediation becomes pending without
deleting its reviews.

# Classification and Confirmation Conditions {#classification}

The following codes define the method's analytical taxonomy. Discovery
families, mechanism labels, object labels, and evidence codes describe
different things and are recorded separately.

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
or institutional-phase path. WG adoption alone is insufficient. For
T2, normative dependence identifies the content actually used; a
normative reference alone is insufficient. Similar terminology or a
background citation is insufficient for T3. Citing an experiment
without demonstrated use is insufficient for T4. Thematic proximity
between groups is insufficient for T5. Authorship, chair status, or
participation alone is insufficient for T6.

T6 is auxiliary: it describes mediation of an established event and
cannot establish the underlying contribution by itself. Mechanisms
are not mutually exclusive. Adding mechanism labels does not multiply
the number of consolidated events.

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

For a T5 event, a research agenda or problem can be recorded as O16
with a description. A source format, such as a charter or a slide,
is not a transferred object. O5 means a technical communication
protocol, not the study plan. Multiple object labels can apply to one
event. New labels require a versioned change to the coding manual.

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
collection time. State whether the connection is indirect, explicit,
or independently corroborated. Record unknown values and why they
matter to the decision; do not fabricate dates or passages.

Legacy E0--E5 descriptors are not a universally ordered scale. Do not
sum them, average them, or select their maximum to confirm an event.
Apply the mechanism-specific conditions instead.

# Independent Review and Decision History {#review}

Assign first and second reviews to different people and adjudication
to a third person. Keep each reviewer's initial assessment concealed
from the other reviewer until both have recorded their decisions.

Use the following review sequence:

1. Inspect the candidate unit, discovery reasons, preserved paths,
   source coverage, and unresolved checks.
2. Verify endpoint identity, historical affiliation, chronology, and
   the identifiable object or agenda under investigation.
3. Locate the relevant passage in its preserved revision and inspect
   the surrounding context, provenance, and counterevidence.
4. Apply the T1--T6 conditions and O1--O16 labels. Record a confirmed,
   rejected, or uncertain decision and its justification.
5. Have the second reviewer decide independently before revealing
   either review to the other reviewer.
6. Consolidate matching decisions or adjudicate disagreements only
   after both reviews exist. Preserve the disagreement and rationale.

For decision consolidation under this method, agreement requires
matching decision state, mechanism labels, and object labels. A separate
adjudicator can resolve a disagreement after both reviews. Pending means that
no effective consolidated decision exists; unresolved disagreement
remains distinguishable from uncertainty and rejection.

{{fig-independent-review}} summarizes the decision flow. Reviewers
complete their own decisions before comparison. Agreement is assessed
before adjudication; both agreement and adjudication can result in a
confirmed, rejected, or uncertain consolidated decision.

~~~ ascii-art
           Candidate and preserved evidence
                           |
              +------------+------------+
              v                         v
      +-----------------+       +-----------------+
      | First reviewer  |       | Second reviewer |
      | Own decision    |       | Own decision    |
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
                          v                  Pending
                 Consolidated decision
~~~
{: #fig-independent-review title="Independent review and decision consolidation"}

Missing reviews and disagreement awaiting adjudication remain pending.
All branches retain the individual decisions and any later corrections.

One positive review does not establish independent confirmation. If
the study lacks a second reviewer or adjudicator, disclose the
resulting limitation instead of reporting that role as completed.
Measure agreement before adjudication as described in {{validation}}.

Corrections append a new review linked to the preceding decision.
Annotations do not silently rewrite scientific judgments. New source
material or a changed base association can require an explicit new
review. Retain all versions, while identifying which decisions are
currently effective.

For mediation, also enforce the base and role-evidence conditions in
{{human}}. A source code indicating authorship or chair participation
does not satisfy the mediation-role requirement by itself. A complete
evidence record does not establish that its passage supports the
claimed role; reviewers must assess that substantive connection.

# Validation and Coverage Auditing {#validation}

Audit the eligible origin universe independently of the discovered
queue. Reviewing only retrieved candidates can assess those
candidates but cannot estimate cases missed by discovery.

If using a probability audit, declare its sampling frame, strata,
sample sizes, random seed, inclusion probabilities, and precision
targets. Inspect selected origins using complementary searches and
record which eligible connections were absent from discovery.
Report difficult or illustrative cases selected purposively
separately from the probability sample. Document the selection
procedure, selected units, completed inspections, and estimation
procedure so the audit can be reproduced.

Assess independent reviewer agreement before adjudication. Percentage
agreement and Cohen's kappa can be reported, accompanied by label
prevalence, the reviewed units, missing decisions, and the treatment
of multiple labels. For multilabel coding, state whether agreement
is measured per label, for exact label sets, or both. Preserve the
original disagreements even after adjudication.

Document coding-manual revisions and distinguish pilot calibration
from independent evaluation. Check procedural reproducibility, source
coverage, and the reliability of substantive judgments separately.
Reproducing a collection or count does not establish corpus
completeness, validate a passage interpretation, or confirm a
scientific conclusion.

# Analysis and Reporting {#reporting}

## Counts and Consolidation {#counts}

Report separately:

* Eligible origin units and audited coverage gaps.
* Unique candidates by category and discovery snapshot.
* Discovery families and signals, allowing for overlap.
* Direct-only, chain-only, direct-and-chain, and unknown-topology
  candidate groups, each candidate appearing once in this partition.
* Individual and consolidated review states, including unresolved
  disagreements and missing reviews.
* Confirmed findings and any manually consolidated contribution
  events, with their mechanism and object labels.

Before reporting event totals, state the rule for deciding whether
different document versions, paths, group hypotheses, or mediation
claims concern the same contribution. Maintain their mappings to the
consolidated event. Removing duplicate candidate records and
consolidating reviewer decisions are distinct from deciding whether
several hypotheses describe the same scientific event.

A transfer rate needs a validated denominator of eligible,
consolidated origin units. State whether the numerator counts origins
with at least one event or counts events, and ensure the units match
the intended measure. Candidate counts and citation counts are not
substitutes for that numerator. Label totals can exceed event totals
because mechanisms and objects are multilabel.

## Dates and Observed Reach {#time-analysis}

Publication-year charts and approximate destination dates describe
the observed documentary material. They are not validated transfer
dates or transfer-latency estimates. Identify the date basis,
precision, and provenance of each reported series, including fallback
approximations.

Origins without an observed event by the cutoff are right-censored,
not assigned a fabricated event date or assumed never to contribute.
Unequal follow-up periods, incomplete histories, and different
collection coverage can change observed rates and timelines.

Observed reach can be described through confirmed destination
documents, objects, or groups where the study has validated those
units and affiliations. Do not interpret raw citation counts as
technical use or research quality. Descriptive association does not
establish that IRTF participation caused a destination outcome.

## Reproducibility Package {#reproducibility}

Publish, subject to the evidence-release plan and privacy decisions:

1. The frozen study plan, inventory audit, and coding-manual version.
2. Collection scope, requests, checkpoints, unavailable sources, and
   integrity manifests for preserved artifacts.
3. Normalization and discovery-rule versions, analytical input
   snapshots, and source-to-candidate provenance.
4. Evidence observations, review histories, adjudication rationales,
   effective decisions, and event-consolidation mappings.
5. Analysis definitions, filters, date bases, and the scripts or
   procedures needed to reproduce reported counts and tables.
6. Coverage-audit and agreement results, or an explicit statement that
   these validation steps have not been completed.

Distinguish the historical input of a candidate from newer source
collections and screening reports. Historical snapshot totals and
current study-wide totals can differ because older candidates are
retained and new evidence has been added.

# Methodological Limitations {#limitations}

Source acquisition and hypothesis discovery are separate procedures.
Record the coverage and completion status of each discovery route,
together with its input snapshot and rule version. An unfinished search,
missing inputs, unavailable sources, and a completed search with zero
matches are different outcomes. Revised rules require a new documented
screening pass before their results can be compared with earlier findings.

Discovery does not establish technical, conceptual, or empirical use,
verify person identity, or consolidate hypotheses into scientific events.
These conclusions require the evidence, review, and consolidation
procedures defined above. Probability audits and agreement assessment
require an explicit design and completed observations. Causal or
social-network claims require additional analytical designs and cannot
be inferred from the discovery records alone.

Coverage is limited by mutable metadata, incomplete archives, missing
group histories, unavailable revisions, ambiguous identities, restricted
search universes, language-dependent screening, and undocumented
influence. Declare these limits for each study and assess their possible
effects on the findings. A zero candidate count is not evidence that
no contribution occurred. Any conclusion that no evidence was found
must identify the sources, historical scope, search procedures, and
remaining gaps; it is distinct from a conclusion that no contribution
occurred.

# Security Considerations {#security}

This method does not change a network protocol. Its principal security
concerns are the integrity of research artifacts, safe handling of
untrusted source material, and protection of review records. Treat
downloaded texts, API fields, and links as untrusted input. Rendering
evidence should not execute embedded content, and access to collection,
review, correction, and export functions should follow assigned roles.

Verify preserved bytes against their recorded hashes when deriving or
exporting evidence. Retain acquisition and correction history to make
unexpected changes detectable. A matching hash is not authentication
of a historical claim. Exporting first-round reviews before both
independent decisions exist can compromise the study's blinding
procedure.

# Privacy Considerations {#privacy}

Public submissions and process records can contain names, addresses,
affiliations, and statements about individuals. Address matches remain
identity hints until verified; they do not justify assertions about a
person's influence, intent, or responsibility.

The study plan identifies what personal information is needed and
what can be released. Publish only the identifying detail needed to
support the research claim. Separate reviewer access from public
release where appropriate, and document any redaction or restricted
artifact together with its effect on reproducibility. Preserve
contradictions and uncertainty rather than turning an automated
address match into a personal attribution.

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
| Review | Reviewer role, decision, mechanism/object labels, rationale, and correction history |
| Consolidation | Independent agreement or adjudication; event mapping where applicable |
| Mediation dependency | Linked T1--T5 base, verified participation, and role-bearing evidence |

# Source Metadata and Editorial Notes {#editorial}

This section is to be removed before publication as an RFC.

The source retains the existing author name and email address. An
institutional affiliation and postal address have not been supplied
and are omitted. Confirm the author list and any affiliations before
submission; do not copy author or organization details from another
draft.

The source uses the existing draft name and intended IRTF stream,
with the Informational category. No adopted research group, mailing
list, or consensus setting is supplied. Revisit these
metadata if the document's actual submission context changes. The
blank source date is resolved by the build tools.

The Markdown structure follows the YAML metadata and abstract,
middle, references, and back-matter conventions illustrated by the
[hash-to-curve draft source](https://github.com/cfrg/draft-irtf-cfrg-hash-to-curve/blob/main/draft-irtf-cfrg-hash-to-curve.md).
That document is a formatting example, not evidence for this research
method. The references in this document are informative; no normative
reference is needed to define an interoperable protocol.

Each empirical study identifies the version of this method and any
registered deviations or extensions. Document study-specific procedures
and supporting materials in its reproducibility package, separately
from the methodological specification.

# Acknowledgments
{:numbered="false"}

Acknowledgments will be added as contributions to this document are
received and agreed with the people concerned.
