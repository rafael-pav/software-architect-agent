# Project Charter (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Project Charter used in Phase 1 (Planning and Scope) to record the project's purpose, boundaries, stakeholders, success criteria, budget placeholders, milestones, and approval status. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Project charters stored under `docs/01-planning/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`scope-statement.md`](./scope-statement.md); [`feasibility-study.md`](./feasibility-study.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/01-planning/`. Do not keep this "How to use" block in the project document.
2. Replace every `{{ ... }}` placeholder. A placeholder that cannot be filled must become an `OPEN QUESTION`, not an invented value.
3. Remove every italic guidance note and every HTML comment once the section is complete. If a section genuinely does not apply, keep the heading and write `Not applicable — {{reason}}`.
4. Assign identifiers before content expands: define the identifier schemes you use here, keep them stable, and never reuse a withdrawn identifier.
5. Classify every statement whose certainty matters as `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`. A `CONFIRMED` value requires a citable project source or a recorded approval.
6. Do not present a budget, date, scope boundary, or stakeholder commitment as confirmed unless it has been approved by the authorized human role.
7. Complete the metadata block and change history. Drafting a charter does not approve the project, its budget, or its scope, and does not complete Phase 1.

**Identifier scope.** Non-standard prefixes used in this template (`OBJ`, `SC`, `MS`, `ASM`, `OQ`, `RISK`, `DEC`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Project Charter

| Field | Value |
| --- | --- |
| Purpose | {{One to three sentences: why this charter exists and which decisions it supports.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role, normally the Documentation Agent under Software Architect coordination.}} |
| Authority / approval | {{Who authorized this charter; use `Not approved` if no approval has been granted, with the pending approver named.}} |
| Related documents | {{Paths or identifiers of related documents, for example the scope statement, feasibility study, and assumptions register.}} |

## 1. Purpose and objectives

### 1.1 Purpose

{{Why the project is being undertaken, stated in one to three sentences.}}

*Guidance: if the purpose is still contested, state it as `OPEN QUESTION` and name who must resolve it.*

### 1.2 Objectives

| ID | Objective | Measure of achievement | Target | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| `OBJ-001` | {{Objective statement}} | {{How achievement is observed and measured}} | {{Target value, date, or condition}} | {{CONFIRMED / ASSUMPTION / RECOMMENDATION / OPEN QUESTION}} | {{Source reference or approval}} |

*Guidance: objectives must be verifiable. A target of `{{TBD}}` must be paired with an `OPEN QUESTION`. Identifier scheme used here: `OBJ-NNN`.*

## 2. Background and context

{{Relevant history, the problem being addressed, and the constraints that shape the project.}}

| Aspect | Statement | Classification | Source |
| --- | --- | --- | --- |
| {{Problem or opportunity}} | {{Statement}} | {{Label}} | {{Source}} |

*Guidance: reference original project material under `input/existing-documentation/` rather than restating it. Record contradictions between sources in §9 (as open questions) or §10 (as risks) instead of resolving them by assumption.*

## 3. Scope summary

### 3.1 In scope

- {{Included capability, deliverable, or activity}}
- {{...}}

### 3.2 Out of scope

| Excluded item | Reason for exclusion | Classification | Source |
| --- | --- | --- | --- |
| {{Item}} | {{Reason}} | {{Label}} | {{Source}} |

*Guidance: the authoritative scope boundaries belong in the scope statement. If this charter and the scope statement disagree, record the conflict for the Software Architect rather than aligning them silently.*

## 4. Stakeholders

| Stakeholder or role | Interest in the project | Influence | Decision authority | Approval required from this stakeholder | Classification | Source |
| --- | --- | --- | --- | --- | --- | --- |
| {{Role or organizational unit}} | {{Interest}} | {{High / Medium / Low with basis}} | {{Decisions this stakeholder owns}} | {{Yes — which decisions / No}} | {{Label}} | {{Source}} |

*Guidance: record roles and organizational units, not personal names, unless the human user requires names. An assumed stakeholder must remain `ASSUMPTION` until confirmed.*

## 5. Success criteria

| ID | Success criterion | Measure and threshold | Verification method | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| `SC-001` | {{Criterion}} | {{Measure, threshold, and conditions}} | {{How it will be demonstrated}} | {{Label}} | {{Source}} |

*Guidance: identifier scheme used here: `SC-NNN`. Criteria must be evaluable; unverifiable criteria are defects and must be flagged.*

## 6. Budget

| Cost category | Basis of estimate | Amount | Currency | Confidence | Classification | Source |
| --- | --- | --- | --- | --- | --- | --- |
| {{Category}} | {{Assumption, quotation, or method behind the figure}} | {{Amount or TBD}} | {{Currency}} | {{High / Medium / Low with basis}} | {{Label}} | {{Source}} |

**Total:** `{{Amount}}` `{{Currency}}` — **Classification:** `{{Label}}`

*Guidance: never state a cost as `CONFIRMED` without an approved quotation or decision. Budget approval is a human decision presented by the Software Architect; drafting this charter does not approve any amount.*

## 7. Milestones and roadmap

| ID | Milestone | Target date | Predecessor or dependency | Exit criteria | Status | Classification |
| --- | --- | --- | --- | --- | --- | --- |
| `MS-001` | {{Milestone}} | {{YYYY-MM-DD or TBD}} | {{Dependency or None}} | {{What must be true to close it}} | {{Planned / In progress / At risk / Achieved}} | {{Label}} |

*Guidance: identifier scheme used here: `MS-NNN`. Dates that are targets rather than commitments must be stated as such. Document dates are not evidence of commitment.*

## 8. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption statement}} | {{Why it is currently accepted}} | {{Consequence}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. Each assumption is classified `ASSUMPTION` unless and until verification is recorded.*

## 9. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected decisions or documents}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. The author does not decide whether an item is blocking; the Software Architect does. Resolved items remain in the table with their disposition.*

## 10. High-level risks

| ID | Risk | Likelihood | Impact | Mitigation or contingency | Owner | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `RISK-001` | {{Risk statement: cause, event, consequence}} | {{High / Medium / Low with basis}} | {{High / Medium / Low with basis}} | {{Response}} | {{Role}} | {{Open / Mitigated / Accepted / Closed}} |

*Guidance: identifier scheme used here: `RISK-NNN`. The detailed risk register may live in a separate document; if it does, reference it instead of duplicating entries.*

## 11. Decisions and approval status

| ID | Decision | Approving role | Approval date | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| `DEC-001` | {{Decision required or granted}} | {{Human role with authority}} | {{YYYY-MM-DD or Pending}} | {{Proposed / Approved / Rejected / Superseded}} | {{Recorded approval reference}} |

**Statement of approval status.** {{State plainly what has and has not been approved. Example shape: "No element of this charter has been approved. Scope, budget, and schedule are classified `RECOMMENDATION` pending human approval." Do not omit this statement.}}

*Guidance: identifier scheme used here: `DEC-NNN`. Charter approval does not by itself complete Phase 1; that is a separate Software Architect phase-gate decision with the required human approvals recorded.*

## 12. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or source}} | {{What it supports in this charter}} | {{Repository-relative path, section anchor, or URL with access date}} |

*Guidance: cite only sources that were actually consulted or supplied. Use the source-record fields in the documentation standard for external claims.*

## 13. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
