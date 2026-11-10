# Use Case (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for documenting a single use case (`UC-NNN`) in Phase 2 (Requirements Analysis), covering actors, flows, exceptions, postconditions, related requirements, and acceptance criteria. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Use case documents stored under `docs/02-requirements/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`software-requirements-specification.md`](./software-requirements-specification.md); [`requirements-traceability-matrix.md`](./requirements-traceability-matrix.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/02-requirements/`. Use one file per use case, or one file containing several use cases if the project prefers; keep the identifier unique either way.
2. Assign the `UC-NNN` identifier once and never reuse it.
3. Replace every `{{ ... }}` placeholder and remove all italic guidance notes and HTML comments.
4. Describe behaviour, not implementation. A use case must not prescribe internal design or introduce application code.
5. Sequence steps so that each step names the actor or component responsible. Steps without an owner are defects.
6. Classify anything not established by a requirement or an approved decision; do not present a designed flow as confirmed behaviour.
7. Link the use case into the traceability matrix: originating business rule, requirement(s), architecture decision(s), acceptance criteria, and future test(s).

**Identifier scope.** Non-standard prefixes used in this template (`ADR`, `AC`, `TST`, `ASM`, `OQ`, `DEC`), together with the flow identifiers `UC-NNN-AF-NN` and `UC-NNN-EX-NN`, are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# `{{UC-001}}` — {{Use case name}}

| Field | Value |
| --- | --- |
| Purpose | {{Why this use case is documented and which requirements it realizes.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role}} |
| Authority / approval | {{Who authorized this document; `Not approved` if the behaviour has not been approved.}} |
| Related documents | {{Requirements specification, traceability matrix, related use cases, architecture decision records.}} |

## 1. Purpose and scope

{{The goal the primary actor pursues, and the boundary of this use case.}}

*Guidance: state explicitly what the use case does not cover, so that adjacent use cases are not silently duplicated.*

## 2. Identification

| Field | Value |
| --- | --- |
| Use case ID | `{{UC-001}}` |
| Use case name | {{Short verb-based name}} |
| Goal | {{Outcome the primary actor wants}} |
| Scope | {{System or subsystem boundary the use case applies to}} |
| Level | {{Summary / User goal / Sub-function, per the scheme defined by the project}} |
| Primary actor | {{Actor who initiates the use case to achieve the goal}} |
| Supporting actors | {{Actors or external systems that assist, or None}} |
| Related requirements | {{FR-00N, SEC-00N, INT-00N}} |
| Originating business rules | {{BR-00N or No originating business rule — reason}} |
| Classification of goal and scope | {{CONFIRMED / ASSUMPTION / RECOMMENDATION / OPEN QUESTION}} |

*Guidance: "level" and "supporting actor" definitions must come from the project's own terminology or a referenced source; do not invent a scheme.*

## 3. Stakeholders and interests

| Stakeholder | Interest in this use case | Protection or expectation |
| --- | --- | --- |
| {{Stakeholder or role}} | {{What they need from the outcome}} | {{What must be preserved for them, for example data integrity or auditability}} |

*Guidance: omit this section only if the interests are fully covered by the requirements register; do not leave an empty table.*

## 4. Preconditions

- {{State that must hold before the use case starts, and who or what guarantees it}}
- {{None if no precondition applies — state it rather than leaving the section empty}}

*Guidance: a precondition is a state, not an action. If it depends on an unconfirmed capability, classify it.*

## 5. Trigger

{{The event that starts the use case, attributed to its source.}}

## 6. Main flow

| Step | Responsible actor or component | Action | Data or state affected |
| --- | --- | --- | --- |
| 1 | {{Primary actor}} | {{Action}} | {{Data or state}} |
| 2 | {{System or component}} | {{Response or action}} | {{Data or state}} |

*Guidance: keep the main flow at the level of observable interaction. Reference `FR-NNN` where a step implements a specific requirement. Alternative step numbering, if used, must be consistent throughout.*

## 7. Alternate flows

### 7.1 `{{UC-001-AF-01}}` — {{Alternate flow name}}

- **Branches from:** main flow step {{n}}
- **Condition:** {{Condition that selects this flow}}
- **Steps:**

| Step | Responsible actor or component | Action |
| --- | --- | --- |
| {{1a}} | {{Actor or component}} | {{Action}} |

- **Rejoins at:** {{main flow step or ends the use case}}
- **Classification:** {{Label}}

*Guidance: flow identifiers follow the pattern `UC-NNN-AF-NN`, documented here because flow identifiers are outside the standard's defined prefixes. Delete this subsection if no alternate flows exist, replacing it with `Not applicable — {{reason}}`.*

## 8. Exceptions

### 8.1 `{{UC-001-EX-01}}` — {{Exception name}}

- **Triggered by:** {{Condition or failure}}
- **Detected by:** {{Actor or component}}
- **Handling:** {{What the system or actor does}}
- **Resulting state:** {{State after handling}}
- **Related requirement:** {{FR-00N or None — flagged}}

*Guidance: exception identifiers follow `UC-NNN-EX-NN`. Where handling is undecided, record it as an `OPEN QUESTION` plus the affected step.*

## 9. Postconditions

| Outcome | Postcondition | How it is verified |
| --- | --- | --- |
| Success | {{State that holds when the goal is achieved}} | {{Acceptance criterion or observation}} |
| Failure | {{State that holds when the goal is not achieved, including partial-completion state}} | {{Acceptance criterion or observation}} |

## 10. Related requirements, decisions, and traceability

| Business rule | Requirement | Architecture decision | Acceptance criteria | Future test | Link note |
| --- | --- | --- | --- | --- | --- |
| {{BR-00N}} | {{FR-00N}} | {{ADR-00N}} | {{AC-00N}} | {{TST-00N}} | {{Documented exception or Complete}} |

*Guidance: mirror these links in the requirements traceability matrix; the matrix remains authoritative. Missing links are defects, not empty cells.*

## 11. Acceptance criteria

| ID | Criterion | Verifies | Verification method | Classification |
| --- | --- | --- | --- | --- |
| `AC-001` | {{Evaluable criterion}} | {{FR-00N or UC-001}} | {{Demonstration, inspection, or measurement}} | {{Label}} |

*Guidance: criteria must be evaluable. A criterion that cannot fail is not a criterion.*

## 12. Classification of content

| Content area | Classification | Basis |
| --- | --- | --- |
| Goal and scope | {{Label}} | {{Requirement or decision reference}} |
| Main flow | {{Label}} | {{Basis}} |
| Alternate flows and exceptions | {{Label}} | {{Basis}} |
| Data described | {{Label}} | {{Basis}} |

*Guidance: mark any flow step that reflects a design proposal rather than confirmed behaviour. Proposal-derived behaviour is `RECOMMENDATION` until decided.*

## 13. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Affected steps or requirements}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`.*

## 14. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected steps, actors, or requirements}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`.*

## 15. Decisions and approval status

| ID | Decision | Approving role | Approval date | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| `DEC-001` | {{Decision affecting this use case}} | {{Human role}} | {{YYYY-MM-DD or Pending}} | {{Proposed / Approved / Rejected / Superseded}} | {{Recorded approval reference}} |

**Statement of approval status.** {{State whether this use case has been reviewed and approved, and by whom.}}

## 16. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or source}} | {{What it supports}} | {{Repository-relative path, section anchor, or URL with access date}} |

## 17. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
