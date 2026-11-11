# Documentation Standards

| Field | Value |
| --- | --- |
| Purpose | Foundational reusable standard for documentation produced during Project Planning and Scope, Requirements Analysis, and System Design and Architecture. |
| Status | In review |
| Version | 0.4.1 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent (sole authorized writer). |
| Authority / approval | v0.3.1 approved by Human user on 2026-11-09. The changes incorporated in v0.4.0 and v0.4.1 were approved by Human user on 2026-11-10, under Software Architect authorization of 2026-11-10 naming `framework/standards/documentation-standards.md`, `framework/standards/README.md`, and `framework/workflows/change-control.md`. v0.4.1 is not approved. |
| Validation | v0.2.0: independent validation PASS (second review, 2026-11-09). v0.3.1: independent validation PASS (re-review, 2026-11-09). v0.4.0: validation was pending when v0.4.1 was prepared; no validation result exists for v0.4.0. v0.4.1: pending independent validation. |
| Applies to | All generated project documentation under `docs/`, including persisted research and validation reports; all reusable templates and workflows that describe documentation structure; and the framework standards themselves (see Section 1.2). |
| Not applicable to | Application implementation, programming, source code, executable components, and repository configuration. |
| Related documents | [`README.md`](./README.md) — standards index and governance. |

---

## 1. Documentation purpose and scope

### 1.1 Purpose

This standard defines how documentation is written, structured, classified, identified, traced, sourced, versioned, and judged complete within this multi-agent software engineering system.

Its objective is consistent, accurate, traceable, and honest documentation. Documentation produced under this standard must allow a reader to determine:

- What is confirmed, and on what authority.
- What is assumed, and by whom it must be verified.
- What is recommended, and whether it has been approved.
- What remains unknown or undecided.
- How each statement relates to the requirements and decisions that depend on it.

### 1.2 Scope

This standard applies to documentation for the three supported lifecycle phases:

1. **Planning and Scope** — charter, scope, stakeholders, feasibility, budget, roadmap, risks, assumptions.
2. **Requirements Analysis** — requirements specification, functional and non-functional requirements, user stories, use cases, acceptance criteria, business rules, traceability.
3. **System Design and Architecture** — architecture overview and views, technology specification, data model, API contracts, integrations, security architecture, UX/UI specifications, decision records, deployment architecture.

It applies to:

- Generated project documents under the six designated `docs/` directories.
- Research reports persisted under `docs/04-research/` and validation reports persisted under `docs/05-validation/`.
- Reusable templates and workflows that prescribe document structure, to the extent they describe documentation rather than procedure.

**Self-application.** This standard also governs the framework standards themselves, including this document and [`README.md`](./README.md) in `framework/standards/`. Those assets follow this standard's requirements for structure, metadata, information classification, versioning, and change history, and are subject to its quality criteria where those criteria are applicable. Their subject matter remains framework governance rather than project documentation, so requirements specific to project deliverables — including project-level traceability chains and stakeholder approval of project decisions — apply only where relevant. Where a requirement is not applicable to a standards asset, the asset **MUST** mark it `Not applicable` with a reason, consistent with Section 3.3 and Section 10. In particular, `framework/standards/README.md` maintains its own change history in Section 9 of that file.

### 1.3 Out of scope

This standard does **not**:

- Define or encourage application programming, implementation scope, or executable components.
- Define coding standards, build, test-automation, or deployment procedures.
- Authorize approvals of scope, budget, requirements, technology, or architecture. Approval authority remains with the human user, coordinated by the Software Architect.
- Replace project-specific decisions with generic rules.

### 1.4 Normative language

| Keyword | Meaning |
| --- | --- |
| **MUST / MUST NOT** | Mandatory rule of this standard. Deviation requires explicit authorization from the Software Architect and must be recorded in the affected document. |
| **SHOULD / SHOULD NOT** | Recommended practice. Deviation is permitted when justified and recorded. |
| **MAY** | Optional practice. |

Clauses are mandatory unless explicitly marked as recommended or optional.

---

## 2. Writing principles

### 2.1 Clarity

- Documents **MUST** state their purpose and intended audience near the beginning.
- Sentences **SHOULD** express one primary obligation or statement.
- Ambiguous terms such as "fast", "secure", "user-friendly", "soon", or "appropriate" **MUST** be replaced by measurable or explicitly qualified statements, or classified as `OPEN QUESTION`.
- Pronouns and implicit references **SHOULD** be replaced by explicit references to the named actor, component, or document.

### 2.2 Precision

- Statements **MUST** be specific enough to be verified, contradicted, or accepted.
- Quantitative claims **MUST** include units, basis, and conditions.
- Conditions and exceptions **MUST** be stated explicitly rather than implied.
- Terms with project-specific definitions **MUST** be defined once, in a single location, and referenced thereafter.

### 2.3 Consistency

- Terminology, capitalization, and identifier usage **MUST** be consistent within a document and across related documents.
- Conflicting statements **MUST NOT** be silently reconciled. The conflict **MUST** be documented with the affected locations and escalated to the Software Architect for a decision.
- Duplicated definitions **MUST** be reduced to a single authoritative definition with references.

### 2.4 Traceability

- Requirements and decisions **MUST** be linkable to their origin and to their dependent artifacts (see Section 6).
- Statements that cannot be traced to a source, requirement, decision, or explicit classification **SHOULD** be flagged as unsupported.

### 2.5 Appropriate level of detail

- Detail **MUST** be sufficient for the document's stated purpose and audience, and no more.
- Documents **MUST NOT** restate large blocks of another document. Reference the source instead.
- Design-level detail **MUST NOT** be introduced into planning documents, and implementation-level detail **MUST NOT** be introduced at all.
- Where detail is deferred, the deferral **MUST** be recorded as an `OPEN QUESTION` or a documented assumption, not left implicit.

### 2.6 Honesty about certainty

- Assumptions and recommendations **MUST NOT** be presented as confirmed facts.
- A document **MUST NOT** claim that validation, review, approval, or research occurred unless it did.
- Unresolved issues **MUST** remain visible rather than being absorbed into confident prose.

---

## 3. Document structure and formatting conventions

### 3.1 File format and naming

- Documents **MUST** be written in Markdown and stored as UTF-8 encoded `.md` files.
- Documents **SHOULD** use lowercase hyphenated file names that describe their content (for example, `scope-statement.md`).
- Documents **MUST** be placed in the designated directory for their lifecycle phase or asset class. Files **MUST NOT** be created in the root of `docs/` or `framework/`.
- `README.md` **SHOULD** be used only for index, purpose, or governance documents for a directory.

### 3.2 Required document metadata

Every document **MUST** begin with a meaningful H1 title heading, followed by a metadata block containing, at minimum:

| Field | Requirement | Notes |
| --- | --- | --- |
| Purpose | **MUST** | One to three sentences describing why the document exists and what decisions or work it supports. |
| Status | **MUST** | Explicit status value. See Section 9.2. |
| Version | **MUST** | Version identifier. See Section 9.1. |
| Last updated | **MUST** | ISO date (`YYYY-MM-DD`) of the last material change. |
| Owner role | **MUST** | The responsible role, not an individual's name unless the human user requires it. For generated documentation this is normally the Documentation Agent under Software Architect coordination. |
| Authority / approval | **SHOULD** | Who authorized the document and whether approval exists. Use `Not approved` when no approval has been granted; a document that is not approved **MUST** state that explicitly rather than omitting the field. |
| Related documents | **SHOULD** | Identifiers or paths of dependent and related documents. |

**Title.** The document title is the H1 heading at the start of the document. It is **not** repeated as a metadata row, and a metadata block therefore contains no `Title` field.

Metadata **MAY** be expressed as a table or a structured list, but the field names **MUST** be consistent across documents. A document **MAY** add fields that serve its own purpose, but a concept covered by the table above **MUST** use the field name given there.

### 3.3 Section structure

- Documents **SHOULD** present sections in this order: purpose and scope, content sections, assumptions, open questions, risks, decisions and approval status, references, change history.
- Numbered headings **SHOULD** be used in documents longer than one screen, to permit precise cross-references.
- Cross-references **SHOULD** cite document path plus section number or identifier (for example, `docs/02-requirements/srs.md` §4.2, or `FR-014`).
- Each section **MUST** serve a stated purpose; boilerplate sections that would remain empty **SHOULD** be omitted or marked `Not applicable` with a reason.

### 3.4 Tables, lists, and diagrams

- Tables **MUST** be used when they improve traceability or comparison, such as requirement registers, traceability matrices, decision logs, risk registers, and source lists.
- Tables **MUST** have a header row and **SHOULD** avoid empty cells; use `Not applicable` or `Unknown` explicitly. Unknown values **SHOULD** be linked to an `OPEN QUESTION`.
- Lists **MUST** contain parallel grammatical structures.
- Diagrams **SHOULD** be accompanied by a textual description that can be reviewed independently, and the text and diagram **MUST** agree. Diagrams **MUST** be reproducible from text in the repository; binary-only artifacts **SHOULD** be avoided.
- Where a diagram and its description conflict, the conflict **MUST** be recorded rather than silently corrected by assumption.

### 3.5 Code fences and literals

- Identifiers, field names, file paths, commands, and literal values **MUST** be marked as inline code.
- Multi-line examples and structured snippets **MUST** use fenced code blocks with a language hint where applicable.
- Content in code fences **MUST NOT** be construed as application source code or executable automation.

### 3.6 Terminology and acronyms

- Each document **MUST** define every acronym on first use, or reference a glossary that defines it.
- A glossary **SHOULD** exist when a project uses more than a small number of domain terms; it **MUST** have one authoritative location.
- The same concept **MUST** use the same term throughout. Synonyms **SHOULD** be listed as aliases rather than used interchangeably.
- Terms defined in repository instructions **MUST** keep their established meaning. In particular, `BR` means **Business Rule**, never "Business Requirement".

### 3.7 Language policy

The language used for documentation and communication in this system is governed by the following mandatory rules. Agents **MUST NOT** change, translate, or mix languages on their own initiative.

1. The conversation between the human user and the Software Architect **MUST** follow the language used by the user.
2. Project-specific documentation **MUST** be written in the language the user used when discussing that project.
3. Research Agent and Validation Agent reports for a project **MUST** use the same language as that project's documentation.
4. General repository and framework documentation — including standards, templates, instructions, and reusable workflows — **MUST** be maintained in English.
5. All delegated agents **MUST** respect this policy. They **MUST NOT** decide to change the language, translate existing documents, or mix languages on their own initiative.
6. Any exception to, or change of, this language policy **MUST** require explicit authorization from the human user.

Rule 6 takes precedence over the general deviation path in Section 1.4: for language matters, an exception or change requires explicit human-user authorization, not Software Architect authorization alone.

Independently of the language selected, documents **MUST** be written in professional, neutral, and technically precise language, and **MUST NOT** contain marketing language, unqualified superlatives, or promotional claims.

---

## 4. Information classification

### 4.1 Required classifications

When the certainty of a statement matters, it **MUST** be classified using exactly one of the following four labels.

| Label | Definition | Requires |
| --- | --- | --- |
| `CONFIRMED` | Explicitly supported by project information, an authoritative source, or an approved stakeholder decision. | A citable project source or reference, or a recorded approval, identified in the document. |
| `ASSUMPTION` | Provisionally accepted but not verified. | A stated basis, an owner or verification path, and visibility in the assumptions register or the document's assumptions section. |
| `RECOMMENDATION` | A proposed solution or professional judgment offered by an agent or author. | The reasoning, and an explicit statement that approval is pending where approval is required. |
| `OPEN QUESTION` | Information or a decision still required. | A description of what is missing and who must resolve it. |

**Note on the `CONFIRMED` definition.** `AGENTS.md` §4 defines `CONFIRMED` as *explicitly supported by project information or an authoritative source*. This standard adopts that definition and treats an approved stakeholder decision as a form of authoritative confirmation; the two formulations are aligned, and neither excludes a basis admitted by the other.

### 4.2 Classification rules

- Each classified statement **MUST** carry exactly one label. A statement **MUST NOT** be assigned more than one label; split compound statements instead.
- `CONFIRMED` **MUST NOT** be used for statements supported only by agent reasoning, convention, preference, or an unapproved draft.
- `RECOMMENDATION` **MUST NOT** be presented as a decision. A recommendation becomes a decision only through recorded approval.
- `ASSUMPTION` **MUST NOT** be silently promoted to `CONFIRMED`. Promotion requires evidence or approval, recorded at the point of promotion.
- `OPEN QUESTION` items **MUST** remain visible until resolved; resolution **MUST** be recorded with the resolving evidence or decision.
- Classification **MUST NOT** be omitted where miscalculation of certainty would affect scope, requirements, budget, security, technology, or architecture.
- Labels **SHOULD** be applied consistently at statement or item level, typically using a leading label, a dedicated column in a table, or a register entry.

### 4.3 Classification coverage

- Assumptions **SHOULD** be consolidated in an assumptions register or a dedicated document section, while remaining traceable to the statements they support.
- Open questions **SHOULD** be consolidated in an open-questions section or register with an owner and expected resolution point.
- Recommendations **SHOULD** be consolidated where multiple options are compared, with the approval status stated for each.
- Registers **MUST** use stable identifiers so that items can be referenced from other documents. Identifier schemes for registers **SHOULD** follow the pattern of Section 5 where a prefix is defined, and **MUST** be documented where a new scheme is introduced.

---

## 5. Requirement and artifact identifiers

### 5.1 Defined prefixes

The following six prefixes are defined by this standard and **MUST** be used with the meanings in the table.

| Prefix | Meaning | Example |
| --- | --- | --- |
| `FR` | Functional Requirement | `FR-001` |
| `NFR` | Non-Functional Requirement | `NFR-001` |
| `BR` | Business Rule | `BR-001` |
| `UC` | Use Case | `UC-001` |
| `INT` | Integration Requirement | `INT-001` |
| `SEC` | Security Requirement | `SEC-001` |

`BR` **MUST** be read and written as **Business Rule**. It **MUST NOT** be used to mean "Business Requirement".

**Use of `INT`.** The canonical expansion of `INT` is **Integration Requirement**, resolved by human decision (see `OQ-STD-001` in Section 14). This aligns with `AGENTS.md` §6. The Documentation Agent definition still uses the form *Integrations*; aligning that file requires human-controlled maintenance and is outside this standard's write scope.

### 5.2 Format

- Identifiers **MUST** use the pattern `PREFIX-NNN`, where `PREFIX` is one of the six prefixes above and `NNN` is a zero-padded sequential number of at least three digits.
- Identifiers **MUST** be unique within their prefix across the project, not merely within a document.
- Identifiers **SHOULD** remain within a single numbering sequence per prefix, even when items are distributed across multiple documents.
- An identifier **MUST NOT** be reused for a different item after the original has been withdrawn, superseded, or rejected.

### 5.3 Stability

- Identifiers **MUST** remain stable after assignment.
- Identifiers **MUST NOT** be renumbered without explicit approval from the Software Architect and a recorded rationale.
- Renumbering that is approved **MUST** be recorded in the affected documents' change history, and existing cross-references **MUST** be updated in the same change.
- Withdrawn or superseded items **MUST** be retained and marked with their disposition rather than deleted, so that references remain resolvable.

### 5.4 Assignment discipline

- Identifiers **MUST** be assigned when an item is first recorded in a document, register, or matrix.
- Gaps in numbering are permitted and **MUST NOT** be closed by renumbering.
- Where a numbering range or sequence is allocated across documents, the allocation **SHOULD** be recorded to prevent duplicate assignment.

### 5.5 Other artifact identifiers

This standard defines exactly the six prefixes above. Other identifier schemes used by repository assets or agent outputs — for example validation finding identifiers established by the Validation Agent definition, or architecture decision identifiers used by templates — are outside the scope of this section. Where such schemes are used, they **MUST** be documented in the asset that defines them and **MUST NOT** conflict with the six prefixes defined here.

---

## 6. Traceability

### 6.1 Required chain

Traceability **MUST** be maintained, where applicable, along the following chain:

**Business Rule → Requirement → User Story / Use Case → Architecture Decision → Acceptance Criteria → Future Test**

Each link means:

| Link | Meaning |
| --- | --- |
| Business Rule → Requirement | The requirement exists because of a stated business rule, or records that no rule applies. |
| Requirement → User Story / Use Case | The requirement is realized through at least one user story or use case. |
| User Story / Use Case → Architecture Decision | The design decision that satisfies or constrains the story or use case is identified. |
| Architecture Decision → Acceptance Criteria | The acceptance criteria that verify the requirement and its realization are identified. |
| Acceptance Criteria → Future Test | Each acceptance criterion identifies the future test or verification activity that will evaluate it. |

### 6.2 How to maintain traceability

- Traceability **SHOULD** be maintained in a requirements traceability matrix or an equivalent structured register that lists identifiers and their links in both directions.
- Links **MUST** be expressed using stable identifiers, not section titles or prose descriptions.
- When an item is added, changed, or withdrawn, affected links **MUST** be reviewed in the same change.
- Traceability **SHOULD** be verified before a phase gate is proposed for completion.
- Acceptance criteria **MUST** be expressed so that they can be evaluated; criteria that cannot be verified **MUST** be flagged.
- Future tests **MAY** be recorded at a planning level only. Their presence **MUST NOT** be represented as evidence that testing has occurred.

### 6.3 Exceptions

- Where a link does not apply, the exception **MUST** be recorded explicitly (for example, a non-functional requirement with no use case, or a technology constraint with no originating business rule) rather than left blank.
- A documented, reasoned exception is traceable. An empty cell is not.

### 6.4 Defects to flag

The following conditions **MUST** be identified and reported to the Software Architect rather than resolved silently:

| Condition | Description |
| --- | --- |
| Orphan requirement | A requirement with no originating business rule or other documented source. |
| Orphan business rule | A business rule with no related requirement. |
| Missing link | A break in the chain in Section 6.1 that is not a documented exception. |
| Missing acceptance criteria | A requirement without verifiable acceptance criteria. |
| Decision without requirement | An architecture decision with no supporting requirement or constraint. |
| Non-verifying criterion | Acceptance criteria that do not actually verify their associated requirement. |
| Conflicting reference | Two documents reference the same identifier with different or incompatible content. |
| Duplicate identifier | The same identifier assigned to different items. |
| Broken identifier | A reference to an identifier that does not exist or was changed without updating references. |

### 6.5 Reporting traceability defects

- Each defect **SHOULD** be recorded with the affected identifiers, documents, and sections.
- Defects **MUST** remain open until corrected and the correction is confirmed, or until a documented decision accepts the exception.
- A traceability defect **MUST NOT** be closed merely because a correction was proposed.

---

## 7. Sources, references, and evidence quality

### 7.1 Source preference

Where external evidence is used, sources **SHOULD** be prioritized as follows:

1. Official vendor or project documentation.
2. Official API references and technical specifications.
3. Official pricing, licensing, and security documentation.
4. Standards organizations and published specifications.
5. Official support announcements and release notes.
6. Reputable technical publications.
7. Community discussions, only as supplementary evidence.

Marketing material **MUST NOT** be treated as proof of technical capability.

### 7.2 Required source record

For every material external claim, the following **MUST** be recorded when available:

- Source title.
- Publisher or organization.
- URL.
- Publication or update date.
- Access date.
- Relevant version, edition, or product generation.
- The finding supported, and its limitations or uncertainties.

Where a field is genuinely unavailable, the document **MUST** say so rather than omit the field silently.

### 7.3 Evidence discipline

- A source **MUST NOT** be cited unless it was actually consulted or supplied by the Research Agent or the Software Architect.
- Sources, URLs, dates, and capabilities **MUST NOT** be invented or reconstructed from memory.
- Documented capability **MUST** be distinguished from assumption, inference, and vendor claim.
- Claims that could not be verified **MUST** be marked as unverified and classified `ASSUMPTION` or `OPEN QUESTION`.
- Version-specific claims **MUST** identify the version they apply to, and **SHOULD** note when applicability to other versions is unknown.
- Limitations, dependencies, and licensing conditions that affect a finding **MUST** be disclosed alongside it.
- Persisting a report **MUST NOT** be presented as independent verification of its content.

### 7.4 References section

- Documents **SHOULD** include a references section listing consulted sources.
- References **MUST** be identifiable and **SHOULD** be stable. Where a URL is unstable, the document **SHOULD** record a stable identifier such as a document title and version.
- Internal references **MUST** use repository-relative paths with section or identifier anchors.
- Original project material under `input/existing-documentation/` **MAY** be referenced but **MUST NOT** be modified, renamed, moved, or replaced.

---

## 8. Assumptions, open questions, risks, and decisions

### 8.1 Where each belongs

| Item | Primary location | Also required |
| --- | --- | --- |
| Assumption | Assumptions register (Phase 1) and the assumptions section of the affected document | Basis, impact if wrong, verification path, classification `ASSUMPTION` |
| Open question | Open-questions section or register | Owner or resolver, affected documents, expected resolution point |
| Risk | Risk register (Phase 1) | Likelihood, impact, mitigation or contingency, owner, status |
| Decision | Architecture Decision Record or the decision section of the governing document | Context, options considered, decision, rationale, approver, approval date, status |
| Recommendation | The document proposing it, or an options comparison | Reasoning, approval status, and explicit statement that it is not yet a decision |

### 8.2 Tracking rules

- Items **MUST** have stable identifiers within their register so they can be referenced from other documents.
- Items **MUST** carry a status such as open, accepted, rejected, superseded, or resolved, and the status **MUST** reflect reality.
- Items **MUST NOT** be deleted to tidy a document. Resolved or rejected items remain with their disposition recorded.
- Assumptions that are accepted without verification **MUST** record that acceptance and its authority.
- Open questions that block a phase gate **MUST** be identifiable as blocking; the Software Architect decides blocking status, not the author.

### 8.3 Decisions and rationale

- Decisions **MUST** record the problem, the alternatives considered, the trade-offs, the chosen option, the rationale, and the approval status.
- A decision **MUST** identify who approved it. Agent authorship is not approval.
- Decisions **MUST NOT** be rewritten to appear better-justified in hindsight. Corrections are recorded as amendments with dates and reasons.
- Superseded decisions **MUST** remain visible and reference their replacement.
- Where a decision conflicts with a previously approved decision, the conflict **MUST** be documented and escalated.

### 8.4 Prohibited conversions

- A `RECOMMENDATION` **MUST NOT** be silently converted into a decision, requirement, or `CONFIRMED` statement.
- An `ASSUMPTION` **MUST NOT** be silently converted into a requirement or fact.
- An `OPEN QUESTION` **MUST NOT** be silently closed by an author's preference.
- Promotion of any of the above **MUST** be recorded together with the authority or evidence that justified it.

### 8.5 Human approval

Human approval is required for significant decisions involving project scope, budget and costs, business priorities, functional requirements, security and privacy, technology selection, architecture decisions, and changes to previously approved deliverables. Agents may investigate and recommend; they **MUST NOT** treat a recommendation as approved. The Software Architect presents such decisions to the human user.

---

## 9. Versioning and document maintenance

### 9.1 Versioning

- Documents **MUST** carry a version identifier.
- Documents **MUST** use semantic-style version numbering `MAJOR.MINOR.PATCH`:
  - `MAJOR` — changes that alter approved content, scope, or meaning, or that supersede prior decisions.
  - `MINOR` — additive changes such as new sections, requirements, or sources.
  - `PATCH` — editorial corrections that do not change meaning.
- A document **MUST** record material changes in a change history section with version, date, summary, and reason.
- Version identifiers **MUST NOT** be reused or renumbered retroactively.

This mandatory requirement reflects resolved decision `OQ-STD-003` (Section 14).

### 9.2 Status

Every document **MUST** state a status. Documents **MUST** use the following vocabulary:

| Status | Meaning |
| --- | --- |
| `Draft` | Work in progress. Not reviewed for completeness. Not approved. |
| `In review` | Submitted for Software Architect review and, where applicable, independent validation. Not approved. |
| `Approved` | Reviewed and approved by the authorized human role. Approval date and approver recorded. |
| `Superseded` | Replaced by a named successor. Retained for traceability. |
| `Withdrawn` | No longer pursued. Retained with the reason recorded. |

- A status value **MUST NOT** imply an approval that did not occur.
- Document status and approval status **MUST** be distinguished. "Approved" requires recorded human approval; validation alone is not approval.
- A document with unresolved critical validation findings **MUST NOT** be marked `Approved`.

This mandatory requirement reflects resolved decision `OQ-STD-002` (Section 14).

### 9.3 Change control

- Before changing an existing document, the author **MUST** read the current version, identify the requested change and its reason, and confirm that the change is within authorized write scope.
- Changes **MUST NOT** overwrite, weaken, or obscure previously approved decisions, requirements, or validation findings without explicit direction from the Software Architect.
- Approved content that is no longer valid **MUST** be superseded with a recorded reason, not silently replaced.
- Material changes **MUST** be reported to the Software Architect.
- Unrelated rewriting **SHOULD** be avoided; changes **SHOULD** be traceable to their reason.
- Deletion of project documentation or framework assets **MUST NOT** occur. Obsolete content is marked `Superseded` or `Withdrawn` and its replacement identified.

### 9.4 Accuracy of state

- Documentation **MUST** describe the state that actually exists.
- Planned, proposed, or recommended features **MUST NOT** be documented as implemented, decided, or approved.
- Where a document describes intended future work, it **MUST** label that content as planned or proposed and classify it accordingly.
- Where repository instructions change, affected documents **SHOULD** be updated in the same repository change, at the direction of the Software Architect.

### 9.5 Protected material

- Original material under `input/existing-documentation/` **MUST** remain unchanged. It **MUST NOT** be edited, renamed, deleted, or replaced.
- Repository configuration, instructions, and agent definitions (`README.md`, `AGENTS.md`, `opencode.json`, `.opencode/`, `.gitignore`) **MUST NOT** be modified during documentation work. Conflicts or required changes are reported to the Software Architect for human-controlled maintenance.

### 9.6 Documentation impact review

Whenever a significant change occurs to the project's sources, requirements, decisions, scope, architecture, or documentation, every agent that produces, researches, reviews, or updates documentation **MUST** perform a documentation impact review. The review:

1. Identifies the documents that mention the changed file, requirement, decision, or element.
2. Locates statements that have become obsolete, contradictions, and references to information that is now available.
3. Updates the affected sections or explicitly states what remains pending.
4. Verifies coherence between related documents.
5. Checks that references to sources, versions, statuses, and decisions reflect the current state.
6. Records the relevant changes in the project's decision log.

The term *significant* in this section means a change material enough to affect the project's documentation. It is **not** the `Significant change` class defined in [`framework/workflows/change-control.md`](../workflows/change-control.md) §11.2, and the review is **not** limited to changes of that class: it applies generally to every change that is processed, including documentary corrections, while those change classes govern only the approval level a change requires.

It **MUST NOT** be assumed that adding or modifying a file affects only the document being worked on; the review considers the project's documentation as a whole.

This rule applies to all agents that produce, research, review, or update documentation, not only the Documentation Agent.

The review operates together with the change-control discipline of Section 9.3 and the accuracy-of-state requirement of Section 9.4: it is a precondition for describing a change as complete, and its outcome **MUST** be recorded rather than implied. Agents that do not hold write authority over the affected documents — as determined by the repository instructions and their own agent definitions — **MUST** report the outcome of the review, including anything that remains pending, to the Software Architect instead of editing the documents themselves. The procedural application of this rule is defined in [`framework/workflows/change-control.md`](../workflows/change-control.md) (WF-009).

---

## 10. Minimum quality criteria for a complete document

A document may be considered complete only when **all** applicable criteria below are satisfied. Criteria that are not applicable **MUST** be marked `Not applicable` with a reason.

### 10.1 Structural criteria

- [ ] The document is Markdown, UTF-8, and located in the designated directory for its phase or asset class.
- [ ] The document has a meaningful title and a stated purpose and audience.
- [ ] Metadata includes status, version, last-updated date, and owner role.
- [ ] Sections are logically ordered, numbered where useful, and free of empty boilerplate.
- [ ] Related documents and dependencies are identified.

### 10.2 Content criteria

- [ ] Scope is stated, including what the document deliberately does not cover.
- [ ] Statements whose certainty matters are classified using `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`.
- [ ] No assumption or recommendation is presented as a confirmed fact or an approved decision.
- [ ] Terminology is consistent, and acronyms are defined on first use or in a glossary.
- [ ] Vague or unmeasurable statements are qualified or flagged.
- [ ] Conflicts between sources or documents are documented rather than silently resolved.
- [ ] Content remains within planning, requirements, and design scope; no application implementation or executable components are introduced.

### 10.3 Identification and traceability criteria

- [ ] All requirements use the defined prefixes and the `PREFIX-NNN` format.
- [ ] Identifiers are unique, and no identifier has been renumbered or reused without recorded approval.
- [ ] Traceability links exist along the applicable chain, or documented exceptions are recorded.
- [ ] Orphans, missing links, duplicate identifiers, broken identifiers, and conflicting references have been identified and reported.
- [ ] Acceptance criteria are verifiable, and future tests are identified without implying that testing occurred.

### 10.4 Evidence criteria

- [ ] Every material external claim has a recorded source with the fields in Section 7.2 where available.
- [ ] No source is cited that was not consulted or supplied.
- [ ] Documented capability is distinguished from assumption, inference, and vendor claim.
- [ ] Unverified claims are marked and classified.
- [ ] Limitations, dependencies, and version applicability are disclosed.
- [ ] Recommendations are not represented as approved decisions.

### 10.5 Governance criteria

- [ ] Assumptions, open questions, and risks are recorded with owners and status.
- [ ] Decisions record context, alternatives, rationale, approver, and approval status.
- [ ] Approval status is accurate; no approval, validation, or review is claimed that did not occur.
- [ ] Independent validation has been performed where required, and findings are resolved or explicitly tracked with status.
- [ ] Material changes are recorded in the change history.
- [ ] The document does not modify or misrepresent original project material or repository configuration.
- [ ] The document is subject to the Software Architect's phase-gate decision; completeness of the document does not itself complete a phase.

### 10.6 Completion statement

A document that satisfies these criteria is ready to be submitted for the Software Architect's review and, where applicable, independent validation. Meeting these criteria is not an approval, and the author **MUST NOT** describe such a document as approved, validated, or final.

---

## 11. Relationship to other framework assets and repository instructions

- **Templates** (`framework/templates/`) **SHOULD** implement this standard's structure and metadata requirements. A template that conflicts with this standard **MUST** be reported to the Software Architect.
- **Workflows** (`framework/workflows/`) describe repeatable agent procedures. They **MAY** reference this standard and **MUST NOT** restate its rules in contradictory form.
- **Repository instructions** (`AGENTS.md`, `README.md`, `opencode.json`, agent definitions) take precedence. Where this standard conflicts with them, the repository instructions prevail until the human user authorizes a controlled change.
- This standard defines conventions for documentation. It does **not** grant write permissions, approve work, or authorize any activity outside the three supported lifecycle phases.
- This standard is a reusable, project-agnostic asset. It **MUST NOT** accumulate project-specific content. Project-specific conventions are recorded (with justification) in the affected project documents, not here.

---

## 12. References

### 12.1 Internal references

| Reference | Purpose |
| --- | --- |
| `AGENTS.md` | Repository-wide agent instructions, restrictions, classification, identifiers, validation, phase completion, and framework governance. |
| `README.md` | Repository overview, agent architecture, permission model, and governance. |
| `.opencode/agents/software-architect.md` | Coordination, decision management, documentation governance, and phase gates. |
| `.opencode/agents/documentation-agent.md` | Documentation Agent mission, write boundaries, standards duties, and change control. |
| `.opencode/agents/research-agent.md` | Research evidence requirements and source quality expectations. |
| `.opencode/agents/validation-agent.md` | Independent review dimensions, finding severity, and report structure. |
| `framework/standards/README.md` | Standards index and governance lifecycle. |

No external sources were consulted in preparing this standard. Statements about repository conventions are derived from the repository instructions listed above.

---

## 13. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-09 | Initial draft of the foundational documentation standard, created under Software Architect authorization for `framework/standards/README.md` and `framework/standards/documentation-standards.md`. Includes an `INT` terminology note and framework-level open questions. | Establish reusable documentation conventions for the three supported lifecycle phases. | Documentation Agent | Draft — not independently validated and not approved. |
| 0.2.0 | 2026-11-09 | Corrections applied under Software Architect authorization following independent review findings VAL-001 to VAL-005: the `INT` meaning is marked provisional (VAL-001); metadata field names are harmonized and the title rule clarified (VAL-002); the `CONFIRMED` definition is aligned with `AGENTS.md` §4 (VAL-003); scope now states self-application to the framework standards (VAL-004). No finding is claimed as resolved until the corrections are reviewed. | Resolve the LOW- and INFORMATIONAL-severity review findings without changing repository instructions or agent definitions. | Documentation Agent | Draft — corrections applied; not re-validated and not approved at time of authoring; subsequently passed independent validation (second review, 2026-11-09); not approved. |
| 0.3.0 | 2026-11-09 | `INT` resolved to "Integration Requirement" (`OQ-STD-001`); status vocabulary made mandatory (`OQ-STD-002`); semantic-style version numbering made mandatory (`OQ-STD-003`); language policy added (§3.7); VAL-006 wording simplified (§5.1). | Apply human decisions on the framework-level open questions, adopt the language policy, and simplify the dense §5.1 lead-in. | Documentation Agent | In review — changes applied; pending independent validation; not approved. |
| 0.3.1 | 2026-11-09 | Corrections applied following the independent review of v0.3.0: §14 column relabeled from `Classification` to `Status` with values `Resolved` (VAL-001); the v0.2.0 change-history note reconciled with the v0.2.0 validation PASS (VAL-002); the precedence of the §3.7 language policy over the §1.4 deviation path clarified (VAL-003); versioning terminology standardized to "semantic-style version numbering" (VAL-004). | Address editorial and consistency findings from the v0.3.0 independent review without changing the standard's meaning. | Documentation Agent | Approved by Human user on 2026-11-09 (following independent validation PASS). |
| 0.4.0 | 2026-11-10 | Adds §9.6 *Documentation impact review*: a significant change to sources, requirements, decisions, scope, architecture, or documentation requires every agent that produces, researches, reviews, or updates documentation to review the project's documentation as a whole for affected mentions, obsolete statements, contradictions, newly available information, stale references, and decision-log updates. No existing section was renumbered, rewritten, or removed. | Incorporate a permanent framework rule approved by the Human user on 2026-11-10, under Software Architect authorization, so that a change is not treated as affecting only the document being edited. | Documentation Agent | In review — additive change applied; pending independent validation; not approved. |
| 0.4.1 | 2026-11-10 | §9.6 terminology clarified (VAL-002): a sentence states that *significant* in that section means a change material enough to affect the documentation, that it is not the `Significant change` class defined in `framework/workflows/change-control.md` §11.2, and that the review applies generally to every processed change, including documentary corrections, while the change classes govern only the approval level. The six review points and the section's position are unchanged; no other section was modified. | Remove the ambiguity between the §9.6 trigger and the three-class scheme of the change-control workflow, without altering the rule's content. | Documentation Agent | In review — clarification applied under Human approval of 2026-11-10 and Software Architect authorization of 2026-11-10; pending independent validation; not approved. |

---

## 14. Resolved decisions (formerly open questions)

The items below were recorded as framework-level open questions in earlier versions. Each is now closed by explicit human decision and is retained with its original identifier for traceability.

| ID | Status | Resolved decision | Deciding authority | Date | Applied in |
| --- | --- | --- | --- | --- | --- |
| `OQ-STD-001` | `Resolved` | The canonical expansion of `INT` is **Integration Requirement**. | Human user | 2026-11-09 | Section 5.1 |
| `OQ-STD-002` | `Resolved` | The document-status vocabulary (`Draft`, `In review`, `Approved`, `Superseded`, `Withdrawn`) is **mandatory**. | Human user | 2026-11-09 | Section 9.2 |
| `OQ-STD-003` | `Resolved` | Semantic-style version numbering `MAJOR.MINOR.PATCH` is **mandatory**. | Human user | 2026-11-09 | Section 9.1 |

These decisions are resolved and are retained here for traceability, not as open items. Resolving these decisions is distinct from approving the standard; version 0.3.1 was approved by the Human user on 2026-11-09, and the status of the current version is recorded in the document metadata.

