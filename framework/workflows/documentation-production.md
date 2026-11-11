# Workflow WF-006 — Documentation Production

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-006` |
| Workflow name | Documentation Production |
| Version | `0.1.4` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-006` |
| Purpose | Define how the Documentation Agent receives, executes, and reports a documentation assignment: with explicit authorization, an explicit write scope, applied standards and templates, preserved traceability and approved content, and an accurate account of what was and was not done. |
| Status | `Approved` |
| Version | `0.1.4` |
| Last updated | `2026-11-11` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | v0.1.2 approved by Human user on 2026-11-10. |
| Validation | v0.1.2: PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. v0.1.3: PATCH documentary correction; affected scope re-reviewed by the Validation Agent on 2026-11-11. v0.1.4: PATCH documentary correction (residual VAL-P03) under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. |
| Applies to | Every creation or modification of a project document under `docs/`, and every creation or modification of a framework asset under `framework/`, including persistence of research and validation reports. |
| Related workflows | `WF-001`, `WF-002`, `WF-003`, `WF-004`, `WF-005`, `WF-007` (all invoke this workflow), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§3, 6, 9, 11–13; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§3–10; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §§2–3, 8.4, 10–14; [`framework/standards/README.md`](../standards/README.md) §4. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `VAL`, `CR`) keep the meanings given by the standard, template, or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items — **except** the section-structure convention described in the next paragraph, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines the only path by which a document enters or changes in this repository. The Documentation Agent is the sole writer, and its authority to write is always scoped: a named file list, a named directory, and a named objective.

The workflow exists because unscoped writing is the main way a documentation system loses traceability. A document produced without an authorization has no accountable origin; a document edited outside its authorized scope damages decisions someone else approved. Producing documentation is a professional activity, not an approval: no document becomes approved because it was written well.

---

## 3. Trigger / When to Use

Use this workflow when:

- The Software Architect assigns the creation of a project document.
- The Software Architect assigns a correction, extension, or restatement of an existing document.
- The Software Architect authorizes persistence of a Research Agent or Validation Agent report.
- The Software Architect authorizes a framework change under an identified objective, subject to the framework authorization rules.
- An approved change under `WF-009` requires a specific set of files to be updated.

Do not use this workflow as a substitute for `WF-009`. A change that alters approved decisions, scope, requirements, or architecture baselines is authorized through change control first, and only then executed here.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Creating and modifying files inside the six designated `docs/` directories and the three designated `framework/` directories.
- Applying the documentation standard's structure, metadata, classification, identifier, source, versioning, and completion rules.
- Applying the relevant template where one exists.
- Preserving approved content, prior decisions, and traceability while making an authorized change.
- Reporting what was written, what was assumed, what remains open, and what requires approval or validation.

### 4.2 Deliberately excluded

- Writing outside the nine designated directories, including the root of `docs/` and `framework/`.
- Modifying `README.md`, `AGENTS.md`, `opencode.json`, `.gitignore`, `.opencode/`, `input/existing-documentation/`, `project/`, or any application source.
- Creating scripts, code, prototypes, infrastructure, migrations, or executable artefacts, including as "examples" inside a document.
- Approving, validating, or certifying anything. The Documentation Agent cannot approve its own work.
- Deciding scope, requirements, technology, architecture, budget, or priorities.
- Deleting documents or framework assets. Obsolete content is marked `Superseded` or `Withdrawn` with its replacement identified.
- Modifying framework assets without an authorization that identifies the intended objective or asset.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Issues the assignment, defines the objective and the permitted files, supplies inputs and decisions, reviews the output, and decides whether corrections or validation are required. Writes no files. |
| **Documentation Agent** | Sole writer. Reads the current state, plans the document, drafts or revises it, assigns and preserves identifiers, classifies statements, maintains metadata and change history, and reports back accurately. |
| **Research Agent** | Read-only. Supplies evidence and findings used in the document when the Software Architect provides them. Does not write and does not review the document. |
| **Validation Agent** | Read-only. Reviews the produced document independently when assigned, under `WF-007`. Does not correct it. |
| **Human user / stakeholder** | Approves the content that requires approval. Does not authorize file writes directly; approvals reach the Documentation Agent through the Software Architect. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- An assignment exists from the Software Architect that identifies the objective, the document type, and the permitted files or directory.
- The permitted files lie inside the Documentation Agent's write boundaries.
- Where the assignment concerns a framework asset, a framework authorization exists that identifies the intended objective or asset.
- Where the assignment is a change to approved content, an authorizing decision under `WF-009` exists.
- The Documentation Agent has read the current version of every file it will modify, and the related standards and templates.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Assignment: objective, document type, permitted files, constraints | Software Architect | **MUST** | An assignment without permitted files is incomplete and is returned. |
| Authorizing decision, for changes to approved content | `WF-009` record | **MUST** where applicable | Names the affected files and the approved change. |
| Research findings and sources | Research Agent, via the Software Architect | **SHOULD** | Must be attributable; the Documentation Agent does not research independently. |
| Validation findings to be corrected | Validation Agent, via the Software Architect | **MUST** where the task is a correction | Finding identifiers and status are preserved. |
| Templates | `framework/templates/` | **MUST** where one exists for the document type | A missing template is reported, not invented. |
| Documentation standard | `framework/standards/documentation-standards.md` | **MUST** | Normative for structure, metadata, classification, identifiers, and versioning. |
| Current file contents | Target paths | **MUST** | Required before any modification. |

---

## 7. Workflow Steps

1. **Validate the assignment.** Confirm that it states the objective, the document type, and the permitted files; that the files are inside the write boundaries; and that the task is not a disguised change to approved content. If any element is missing, return the assignment with a precise statement of what is required. Do not infer the missing element from context.
2. **Confirm the authorization class.** Establish whether the task is: new document, authorized correction, authorized change under `WF-009`, persistence of an agent report, or framework change. The class determines the constraints applied in later steps.
3. **Read before writing.** Read the current version of every target file, the related documents it depends on or is referenced by, the applicable template, and the relevant standard sections. A modification without reading the current content is not permitted.
4. **Check for collisions and duplication.** Confirm that the target does not already contain an asset that serves the same purpose, that identifiers in use will not be duplicated, and that no definition is being duplicated across documents. Report collisions rather than resolving them by preference.
5. **Plan the document.** Determine the structure from the template where one exists, or from `documentation-standards.md` §3 where none does. Identify the registers, identifier ranges, and cross-references the document must contain. Note any section that cannot be completed and why.
6. **Establish the fact base.** Separate supplied inputs into confirmed material with a citable source, assumptions, recommendations, and open questions. Where an input is missing, plan a labeled `OPEN QUESTION` or `ASSUMPTION`; do not plan to fill the gap with plausible content.
7. **Draft or revise.** Write the content in the required language, apply the metadata block, apply classification labels at statement or register level, and use tables where they improve traceability. Remove template guidance notes and placeholders, or convert unfillable placeholders into `OPEN QUESTION` entries.
8. **Assign and preserve identifiers.** Assign identifiers at first recording, in the required `PREFIX-NNN` format, unique within their prefix across the project. Never renumber, reuse, or close gaps. Retain withdrawn and superseded identifiers with their disposition.
9. **Maintain traceability.** Record links using stable identifiers, in both directions where the asset is a register, and update affected links in the same change. Where a link does not apply, record a documented exception; never leave an empty cell.
10. **Preserve approved content and prior decisions.** Where an approved statement is no longer valid, mark it superseded with a reason and reference its replacement; do not delete it or rewrite it as though it had never existed. Where a correction contradicts an approved decision, stop and report it instead of applying the correction.
11. **Update metadata, version, and change history.** Apply the status that reflects reality, the version increment that matches the class of change, the last-updated date, and a change-history entry stating the summary and the reason. Do not advance a version without a change-history entry, and do not claim a status that has not been reached.
12. **Self-check against the standard's completion criteria.** Use `documentation-standards.md` §10 as an author's checklist: structure, content, identifiers, traceability, evidence, and governance. A failed item is corrected, or reported as a limitation of the deliverable. This self-check is not independent validation and is not described as such.
13. **Verify write scope after writing.** Confirm that every path written is inside the authorized set and inside the permitted directories. Confirm that no original material, protected file, or out-of-scope document was touched.
14. **Report to the Software Architect.** Report: files created or modified with exact paths; whether the work concerned project documentation or framework assets; the authorization received; the purpose and content of each asset; the decisions and identifiers recorded; sources used; assumptions and open questions; missing information and dependencies; changes requiring stakeholder approval; and items requiring independent validation.
15. **Handle review outcomes.** If the review requests corrections, confirm that the correction is within the existing authorization or obtain a new one; apply it; report the resolution status per finding without claiming a finding resolved before it has been re-reviewed.
16. **Escalate instead of improvising.** Where the assignment requires a change outside the authorized scope, a new framework asset, a modification of a protected file, or a decision the agent cannot make, stop and report. Do not satisfy the intent by writing somewhere else or by loosening the standard.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Documentation Agent | Create, revise, or correct named files. | Explicit file list and objective; write scope limited to those files; report required on completion. |
| Software Architect | Documentation Agent | Persist a Research Agent or Validation Agent report. | Target path under `docs/04-research/` or `docs/05-validation/`; attribution and findings preserved. |
| Documentation Agent | Software Architect | Completion report and material-change report. | Must not describe work as validated, approved, or complete beyond what occurred. |
| Documentation Agent | Software Architect | Escalation of a conflict, collision, missing input, or out-of-scope requirement. | Escalation is not permission to proceed on an assumption. |
| Software Architect | Validation Agent | Independent review of the produced document. | Read-only; findings returned to the Architect, not to the author for direct action. |
| Software Architect | Research Agent | Additional evidence needed for a document in progress. | Read-only; evidence returned to the Architect, who forwards it. |

The Documentation Agent does not delegate, does not launch other agents, and does not communicate with the human user directly. Corrections arrive through the Software Architect.

---

## 9. Expected Outputs

| Output | Description |
| --- | --- |
| Created or modified documents | Markdown, UTF-8 files at the authorized paths, with metadata, classification, identifiers, and change history. |
| Completion report | Files touched, authorization used, purpose and content, sources, assumptions, open questions, dependencies, approval needs, validation needs. |
| Escalation record | Any conflict, collision, missing input, out-of-scope requirement, or protected-file dependency that prevented completion as assigned. |
| Change-history entries | Version, date, summary, reason, author role, and status for every material change. |
| Traceability updates | Affected links and registers updated in the same change, or a reported defect. |
| Persisted agent reports (conditional) | Research or validation records that preserve attribution, findings, severity, limitations, and later decisions separately. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Documentation Standards | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Normative rules applied to every document: §§3–10. |
| Standards governance README | [`framework/standards/README.md`](../standards/README.md) | Authorization rules and governance lifecycle for standards, including the rule that an authorization is asset-specific. Changes to workflows and templates are authorized under `AGENTS.md` §11; the standards governance model is referenced here as the closest established precedent, not as governing authority over workflows. No dedicated governance document exists for workflows and templates, but a specific framework-change rule for approved framework assets was approved by the Human user on 2026-11-10 and is recorded in §12. |
| Project Charter template | [`framework/templates/project-charter.md`](../templates/project-charter.md) | Phase 1 deliverable structure. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Phase 1 deliverable structure. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | Phase 1 deliverable structure. |
| Software Requirements Specification template | [`framework/templates/software-requirements-specification.md`](../templates/software-requirements-specification.md) | Phase 2 deliverable structure. |
| Use Case template | [`framework/templates/use-case.md`](../templates/use-case.md) | Phase 2 use case structure. |
| Requirements Traceability Matrix template | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | Phase 2 traceability structure. |
| Architecture Overview template | [`framework/templates/architecture-overview.md`](../templates/architecture-overview.md) | Phase 3 architecture structure. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Phase 3 decision structure. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Persistence structure for research reports. |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Persistence structure for validation reports. |

**Template coverage (observed 2026-11-10).** Ten templates exist. Several deliverable types named in `AGENTS.md` and in the phase workflows have no template. The Documentation Agent **MUST** apply `documentation-standards.md` §3 to those documents, **MUST** report the absence in its completion report, and **MUST NOT** create a template unless separately authorized.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Authorization check | Documentation Agent | No write occurs without an assignment naming the objective and the permitted files. |
| Boundary check | Documentation Agent | Every written path lies inside the nine designated directories and inside the authorized set. |
| Read-before-write | Documentation Agent | The current version of each modified file was read in this task. |
| Template and standard compliance | Documentation Agent, reviewed by the Software Architect | Structure and metadata follow the template and the standard, or the deviation is recorded. |
| Classification accuracy | Documentation Agent | Every statement whose certainty matters carries exactly one label; `CONFIRMED` has a citable basis. |
| Identifier integrity | Documentation Agent, checked by the Validation Agent | No duplicate, reused, or renumbered identifier; withdrawn identifiers retained. |
| Traceability preservation | Documentation Agent | Links updated in the same change; exceptions documented; defects reported. |
| Version and history discipline | Documentation Agent | Version increment matches the change class; every material change has a change-history entry. |
| Status honesty | Documentation Agent | No document claims approval, validation, or completion that did not occur. |
| Independent validation | Validation Agent, under `WF-007` | Performed when assigned; the author's self-check is never presented as independent review. |
| Write verification | Documentation Agent, confirmed by the Software Architect | The completion report lists every path touched, and no other path changed. |

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Approval of the content produced | Human user, on the Software Architect's presentation | After review and any required validation | Writing a document does not approve it; approval is recorded through `WF-008`. |
| Approval of any change to previously approved content | Human user, through `WF-009` | Before the change is executed | No approved statement is altered under a drafting assignment. |
| Authorization to create or change any framework asset | **Software Architect**, in every case (`AGENTS.md` §11) | Before any framework write | No framework write occurs without an authorization that identifies the asset or the intended objective; framework authorization is granted per asset, not in general, and a workflow authorization does not extend to a template or a standard. |
| Human approval of a change to an already-approved framework asset | **Human user**, on the Software Architect's presentation — **approved rule** (Human user, 2026-11-10) | Before the change is executed, where the asset is already approved | A modification to an approved framework asset requires **two distinct approvals**: (1) **human approval of the proposed change**, given by the authority that approved the asset; and (2) **specific Software Architect authorization** identifying the exact files the Documentation Agent may modify and the permitted scope of each. The two are not interchangeable: Software Architect authorization does **NOT** replace human approval, and human approval does **NOT** by itself authorize a file write. The rule applies to approved standards, templates, and workflows, and it is recorded in `WF-009` §12. It is an approved framework rule, not a recommendation. |
| Approval of content that affects scope, budget, requirements, security, technology, or architecture | Human user | At the decision point in the phase workflow | The document records the outcome; it does not create the approval. |

There is no approval step internal to documentation production. The absence of an approval step is deliberate: the Documentation Agent has no authority to approve, and no amount of authoring produces an approval.

---

## 13. Completion Criteria

A documentation assignment under this workflow is complete when all of the following hold:

- [ ] The assignment named the objective, the document type, and the permitted files.
- [ ] The authorization class was identified, and a `WF-009` authorization existed where the task changed approved content.
- [ ] The current version of each modified file, the applicable template, and the relevant standard sections were read first.
- [ ] Every written path is inside the authorized set and inside the permitted directories.
- [ ] The document has a title, metadata block, classification labels, and a change-history entry.
- [ ] Identifiers were assigned at first recording and none were renumbered, reused, or closed.
- [ ] Traceability links were updated in the same change, or the defect was reported.
- [ ] Approved content was preserved; superseded content names its replacement and reason.
- [ ] The self-check against `documentation-standards.md` §10 was performed, and any failed item is reported as a limitation.
- [ ] The completion report was delivered to the Software Architect with all required elements.
- [ ] No original material, protected file, out-of-scope document, or protected path was modified.
- [ ] No document or asset is described as validated, approved, or final without the corresponding recorded review or approval.

---

## 14. Exception Handling

### 14.1 Insufficient or ambiguous assignment

Return the assignment with a precise statement of the missing element: which file, which objective, which document type, or which authorizing decision. Do not begin drafting on the basis of a plausible interpretation. A partial draft produced under an inferred scope is harder to withdraw than a clarification request is to answer.

### 14.2 Missing information for content

Record the gap as `OPEN QUESTION` with an owner, or as `ASSUMPTION` with its basis, impact if wrong, and verification path. A placeholder left in a delivered document is acceptable only when it is explicitly labeled; an unlabeled placeholder is a defect.

### 14.3 Contradictions between sources or documents

Record the contradiction with both locations and escalate. Do not reconcile by choosing the newer, the more detailed, or the more convenient source. Where the contradiction affects an approved statement, report it as a potential change requiring `WF-009`.

### 14.4 Template missing, or template conflicting with the standard

Where no template exists, apply the standard's structure and report the gap. Where a template conflicts with the standard or with repository instructions, do not silently choose one: report the conflict to the Software Architect, who resolves it within the applicable governance path. The Documentation Agent **MUST NOT** edit the template or the standard to remove the conflict.

### 14.5 Out-of-scope requests

A request to write outside the nine directories, modify a protected file, create a new framework asset, or produce executable content is refused, explained, and reported. The refusal is recorded with the reason; it is not satisfied by an alternative location or an indirect form.

### 14.6 Findings and review pressure

A request to remove, soften, downgrade, or omit a validation finding, or to describe a document as approved or validated before that occurred, is refused and escalated. The Documentation Agent records corrections and resolution status; it does not adjudicate findings.

### 14.7 Persistence of agent reports

When persisting a report, preserve attribution, date or session context, findings, severity, limitations, and recommendations. Later decisions and corrections are recorded in the report's status section, not by rewriting the findings. Persistence does not validate the report and does not approve any decision it discusses.

### 14.8 Interrupted or partial work

If a task cannot be completed, report the state precisely: which files were written, which were not, and what remains. Do not leave a document in a state that implies completion, such as a filled metadata block with a status that overstates progress.

### 14.9 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-006-01` | Should the Documentation Agent be permitted to create a missing template when a phase deliverable requires one, or must templates always be a separate authorization? | Affects how the documentation gaps are closed and who decides their structure. | Software Architect |
| `OQ-WF-006-02` | When one change touches several documents, is a single authorization with a file list sufficient, or is a per-document authorization expected? | Affects the auditability of a multi-document change. | Software Architect |
| `OQ-WF-006-03` | Is there an expected location for a project-level change record, or is the change history of each affected document sufficient? | Traceability of changes across documents depends on it. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | Invokes this workflow to persist an audit or work plan. |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Invokes this workflow for Phase 1 deliverables. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Invokes this workflow for Phase 2 deliverables. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Invokes this workflow for Phase 3 deliverables. |
| [`WF-005` — Research](./research.md) | Invokes this workflow to persist a research report. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invokes this workflow to apply authorized corrections and to persist a validation report. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Records approval outcomes that this workflow then documents. |
| [`WF-009` — Change Control](./change-control.md) | Authorizes the file set and the change that this workflow executes. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the documentation production workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a controlled, auditable path for all documentation writes, with explicit authorization and preserved traceability. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001); the framework-change approval row in §12 is reconciled with §10, stating that Software Architect authorization is always required and that human approval of a change to an already-approved framework asset is a `RECOMMENDATION` pending a workflow-governance decision (VAL-002); and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval; governance rule for approved framework assets (double authorization: human approval + exact-file Architect authorization) incorporated per Human user approval of 2026-11-10. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.1.3 | 2026-11-11 | PATCH documentary correction: the §1 "Normative basis" now carves out the section-structure convention — which remains a `RECOMMENDATION` until a durable workflow-governance document is established — so that it is no longer read as already in effect as part of the approved workflow; the `Authority / approval` field now attributes the Human approval to v0.1.2; and the `Validation` field now attributes the PASS result to v0.1.2 and records this version as a PATCH documentary correction not requiring re-validation per WF-009 §11.2. No rule, procedural step, approval, or approved decision was changed; status remains `Approved`. | Resolve the systemic "Normative basis / Section structure" pattern under the carve-out recorded in WF-009 §16 and align the metadata attribution with the change history. Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.2 approved by Human user on 2026-11-10; v0.1.3 PATCH documentary correction; the v0.1.2 validation result stands. |
| 0.1.4 | 2026-11-11 | PATCH documentary correction: the `Validation` field no longer asserts that re-validation is not required for v0.1.3 by reference to WF-009 §11.2; it now records that the affected scope was re-reviewed by the Validation Agent on 2026-11-11, and a v0.1.4 entry records this residual correction (VAL-P03). Status remains `Approved`; "Normative basis" and "Authority / approval" are unchanged. No rule, procedural step, approval, or approved decision was changed. | Resolve validation finding VAL-P03 (residual). Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.2 approved by Human user on 2026-11-10; v0.1.4 PATCH documentary correction; the v0.1.2 validation result stands. |
