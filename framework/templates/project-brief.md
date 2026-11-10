# Project Brief (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Project Brief produced during project intake under `WF-001`, consolidating the intake state, problem statement, objectives, users and stakeholders, preliminary scope, constraints, integrations, risks, assumptions, and open questions into a single classified record that the human user approves before Phase 1 begins. |
| Status | Approved |
| Version | 0.1.0 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Project Briefs produced during `WF-001` intake and stored under `docs/00-project-management/` unless the Software Architect's authorization names another path. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`project-charter.md`](./project-charter.md); [`scope-statement.md`](./scope-statement.md); [`project-documentation-audit-and-manifest.md`](./project-documentation-audit-and-manifest.md); [`project-initiation.md`](../workflows/project-initiation.md); [`planning-and-scope.md`](../workflows/planning-and-scope.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the Project Brief template, under explicit Software Architect authorization for the consolidated framework-expansion pass. | Consolidate the result of project intake into one classified, approvable record that precedes Phase 1. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. A Project Brief is produced during `WF-001` intake, after the intake state has been classified and the documentation audit has been recorded. The Software Architect conducts the interview and decides what the brief states; the Documentation Agent drafts it only when the Software Architect authorizes that drafting.
2. Copy everything from the *Project document skeleton* marker into the target file. Do not keep this "How to use" block in the project document.
3. Replace every `{{ ... }}` placeholder. A placeholder that cannot be filled must become an `OPEN QUESTION` in §11, not an invented value.
4. Remove every italic guidance note and HTML comment once the section is complete. If a section genuinely does not apply, keep the heading and write `Not applicable — {{reason}}`.
5. Record exactly one intake state in §1. The intake state determines the questioning path and the audit depth, so an unconfirmed selection is an `ASSUMPTION` until the human user confirms it.
6. Record the origin of every statement. Information supplied verbally, by pasted text, or by reference to a document that was not delivered is a source record with a speaker, a date, and a channel (§2). Do not record a statement without an attributable source.
7. Classify every statement whose certainty matters as `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`. A recorded user statement confirms what the user said; it does not by itself confirm what an existing system does.
8. **The Project Brief requires human approval before Planning and Scope (`WF-002`) begins.** Drafting the brief is not approval of the brief, the project, its scope, its budget, or its priorities. Record the approval, the approver, and the date in §12.
9. Keep the brief short. It is an intake record, not a charter: authoritative scope boundaries belong in the scope statement, and detailed feasibility analysis belongs in the feasibility study.

**Identifier scope.** Non-standard prefixes used in this template (`OBJ`, `CON`, `RISK`, `ASM`, `OQ`, `DEC`, `SRC`) are register identifiers, not requirement prefixes defined by the documentation standard. Several are cross-referenced schemes rather than schemes local to this template: `OBJ-NNN` is defined in [`project-charter.md`](./project-charter.md) §1.2, `RISK-NNN` in [`project-charter.md`](./project-charter.md) §10, `ASM-NNN` in [`project-charter.md`](./project-charter.md) §8, `OQ-NNN` in [`project-charter.md`](./project-charter.md) §9, `DEC-NNN` in [`project-charter.md`](./project-charter.md) §11, `CON-NNN` in [`scope-statement.md`](./scope-statement.md) §4, and `SRC-NNN` in [`research-report.md`](./research-report.md) §6. Identifiers carried from this brief into Phase 1 documents **MUST** keep the same item and the same number; where the same item type appears in more than one document, the project allocates a single project-wide sequence (`documentation-standards.md` §5.4) so that one identifier is never assigned to different items. `INT-NNN` is not a local scheme: it is the standard **Integration Requirement** prefix defined by `documentation-standards.md` §5.1, and its identifiers are project-wide and **MUST NOT** be reused for a different item (§§5.2–5.3).

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Project Brief

| Field | Value |
| --- | --- |
| Purpose | {{One to three sentences: why this brief exists and which decision it supports. It records the intake result so that Phase 1 can begin from a shared, approved understanding.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role, normally the Documentation Agent under Software Architect coordination.}} |
| Authority / approval | {{Who approved this brief; use `Not approved` if no approval exists, and name the pending approver.}} |
| Intake state | {{Idea (greenfield) / Partial documentation / Complete documentation / Existing system modification}} |
| Intake date | {{YYYY-MM-DD}} |
| Intake conducted by | {{Software Architect}} |
| Related documents | {{Documentation audit and manifest, source originals, charter, scope statement, and other dependent documents.}} |

## 1. Intake state

### 1.1 Selected state

| Field | Value |
| --- | --- |
| Intake state | {{Idea (greenfield) / Partial documentation / Complete documentation / Existing system modification — exactly one}} |
| Basis for selection | {{Evidence that supports the selection, with paths or source references}} |
| Confirmed by | {{Human role and date, or `Not confirmed`}} |
| Classification | {{CONFIRMED / ASSUMPTION / RECOMMENDATION}} |

*Guidance: the Software Architect proposes the state from the audit evidence; the human user confirms it. An unconfirmed selection is an `ASSUMPTION`. If the evidence supports more than one state, record the chosen state and the reason for the choice.*

### 1.2 State definitions and their effect

The authoritative definition of the four intake states, including their effect on the questioning path and audit depth, is [`project-initiation.md`](../workflows/project-initiation.md) §4.3. The table below restates it so that this brief can be read on its own; where the two differ, `WF-001` §4.3 prevails.

| Intake state | Meaning | Effect on the questioning path and audit depth |
| --- | --- | --- |
| `Idea (greenfield)` | No project material exists beyond the request itself. | Questions establish the problem, outcomes, users, constraints, and success measures. The audit is minimal: the repository state is confirmed and an empty or near-empty manifest is expected. |
| `Partial documentation` | Some material exists; coverage, currency, and authority are uncertain. | Questions establish what exists, what it covers, what it omits, which version governs, and who owns it. The audit records the supplied material and the gaps against what the lifecycle phases require. |
| `Complete documentation` | Material appears to cover the project's planning, requirements, and design scope. | Questions establish which documents are authoritative, approved, and current. The audit is full: every document is classified, versions and duplicates are analysed, and contradictions are reviewed. |
| `Existing system modification` | A system already operates and the engagement concerns a change to it. | Questions establish what the system does today, its documented interfaces, its operational constraints, and what must change or remain. **Application source code is out of scope:** only the system's documented behaviour, interfaces, and constraints are captured. The audit targets documented behaviour and interface records, not code review. |

*Guidance: the state is a classification of the engagement, not of the user's diligence. Record a change of state in the change history rather than editing §1 silently.*

## 2. Information sources and provenance

| ID | Source | Provided by | Date | Channel | Location | Readability | Classification |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `SRC-001` | {{Title of document, description of the conversation, or the referenced material}} | {{Human role or organizational unit}} | {{YYYY-MM-DD}} | {{File delivery / Pasted text / Verbal / Referenced but not provided / Link}} | {{Repository path, `Not provided`, or `Conversation`}} | {{Readable / Partially readable / Not readable}} | {{Label}} |

*Guidance: identifier scheme used here: `SRC-NNN`. A verbal or pasted statement is recorded with who said it and when. Original files belong under `input/existing-documentation/` and are read-only. A document that is referenced but not provided is a gap: request it and record it in §11, rather than describing its contents.*

## 3. Problem statement and context

{{The problem or opportunity in the user's terms, the situation that gives rise to it, and why it matters now.}}

| Aspect | Statement | Classification | Source |
| --- | --- | --- | --- |
| Problem or opportunity | {{Statement}} | {{Label}} | {{SRC-00N}} |
| Current situation | {{How the problem is handled today, or `Not applicable` for a new capability}} | {{Label}} | {{SRC-00N}} |
| Affected users or areas | {{Who or what is affected}} | {{Label}} | {{SRC-00N}} |
| Consequence of inaction | {{What happens if nothing is done}} | {{Label}} | {{SRC-00N}} |

*Guidance: do not convert an assumed consequence into a confirmed fact. A statement taken from a user is attributable; a statement about an existing system's behaviour requires a documented source.*

## 4. Objectives

| ID | Objective | Measure of achievement | Target | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| `OBJ-001` | {{Objective statement, expressed as an outcome rather than an activity}} | {{How achievement is observed and measured}} | {{Target value, date, or condition}} | {{Label}} | {{SRC-00N or approval reference}} |

*Guidance: identifier scheme used here: `OBJ-NNN`, carried into the charter without renumbering. Objectives must be measurable; an objective whose measure or target is unknown is recorded with `TBD` and paired with an `OPEN QUESTION`. An objective with no source is a `RECOMMENDATION`, not a requirement.*

## 5. Users and stakeholders

| Role or organizational unit | Relationship to the project | Interest | Decision authority | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| {{Role, not a personal name unless the human user requires it}} | {{User / Sponsor / Operator / Regulator / Supplier / Other}} | {{What this role needs or expects}} | {{Decisions this role owns, or `None identified`}} | {{Label}} | {{SRC-00N}} |

*Guidance: an assumed stakeholder remains `ASSUMPTION` until the human user confirms the role. Do not assign decision authority to a stakeholder on an agent's judgement.*

## 6. Preliminary scope

*Guidance: preliminary only. The authoritative boundaries are decided in Phase 1 and recorded in the scope statement. A boundary proposed here is a `RECOMMENDATION` until approved.*

### 6.1 Expected in scope

- {{Capability, deliverable, user group, or activity expected to be included — with classification where it is not obvious}}
- {{...}}

### 6.2 Expected out of scope

| Excluded item | Reason for exclusion | Basis | Classification | Source |
| --- | --- | --- | --- | --- |
| {{Item}} | {{Reason}} | {{Decision, constraint, or absence of requirement}} | {{Label}} | {{SRC-00N}} |

### 6.3 Not yet decided

| Topic | Why it is undecided | Decision point | Reference |
| --- | --- | --- | --- |
| {{Topic}} | {{Reason}} | {{Phase or approval point}} | {{OQ-00N}} |

## 7. Constraints

| ID | Constraint | Type | Basis and source | Impact on the project | Classification |
| --- | --- | --- | --- | --- | --- |
| `CON-001` | {{Constraint}} | {{Technical / Organizational / Regulatory / Budget / Schedule / Contractual}} | {{Statement and its origin}} | {{What it restricts}} | {{Label}} |

*Guidance: identifier scheme used here: `CON-NNN`, aligned with the scope statement's constraint register. A constraint asserted without a source is an `ASSUMPTION`, not a constraint.*

## 8. Integrations

| ID | External system or interface | Direction | Purpose | Known constraints or dependencies | Classification | Source |
| --- | --- | --- | --- | --- | --- | --- |
| `INT-001` | {{System, service, or interface}} | {{Inbound / Outbound / Bidirectional}} | {{What the integration achieves}} | {{Protocol, ownership, access, or dependency as known; `Unknown` otherwise}} | {{Label}} | {{SRC-00N}} |

*Guidance: identifier scheme used here: `INT-NNN`, the standard Integration Requirement prefix. An integration identified during intake remains the same item when it is refined into a requirement during Requirements Analysis; its identifier is not reassigned to a different integration.*

## 9. Risks

| ID | Risk | Likelihood | Impact | Basis | Owner | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `RISK-001` | {{Risk statement: cause, event, consequence}} | {{High / Medium / Low with basis}} | {{High / Medium / Low with basis}} | {{Evidence, or `Assumption` with its basis}} | {{Role}} | {{Open / Mitigated / Accepted / Closed}} |

*Guidance: identifier scheme used here: `RISK-NNN`, shared with the risk register. The detailed risk register in Phase 1 is the authoritative register; this section records only the risks already visible at intake.*

## 10. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption statement}} | {{Why it is currently accepted}} | {{Consequence}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. Each assumption is classified `ASSUMPTION` until verification or an approval is recorded. Acceptance of an assumption does not convert it into a fact.*

## 11. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for approval | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected objectives, scope boundaries, or decisions}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. Blocking status is the Software Architect's decision, not the author's. A resolved item stays in the table with its resolution.*

## 12. Approval status

| ID | Decision | Approving role | Approval date | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| `DEC-001` | {{Approval of this Project Brief, or `Not requested`}} | {{Human role with authority}} | {{YYYY-MM-DD or Pending}} | {{Proposed / Approved / Rejected / Superseded}} | {{Recorded approval reference}} |

**Statement of approval status.** {{State plainly what has and has not been approved. Example shape: "This Project Brief has not been approved. Phase 1 under `WF-002` must not begin until the human user approves it and the approval is recorded here."}}

**Approval gate.** An approved Project Brief is a precondition for Planning and Scope (`WF-002`). Approval of the brief confirms the intake understanding recorded here; it does **not** approve the project, its scope boundaries, its budget, its priorities, or its schedule, which remain separate decisions recorded during Phase 1.

*Guidance: do not describe the brief as approved because the user acknowledged it, asked for work to continue, or did not object. Approval is explicit and recorded with approver and date (`WF-008`).*

## 13. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document, conversation record, or source}} | {{What it supports in this brief}} | {{Repository-relative path, section anchor, or URL with access date}} |

*Guidance: cite only sources that were actually consulted or supplied. Original material under `input/existing-documentation/` may be referenced and is never modified.*

## 14. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
