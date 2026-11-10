# Workflow WF-009 — Change Control

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-009` |
| Workflow name | Change Control |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-009` |
| Purpose | Define how a proposed change to project documentation or to a framework asset is identified, described, analyzed for impact, classified, approved at the level it warrants, authorized for specific files, executed, re-validated where required, and recorded with its decision, version, impact, and traceability. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Any proposed change to generated project documentation, to persisted research or validation reports, and to framework assets, at any point in Phases 1 to 3 and after any approval. |
| Related workflows | `WF-001`, `WF-002`, `WF-003`, `WF-004` (phases in which changes arise), `WF-005` (research), `WF-006` (documentation production), `WF-007` (re-validation), `WF-008` (approval and phase gate). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§6, 7, 12; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§5.3, 8.3, 9.1, 9.3; [`framework/standards/README.md`](../standards/README.md) §§4.2–5.6; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §11. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them.

**Change-request identifiers.** This workflow establishes the register scheme `CR-NNN` for change requests, assigned sequentially, unique per project, and never reused. `CR` is a **project-level register identifier**, not one of the six requirement prefixes: a change request is cross-referenced from every document and register it affects, so the scheme is shared across the project rather than local to a single document. It is documented here, as `documentation-standards.md` §5.5 requires for schemes outside that set, and the range-allocation discipline of `documentation-standards.md` §5.4 applies to it as it does to the project-level `DEC` and `ADR` schemes. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `VAL`, `TRD`, `EXC`) keep the meanings given by the standard, template, or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines how approved documentation is allowed to change without losing its history, its traceability, or the authority behind its decisions.

Two opposite failures are addressed. The first is uncontrolled change: an agent adjusts an approved scope boundary, renumbers requirements, or rewrites a decision because the correction seems obvious. The second is excessive control: every typographical correction is escalated to a full impact analysis, so the process is bypassed in practice. The workflow therefore classifies changes and applies proportionate discipline, while never letting a classification downgrade a change that genuinely affects an approved baseline.

A third rule is absolute: an approved change authorizes a *content* decision, not a *file write*. Writing requires the separate, explicit authorization described in section 7, step 11.

---

## 3. Trigger / When to Use

Use this workflow when:

- A stakeholder, the Software Architect, the Research Agent, the Validation Agent, or the Documentation Agent identifies a defect, omission, or improvement in generated documentation.
- Evidence obtained after approval contradicts a recorded statement.
- A validation finding requires a correction that alters approved content.
- A phase-gate decision imposes conditions that change deliverables.
- A requirement, scope, priority, technology, or architecture decision is to be revised, withdrawn, or superseded.
- A framework asset must be corrected or extended.

Use `WF-006` alone — without this workflow — for work that is within an existing authorization and does not alter approved content: drafting a new document, or making an editorial correction to a document that is still `Draft`.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Capturing and identifying change requests, including their origin and the problem they address.
- Describing the proposed change precisely enough to be assessed.
- Impact analysis across scope, budget, roadmap, risks, requirements, use cases, traceability, architecture, and approved documents.
- Classification of the change and determination of the approval level it requires.
- Identifying the agents and deliverables affected.
- Architect recommendation and human approval where appropriate.
- Explicit write authorization naming the files that may be updated.
- Execution by the Documentation Agent, with version, history, and traceability updates.
- Independent re-validation where a validated deliverable is affected.
- Recording the decision, version, impact, and traceability of the change.

### 4.2 Deliberately excluded

- Making the change before it is authorized.
- Assuming that a change needs the same approval level as every other change.
- Assuming that an approved change permits any file to be modified.
- Modifying original project material under `input/existing-documentation/`, which is never edited, renamed, moved, replaced, or deleted.
- Modifying protected repository files (`README.md`, `AGENTS.md`, `opencode.json`, `.gitignore`, `.opencode/`), which require human-controlled repository maintenance and are reported, not changed.
- Deleting documentation or framework assets. Obsolete content is marked `Superseded` or `Withdrawn` with its replacement identified.
- Application implementation of any kind.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Receives and records change requests, performs or directs the impact analysis, classifies the change, recommends a decision, presents it for human approval where required, and issues the write authorization. Writes no files. |
| **Documentation Agent** | Identifies defects and inconsistencies in its own work and reports them; executes authorized changes to named files; updates versions, change history, identifiers, and traceability; reports exactly what changed. Does not decide whether a change is required. |
| **Research Agent** | Read-only. Supplies evidence where a change depends on external facts or where new evidence motivates the change. |
| **Validation Agent** | Read-only. Identifies findings that may require a change, and re-reviews changed deliverables when assigned. Cannot approve a change. |
| **Human user / stakeholder** | Approves changes that affect approved decisions, scope, budget, priorities, requirements, security and privacy, technology, architecture, or a validated baseline. The approving authority for a change is the authority that approved the original, unless it is explicitly delegated. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- The affected documents exist and their current versions are known.
- The change request identifies the problem, not only a preferred solution.
- The current approval and validation status of the affected material has been established.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Change request | Any participant, submitted to the Software Architect | **MUST** | Must state the problem and the proposed change. |
| Affected documents and versions | Repository | **MUST** | Read before analysis; versions recorded. |
| Current decisions and baselines | `DEC-NNN`, `ADR-NNN`, approved documents | **MUST** | Determines whether approved content is affected. |
| Validation findings, where relevant | `docs/05-validation/` | **SHOULD** | Findings retain identifiers and status. |
| Evidence supporting the change | Research Agent, supplied stakeholders, original material | **SHOULD** | A change based on assumption is labeled as such. |
| Traceability matrix and defect log | `docs/02-requirements/` | **SHOULD** | Impact analysis must detect links that will break. |
| Framework authorization, for framework changes | Software Architect | **MUST** for framework assets | Identifies the intended objective or asset. |

---

## 7. Workflow Steps

1. **Capture the change request.** The Software Architect records the request as `CR-NNN`, with: originator and role, date, the problem observed, the proposed change, the documents believed to be affected, and any deadline or driver. A request expressed only as a preferred solution is converted into a problem statement before assessment.
2. **Confirm the problem.** Verify that the problem is real and current: that the affected statement still exists at the stated version, and that the defect is not a misreading of the document. A request based on an outdated version is closed with the reason and, where useful, re-raised against the current version.
3. **Describe the proposed change precisely.** State what would be added, amended, superseded, or withdrawn, in which documents and sections, and using which identifiers. A change described only as "update the requirements" cannot be assessed or authorized.
4. **Collect the baseline facts.** Record the current version and status of each affected document, the decisions and approvals it carries, whether it has been independently validated, and whether it is referenced by other documents or registers.
5. **Perform the impact analysis.** Assess the change against each dimension in the table below. For every dimension, state the impact or state `No impact` with a basis; an unexamined dimension is not the same as an unaffected one.
6. **Classify the change.** Assign `Documentary correction`, `Minor change`, or `Significant change` using the definitions in the table below. Where the classification is uncertain, the higher class applies until the Software Architect records a reasoned decision otherwise.
7. **Identify affected agents and deliverables.** Name which agents must act (Research for evidence, Validation for re-review, Documentation for execution), which deliverables will change, and which dependencies and cross-references must be updated in the same change.
8. **Determine the required approval level.** State whether the change requires human approval, Software Architect authorization alone, or neither, and why. The approval authority for a change to an approved decision is the authority that approved it, unless delegated explicitly.
9. **Form the Architect recommendation.** Recommend accept, reject, defer, or accept with conditions, with reasoning, consequences, and the consequences of not changing. Present alternatives where they exist, including the option of superseding the affected content rather than amending it.
10. **Obtain the decision.** For changes requiring human approval, present the change under `WF-008` with its impact and recommendation, and record the decision, conditions, and approver. For changes within the Software Architect's authority, record the decision and its rationale.
11. **Issue an explicit write authorization.** The Software Architect authorizes the Documentation Agent with: the change-request identifier, the exact files that may be modified, the sections or identifiers to change, what must be preserved, and any constraint. An approval of the change does **NOT** by itself authorize any file write, and an authorization for one change does not extend to another.
12. **Execute the change under `WF-006`.** The Documentation Agent reads the current versions, applies only the authorized change, preserves unaffected content, and avoids unrelated rewriting.
13. **Preserve superseded and withdrawn content.** A statement that is no longer valid is marked `Superseded` or `Withdrawn` with its reason and, where applicable, its replacement. Requirements and decisions are never deleted, renumbered without recorded approval, or rewritten to appear as though they had always read differently.
14. **Update versions and history.** Apply the version increment implied by the classification, add a change-history entry with summary, reason, author role, and status, and record the change-request identifier in the affected documents so the change is traceable to its origin.
15. **Update traceability in the same change.** Add, amend, or withdraw links so that the chain Business Rule → Requirement → User Story / Use Case → Architecture Decision → Acceptance Criteria → Future Test remains accurate, and update the traceability matrix and defect log. Links broken by the change and not corrected are logged as defects.
16. **Re-validate where required.** Where the change affects a deliverable that was independently validated, request re-review under `WF-007` for the affected scope. Validation of the earlier version remains valid only for that version. Findings that prompted the change are updated only after re-review confirms the correction.
17. **Record the change outcome.** Record: change identifier, decision and approver, date, classification, files changed with old and new versions, impact assessment summary, affected identifiers, traceability updates, re-validation outcome, and conditions. Where a project-level change record exists or is authorized, it holds this entry; otherwise each affected document's change history carries its own entry and the Software Architect's report carries the consolidated record.
18. **Close or keep the change open.** Close only when execution, versioning, traceability updates, and any required re-validation are complete. A change whose correction is drafted but not re-reviewed remains open with status `Correction proposed`.
19. **Handle follow-on changes separately.** A new problem discovered during execution is raised as a new `CR` entry; it is not absorbed into the current change without authorization.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Any participant | Software Architect | Submit a change request. | States a problem; does not authorize a write. |
| Software Architect | Research Agent | Evidence for a change that depends on external facts. | Read-only; findings returned to the Architect. |
| Software Architect | Validation Agent | Re-review of changed material. | Read-only; re-review scoped to the affected content and its links. |
| Software Architect | Documentation Agent | Execute the authorized change to named files. | Change identifier, file list, sections, and preservation constraints required. |
| Documentation Agent | Software Architect | Report of what changed, what was preserved, and what remains open. | Must state old and new versions and any traceability effect. |
| Software Architect | Human user | Decision on changes that affect approved decisions, scope, budget, requirements, security, technology, architecture, or a validated baseline. | Presented under `WF-008` with impact and recommendation. |

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Change request record | Software Architect | `CR` entry with origin, problem, proposed change, and affected documents. |
| Impact analysis | Software Architect | Assessment across every dimension in §7 step 5, with `No impact` bases stated. |
| Change classification | Software Architect | One of the three classes, with reasoning. |
| Change decision | Human user or Software Architect, as the class requires | Accept, reject, defer, or accept with conditions, with approver and date. |
| Write authorization | Software Architect | Named files and sections, with preservation constraints. |
| Updated documents | Documentation Agent | Changed files with new versions and change-history entries. |
| Traceability and defect updates | Documentation Agent | Updated links, matrix, and defect log. |
| Re-validation outcome | Validation Agent, then documented | Finding status after re-review. |
| Consolidated change record | Software Architect; persisted only if authorized | Decision, version, impact, and traceability in one place. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Documentation Standards §9 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Versioning rules, status vocabulary, and change-control requirements applied in steps 13 to 15. |
| Documentation Standards §5.3 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Identifier stability, renumbering approval, and retention of withdrawn items. |
| Documentation Standards §6 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Traceability chain and defect categories to re-check after a change. |
| Standards governance README §5 | [`framework/standards/README.md`](../standards/README.md) | Authorization, review, and approval discipline for changes to standards. It is cited as the established reference model for framework change discipline; no dedicated governance document exists for workflows and templates, but a specific framework-change rule for approved framework assets was approved by the Human user on 2026-11-10 and is recorded in §12 of this workflow. |
| Scope Statement template §2.3 | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Place where a project records how scope changes are requested and approved. This workflow defines the discipline that entry follows; it does not create a second, competing process. |
| Architecture Decision Record template §13 | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Amendment log and supersession discipline for changed decisions. |
| Requirements Traceability Matrix template §6 | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | Defect log updated when a change breaks links. |
| Validation Report template §10 | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Finding status after review, updated only after re-review. |

**Template availability (observed 2026-11-10).** No template exists for a change request, an impact analysis, or a consolidated change record. This workflow defines the content those records must contain; the Documentation Agent **MUST** apply `documentation-standards.md` §3 where persistence is authorized and **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

### 11.1 Impact dimensions

| Dimension | What the analysis must determine |
| --- | --- |
| Scope | Whether an in-scope or out-of-scope boundary changes, and whether the change is inside the approved scope. |
| Budget and costs | Whether cost estimates, their bases, or their approval status change. |
| Roadmap and schedule | Whether milestones, dependencies, or target dates are affected, and whether any date was treated as a commitment. |
| Risks | Whether risks are introduced, retired, or re-rated, and whether the risk register is updated. |
| Requirements | Which `FR`, `NFR`, `BR`, `SEC`, `INT`, or `UC` entries are added, amended, superseded, or withdrawn. |
| Use cases and acceptance criteria | Which behaviors and verification criteria change, and whether any criterion becomes unverifiable. |
| Traceability | Which links break, which must be created, and which exceptions or defects must be recorded. |
| Architecture | Which components, boundaries, data ownership, or `ADR` records are affected, and whether an accepted decision must be superseded. |
| Approved documents | Which approved statements are affected, who approved them, and whether their approval must be revisited. |
| Dependencies and references | Which other documents cite the changed content and must be updated in the same change. |

### 11.2 Change classes

| Class | Definition | Version effect | Minimum authority |
| --- | --- | --- | --- |
| `Documentary correction` | Editorial or factual correction that does not change meaning, decisions, scope, identifiers, or traceability. Examples: spelling, broken internal link, metadata date, formatting. | `PATCH` | Software Architect authorization; write authorization still required. |
| `Minor change` | Additive or clarifying change that does not alter an approved decision, baseline, or the meaning of approved content. Examples: an added open question, an added source, a clarified sentence consistent with the approved intent. | `MINOR` | Software Architect authorization; human notification where the document is approved. |
| `Significant change` | Any change that alters an approved decision, scope, budget, priority, requirement, acceptance criterion, identifier assignment, architecture decision, security posture, or validated baseline; or that withdraws or supersedes approved content. | `MAJOR` | Human approval by the authority that approved the original, plus independent re-validation where the deliverable was validated. |

The three-class scheme and its `Minimum authority` mapping are an **approved framework convention**, not a pending recommendation, consistent with the normative-basis note in §1: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS).

The classification is a proposal by the Software Architect until the decision is recorded. Where the correct class is disputed, the higher class governs until the dispute is decided.

### 11.3 Quality controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Problem stated before solution | Software Architect | The request describes the problem, not only a preferred wording. |
| Baseline verified | Software Architect | Analysis is performed against the current version, not a remembered one. |
| Every dimension addressed | Software Architect | Each impact dimension is assessed or explicitly marked `No impact` with a basis. |
| Proportionate approval | Software Architect | The approval level matches the class; a significant change is never processed as editorial. |
| Authorization before write | Software Architect, Documentation Agent | No file is modified without an authorization naming it. |
| Content preservation | Documentation Agent | Unaffected content is retained; superseded content remains visible with its reason. |
| Version and history accuracy | Documentation Agent | Version increment matches the class; every material change has an entry naming the change request. |
| Traceability in the same change | Documentation Agent | Links and registers are updated together with the change. |
| Re-validation discipline | Validation Agent | Changed validated material is re-reviewed; earlier validation does not extend to new content. |
| Closure honesty | Software Architect | A change is closed only when execution and required re-review are complete. |

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Acceptance of a `Significant change` | Human user, normally the authority that approved the original content | Before the write authorization is issued | The change is not executed until approved. |
| Acceptance of a change to approved scope, budget, or priorities | Human user | With the change decision | The workflow may analyze the change; it may not commit to it. |
| Acceptance of a change to approved requirements, security posture, technology, or architecture | Human user | With the change decision | A decision remains recorded as `Superseded` or amended only after the approval. |
| Acceptance of risk introduced by a change | Human user | Where the change creates a risk the approver must own | Risk acceptance is recorded with its authority. |
| Re-validation requirement for a validated baseline | Software Architect, with human approval where the change is significant | Before closure | Independent re-review is performed for the affected scope. |
| Authorization to create or change any framework asset | **Software Architect**, in every case (`AGENTS.md` §11) | Before any framework write | No framework write occurs without an authorization that identifies the asset or the intended objective; framework authorization is per asset and per objective. |
| Human approval of a change to an already-approved framework asset | **Human user**, on the Software Architect's presentation — **approved rule** (Human user, 2026-11-10) | Before execution, where the asset is already approved | A modification to an approved framework asset requires **two distinct approvals**: (1) **human approval of the proposed change**, given by the authority that approved the asset; and (2) **specific Software Architect authorization** identifying the exact files the Documentation Agent may modify and the permitted scope of each. The two are not interchangeable: Software Architect authorization does **NOT** replace human approval, and human approval does **NOT** by itself authorize a file write. The rule applies to approved standards, templates, and workflows. It is recorded here as an approved framework rule, not as a recommendation. |

**Approved framework-change rule (Human user, 2026-11-10).** A modification to an approved framework asset — standard, template, or workflow — requires two distinct approvals: human approval of the proposed change, and specific Software Architect authorization naming the exact files the Documentation Agent may modify and the permitted scope. Software Architect authorization does not replace human approval; human approval does not by itself authorize a write. This is an approved rule, derived from `AGENTS.md` §7 (changes to previously approved deliverables) and §11 (framework authorization in every case), and it is recorded here because no dedicated governance document exists for workflows and templates (§10). The two approvals are cumulative with the "Authorization to create or change any framework asset" row above, which remains in force.

Humans are not asked to approve editorial corrections. Applying a uniform approval level to every change is a failure of this workflow, not a demonstration of rigour.

---

## 13. Completion Criteria

A change is complete when all of the following hold:

- [ ] The change request is recorded with `CR` identifier, origin, problem, and proposed change.
- [ ] The problem was confirmed against the current version of the affected content.
- [ ] The proposed change is described with documents, sections, and identifiers.
- [ ] The impact analysis addresses every dimension, with `No impact` bases stated.
- [ ] The change is classified, and the classification is recorded with its reasoning.
- [ ] The required approval level was determined and the decision obtained and recorded with approver, date, and conditions.
- [ ] A write authorization named the files and sections that could change.
- [ ] Only those files changed; unaffected content was preserved.
- [ ] Superseded or withdrawn content remains visible with its reason and any replacement.
- [ ] Versions and change histories were updated, and the change request is referenced.
- [ ] Traceability links, the matrix, and the defect log were updated in the same change.
- [ ] Re-validation was performed where a validated deliverable was affected, and finding status reflects the re-review.
- [ ] The consolidated outcome — decision, version, impact, traceability — is recorded.
- [ ] No original material, protected file, or out-of-scope document was modified.

---

## 14. Exception Handling

### 14.1 Insufficient information to assess the change

Where the request cannot be assessed because the affected content, the problem, or the intended outcome is unclear, record the missing element and return to the originator. Do not classify a change on the basis of an assumed impact; a `Documentary correction` classification based on incomplete reading is how approved content is lost.

### 14.2 Conflicting change requests

Where two requests affect the same content differently, both are recorded and the conflict is presented for decision. Neither is executed first on the grounds of being simpler. Where one request supersedes another, that is recorded as a decision.

### 14.3 Contradictory or invalidating evidence

Where new evidence contradicts approved content, the evidence is reported with its source and limitations, and the change is classified on the basis of what would be altered. The original statement is superseded with its reason; it is not rewritten as though the earlier evidence had never been accepted.

### 14.4 Pressure to treat a significant change as editorial

A request to reword, renumber, or "tidy" content that alters meaning, decisions, or identifiers is refused as editorial and escalated with the classification that applies. The refusal and the request are recorded. Identifier renumbering additionally requires explicit Software Architect approval and a recorded rationale.

### 14.5 Change requested by an unauthorized party

A request is assessed regardless of who raises it, but the decision is taken by the authority the class requires. A request from someone without decision authority is recorded as a request, not as a decision.

### 14.6 Changes affecting validated deliverables

Where a validated deliverable is changed, closure waits for re-review. If re-review cannot be performed, the change remains open with the reason recorded, and any dependent phase gate reflects that the baseline is not currently validated.

### 14.7 Changes to protected files or original material

A change that would require editing `input/existing-documentation/` or a protected repository file cannot be executed by any agent. It is recorded, refused, and escalated to the Software Architect for human-controlled repository maintenance. The refusal is not satisfied by copying the protected content elsewhere and editing the copy.

### 14.8 Change requested during an active validation

Where a reviewer is assessing a version that is about to change, the Software Architect records that the review applies to the version named. The change proceeds only after the review's findings are recorded, so that findings are not silently invalidated by a moving target.

### 14.9 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-009-01` | Should a consolidated change record be a persisted project artifact, and if so under which `docs/` directory? | Without it, the decision and impact of a change are scattered across document change histories. | Software Architect |
| `OQ-WF-009-02` | Is a change that only adds an `OPEN QUESTION` or a source a `Minor change` requiring human notification, or a `Documentary correction`? | Boundary cases will otherwise be classified inconsistently. | Software Architect |
| `OQ-WF-009-03` | Does a framework change to a template also require re-validation of every document produced from the earlier template version? | Determines the scope of re-review after framework changes. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | New or changed project material may require re-baselining, which this workflow governs where approved content is affected. |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Source of changes to scope, budget, priorities, and Phase 1 deliverables. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Source of changes to requirements, rules, criteria, and traceability, including identifier consequences. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Source of changes to decisions, architecture baselines, and amendments or supersession. |
| [`WF-005` — Research](./research.md) | Source of new evidence that may invalidate approved content. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Executes the authorized change to the named files. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Re-reviews changed validated material and confirms whether findings are resolved. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Records the human decision for significant changes and the gate implications. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the change control workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a proportionate change procedure that preserves approvals, history, and traceability without treating every correction as a decision. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001); the framework-change approval row in §12 is reconciled with §10, stating that Software Architect authorization is always required and that human approval of a change to an already-approved framework asset is a `RECOMMENDATION` pending a workflow-governance decision (VAL-002); `CR-NNN` is relabelled as a project-level register identifier with §5.4 range allocation (VAL-003); the open-questions block now states that none of its items blocks the procedural steps (VAL-004); and the change-class scheme in §11.2 is marked as a proposed convention (VAL-007). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval; governance rule for approved framework assets (double authorization: human approval + exact-file Architect authorization) incorporated per Human user approval of 2026-11-10. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
