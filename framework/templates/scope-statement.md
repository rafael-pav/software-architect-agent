# Scope Statement (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Scope Statement used in Phase 1 (Planning and Scope) to define in-scope and out-of-scope boundaries, deliverables, constraints, dependencies, and scope-level acceptance criteria. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Scope statements stored under `docs/01-planning/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`project-charter.md`](./project-charter.md); [`software-requirements-specification.md`](./software-requirements-specification.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/01-planning/`.
2. Replace every `{{ ... }}` placeholder; convert anything you cannot establish into an `OPEN QUESTION`.
3. Remove all italic guidance notes and HTML comments before review.
4. Keep out-of-scope items explicit. An item that is merely absent is not the same as an item that has been excluded by decision.
5. Classify each boundary, deliverable, constraint, and dependency as `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`.
6. A scope statement records boundaries; it does not approve them. Scope approval is a human decision presented by the Software Architect.

**Identifier scope.** Non-standard prefixes used in this template (`DLV`, `CON`, `DEP`, `AC`, `TST`, `ASM`, `OQ`, `DEC`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Scope Statement

| Field | Value |
| --- | --- |
| Purpose | {{Why this scope statement exists and which decisions it supports.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role}} |
| Authority / approval | {{Who authorized this document; `Not approved` if no approval exists.}} |
| Related documents | {{Charter, requirements specification, and other dependent documents.}} |

## 1. Purpose and scope of this document

{{What this document defines, and what it deliberately does not cover.}}

*Guidance: state which lifecycle phase this document supports and name the authoritative source for each scope decision.*

## 2. Scope boundaries

### 2.1 In scope

- {{Included capability, process, data, user group, or deliverable}}
- {{...}}

*Guidance: phrase each item as a boundary that can be tested. Avoid aggregate statements such as "all reporting features" without a defined enumeration.*

### 2.2 Out of scope

| Excluded item | Reason for exclusion | Decided by | Classification | Source |
| --- | --- | --- | --- | --- |
| {{Item}} | {{Reason}} | {{Approving role or Not decided}} | {{Label}} | {{Source}} |

*Guidance: an exclusion without a recorded decision remains `ASSUMPTION` or `OPEN QUESTION`. Do not present a proposed exclusion as agreed.*

### 2.3 Scope change control

{{How a scope change is requested, who evaluates it, and who approves it.}}

*Guidance: describe the process only as far as it is known. If it is undefined, record it as an `OPEN QUESTION` with the owner who must define it.*

## 3. Deliverables

| ID | Deliverable | Description | Acceptance basis | Responsible role | Status | Classification |
| --- | --- | --- | --- | --- | --- | --- |
| `DLV-001` | {{Deliverable}} | {{What it contains, at the level needed to judge completion}} | {{Criterion or reference to §6}} | {{Role}} | {{Planned / In progress / Delivered}} | {{Label}} |

*Guidance: identifier scheme used here: `DLV-NNN`. Do not claim a deliverable exists unless it has been produced and reviewed.*

## 4. Constraints

| ID | Constraint | Type | Description and source | Impact on scope | Classification |
| --- | --- | --- | --- | --- | --- |
| `CON-001` | {{Constraint}} | {{Technical / Organizational / Regulatory / Budget / Schedule / Contractual}} | {{Statement and its origin}} | {{What it restricts}} | {{Label}} |

*Guidance: identifier scheme used here: `CON-NNN`. A constraint asserted without a source is an assumption, not a constraint.*

## 5. Dependencies

| ID | Dependency | Depends on | Needed by | Owner | Consequence if unavailable | Classification |
| --- | --- | --- | --- | --- | --- | --- |
| `DEP-001` | {{Dependency}} | {{Internal team, external party, system, or decision}} | {{Date or milestone}} | {{Role}} | {{Impact on scope or schedule}} | {{Label}} |

*Guidance: identifier scheme used here: `DEP-NNN`. External dependencies that are not yet committed must be classified accordingly.*

## 6. Acceptance criteria

| ID | Acceptance criterion | Verifies | Verification method | Related requirement | Classification |
| --- | --- | --- | --- | --- | --- |
| `AC-001` | {{Criterion, stated so it can be evaluated}} | {{DLV-00N, objective, or scope boundary}} | {{Demonstration, inspection, measurement, or future test reference}} | {{FR-00N or Not applicable — reason}} | {{Label}} |

*Guidance: identifier scheme used here: `AC-NNN`; future tests use `TST-NNN`. A criterion that cannot be evaluated is a defect and must be recorded in §9 rather than left in this table.*

## 7. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Consequence for scope}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`.*

## 8. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected scope boundaries or deliverables}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. Blocking status is the Software Architect's decision, not the author's.*

## 9. Conflicts and unresolved issues

| Item | Conflicting sources or statements | Affected sections | Effect on scope | Escalated to | Status |
| --- | --- | --- | --- | --- | --- |
| {{Item}} | {{Source A versus source B, with locations}} | {{Sections or identifiers}} | {{Effect}} | {{Software Architect}} | {{Open / Decided — with decision reference}} |

*Guidance: record contradictions rather than reconciling them silently. Delete this section only if `Not applicable — no conflicts identified` is accurate and stated.*

## 10. Decisions and approval status

| ID | Decision | Approving role | Approval date | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| `DEC-001` | {{Decision, for example approval of §2 boundaries}} | {{Human role}} | {{YYYY-MM-DD or Pending}} | {{Proposed / Approved / Rejected / Superseded}} | {{Recorded approval reference}} |

**Statement of approval status.** {{State explicitly which boundaries are approved and which remain proposals.}}

## 11. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or source}} | {{What it supports}} | {{Repository-relative path, section anchor, or URL with access date}} |

## 12. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
