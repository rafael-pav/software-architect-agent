# Workflow WF-002 — Planning and Scope

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-002` |
| Workflow name | Planning and Scope |
| Version | `0.2.0` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-002` |
| Purpose | Define how Phase 1 (Planning and Scope) deliverables are produced, reviewed, and presented so that scope, budget, priorities, and schedule assumptions are established with classified evidence and explicit human approval rather than agent assumption, beginning from an approved Project Brief. |
| Status | `Approved` |
| Version | `0.2.0` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | v0.1.2: independent validation PASS. v0.2.0: independent validation PASS (findings MEDIUM, LOW, and INFORMATIONAL resolved). |
| Applies to | Phase 1 work on any project, whether or not Phase 1 was preceded by `WF-001`. |
| Related workflows | `WF-001` (initiation), `WF-003` (successor phase), `WF-005` (research), `WF-006` (documentation production), `WF-007` (independent validation), `WF-008` (approval and phase gate), `WF-009` (change control), `WF-010` (technology capability assessment). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§5–7, 10; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§4, 7, 8, 9; [`project-brief.md`](../templates/project-brief.md); [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) §§5–6, 9; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §7. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `VAL`, `OBJ`, `SC`, `MS`, `DLV`, `CON`, `DEP`, `CRIT`, `OPT`) keep the meanings given by the standard, template, or agent definition that establishes them; this workflow does not redefine them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. The conventions introduced in v0.1.2 are in effect as part of an approved workflow: v0.1.2 was approved by the Human user on 2026-11-10 and independently validated (PASS). The Project Brief precondition and the mandatory persistence requirements introduced in v0.2.0 are in effect as part of the approved workflow: v0.2.0 was approved by the Human user on 2026-11-10 and independently validated (PASS). Approval does not change their normative rank — `AGENTS.md`, the agent definitions, and `documentation-standards.md` prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines Phase 1: the production of the planning and scope deliverables that establish why a project is being undertaken, what it includes and excludes, what it is expected to cost, how it will be sequenced, and what threatens it.

It exists to keep three things separate that are routinely conflated: the *evidence* about the project, the *recommendations* made by agents, and the *decisions* reserved for the human user. A feasibility study informs a decision; it does not make one. A charter records approval status; it does not confer approval.

---

## 3. Trigger / When to Use

Use this workflow when:

- The human user has authorized Phase 1 work, normally following `WF-001`.
- A previously approved Phase 1 deliverable must be extended within its approved scope.
- A change request requires Phase 1-level impact analysis and re-issue of planning deliverables (coordinated with `WF-009`).

Do not use this workflow to draft requirements or architecture. Those belong to `WF-003` and `WF-004`. A planning question that requires design analysis is recorded and referred, not answered with design detail.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Project Charter, Scope Statement, Stakeholder Analysis, Feasibility Study, Budget Estimate, Project Roadmap, Risk Register, and Assumptions Register, to the extent they apply to the project.
- Determining deliverable applicability and recording the reason for each exclusion.
- Commissioning research needed for feasibility, cost, licensing, or technical viability.
- Assessing, under `WF-010`, any planning-time need that may require an OpenCode mechanism — a Skill, Command, agent, MCP server, or Plugin. A resulting recommendation is an input to a planning decision, never an installation.
- Internal consistency review across Phase 1 deliverables.
- Preparation of the decisions that require human approval.

### 4.2 Deliberately excluded

- Approving the project, its scope, its budget, its priorities, or its schedule. Those are human decisions.
- Functional and non-functional requirements (`WF-003`), even where a charter references them.
- Architecture, technology selection, and integration design (`WF-004`). Feasibility may compare technology options, but selecting one is a decision and an architecture input.
- Application implementation, cost quotations presented as commitments, or schedule commitments made by an agent.
- Installing, enabling, or configuring any OpenCode mechanism, even where `WF-010` recommends one.
- Declaring Phase 1 complete (`WF-008`).

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Retains responsibility for this phase. `AGENTS.md` §10 records that there is no dedicated Planning Agent and that the Software Architect assumes Planning and Scope activities. Defines the deliverable set, commissions research, forms recommendations, reviews drafts, judges blocking status, and presents decisions to the human user. Writes no files. |
| **Documentation Agent** | Drafts the authorized deliverables under `docs/01-planning/`, applies the templates and standard, records classification and approval status, and reports material changes. Writes only the files named in its authorization. |
| **Research Agent** | Read-only. Investigates feasibility, cost, licensing, vendor capability, and market/technical alternatives when assigned. Supplies evidence, limitations, and alternatives; makes no decisions. |
| **Validation Agent** | Read-only. Independently reviews the deliverables for completeness, consistency, feasibility, and evidence quality when assigned. Cannot approve scope, budget, or priorities. |
| **Human user / stakeholder** | Approves the project, scope, budget, priorities, schedule commitments, and acceptance of key assumptions. Designates authoritative stakeholders where the stakeholder set is contested. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- Explicit human authorization to begin Phase 1, recorded with its scope.
- An approved Project Brief is a **MUST** precondition for Phase 1. It is produced through [`project-brief.md`](../templates/project-brief.md) and carries the approver and the approval date. Without an approved brief, Phase 1 drafting **MUST NOT** begin, and this workflow provides no exception: the precondition is unconditional. Where `WF-001` was not run — for example on a resumed, re-baselined, or separately authorized engagement — an equivalent brief approved by the human user is still required before Phase 1 drafting begins, produced through the same template with its approver and date recorded. A missing brief is a blocker (§14.5) presented to the human user, not an `OPEN QUESTION` that permits drafting to proceed.
- The initiation audit and work plan are available as persisted records under `docs/00-project-management/` — produced by `WF-001`, or an equivalent documented statement of available material, gaps, and contradictions where `WF-001` was not run. The Phase 1 authorization record from `WF-001` is required where it exists.
- Agreement on which original material is authoritative where sources conflict.
- The Documentation Agent has read `documentation-standards.md` and the relevant templates before drafting.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Phase 1 authorization | Human user, recorded by the Software Architect | **MUST** | Identifies deliverable scope and any exclusions. Persisted under `docs/00-project-management/`; a verbal authorization that was never recorded is not a sufficient input. |
| Approved Project Brief | `WF-001` output, or an equivalent approved brief where `WF-001` was not run; persisted under `docs/00-project-management/` | **MUST** | Unconditional: no Phase 1 drafting begins without it (§6.1). Approval recorded with approver and date. It establishes the problem, objectives, preliminary scope, constraints, and integrations that Phase 1 elaborates. |
| Initiation audit and work plan | `WF-001` outputs, or an equivalent documented statement of available material, gaps, and contradictions where `WF-001` was not run; persisted under `docs/00-project-management/` | **MUST** | Required as persisted records. Persistence is not optional, and an absent record is a defect to be reported, not a condition to be assumed away. The equivalent path relaxes neither persistence nor the duty to state gaps and contradictions. |
| Original project material | `input/existing-documentation/` | **SHOULD** | Read-only; referenced rather than restated. |
| Business objectives and constraints | Project Brief, and the human user via the Software Architect | **MUST** | Must be attributable, not inferred. |
| Research findings | Research Agent, via `WF-005` | **SHOULD** | Required for feasibility, cost, and technology claims. |
| Capability assessment | Software Architect, under `WF-010` | **MAY** | Required where a planning decision depends on which OpenCode mechanism is appropriate; it informs a decision and installs nothing. |
| Templates | `framework/templates/` | **MUST** where a template exists | Deviation is recorded with its reason. |
| Prior approved decisions | Any `DEC-NNN` register entries | **MUST** be respected | A conflict is escalated, not overwritten. |

---

## 7. Workflow Steps

1. **Confirm the authorization and the Project Brief.** The Software Architect restates which Phase 1 deliverables are authorized, in which order, and with what constraints, and confirms that an approved Project Brief exists, naming its version and approval date. If no explicit Phase 1 authorization exists, stop and obtain it (`WF-008`). If no approved brief exists, stop: return to `WF-001`, or obtain an equivalent approved brief through the same template where `WF-001` was not run. The gate is unconditional — a missing brief blocks Phase 1 drafting and is reported to the human user, not recorded as an open question that drafting proceeds around.
2. **Decide deliverable applicability.** For each of the eight Phase 1 deliverables, record `Applicable`, `Applicable in reduced form`, or `Not applicable — reason`. Applicability is the Software Architect's proposal to the human user, not an agent's unilateral narrowing of scope.
3. **Identify the decision points.** List the decisions this phase must present for approval: project go-ahead, scope boundaries, budget, priorities, schedule commitments, acceptance of material assumptions, and stakeholder authority. Each decision names its approver.
4. **Commission research.** Where feasibility, cost, licensing, or technical viability claims are needed, the Software Architect defines the research question, scope, and evidence threshold, and assigns it to the Research Agent under `WF-005`. Research is not commissioned to confirm a preferred answer. Where the question concerns which OpenCode mechanism is appropriate — a Skill, Command, agent, MCP server, or Plugin — `WF-010` governs the decision framework, the comparison criteria, and the version stamp for every capability claim. This workflow records the resulting recommendation as an input to a planning decision; it neither installs nor configures anything.
5. **Evaluate research findings.** The Software Architect assesses evidence quality and limitations, separates documented capability from vendor claim and inference, and identifies what remains unverified. Findings that are insufficient are returned as new questions, not accepted as conclusions.
6. **Form recommendations.** For each decision point, the Software Architect defines viable alternatives, compares advantages and disadvantages, identifies costs, risks, and dependencies, recommends an option, and records the reasoning. Recommendations remain `RECOMMENDATION` until approved.
7. **Issue the drafting assignment.** The Software Architect authorizes the Documentation Agent under `WF-006` with an explicit list of files under `docs/01-planning/`, the deliverable for each file, the inputs to use, and any constraints. A general instruction to "write the planning documents" is not a sufficient authorization.
8. **Draft in dependency order.** Production normally proceeds: Project Charter, then Scope Statement, then Stakeholder Analysis, then Feasibility Study, then Budget Estimate, then Project Roadmap, then Risk Register, then Assumptions Register. The Software Architect may reorder; the dependency reason is recorded.
9. **Classify every statement whose certainty matters.** Objectives, boundaries, stakeholders, costs, dates, constraints, and success criteria are labeled `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`. A cost is never presented as confirmed without an approved quotation or recorded decision, and a target date is labeled as a target rather than a commitment (`documentation-standards.md` §4).
10. **Assemble registers once.** Risks, assumptions, and open questions are recorded in a single authoritative register per type, with stable identifiers, and referenced from the documents that depend on them. Duplicate registers with divergent content are a defect.
11. **Check internal consistency.** The Software Architect compares the charter's scope summary against the scope statement, the budget against the feasibility study, the roadmap against stated dependencies, and the risk register against feasibility limitations. Disagreements are recorded as conflicts for the Software Architect, not aligned silently.
12. **Review and consolidate.** The Software Architect reviews each draft against the standard's completion criteria and returns corrections with precise references. Review comments are addressed only through an authorized documentation assignment.
13. **Obtain independent validation** for the deliverables the Software Architect designates as important, under `WF-007`. Validation is performed before the deliverables are presented as decision-ready.
14. **Apply authorized corrections.** Corrections that do not alter approved decisions are handled as documentation production (`WF-006`). Corrections that would alter an approved boundary, budget figure, or priority follow `WF-009`.
15. **Present the decisions.** Under `WF-008`, the Software Architect presents each decision with context, alternatives, consequences, recommendation, unresolved findings, and the current approval status. Scope, budget, and priority decisions **MUST** be presented for human approval.
16. **Record the outcome.** The Documentation Agent records the decision, approver, date, conditions, and evidence in the affected documents under an authorized write assignment. A recommendation that was not approved stays `RECOMMENDATION` and is described as such.
17. **Prepare the phase-gate proposal.** The Software Architect assembles the phase completion summary for `WF-008`: deliverables produced, validation performed, findings resolved or open, assumptions and open questions, and approvals obtained.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Research Agent | Feasibility, cost, licensing, and technology-capability questions. | One question set per assignment, with scope, exclusions, and evidence threshold. Read-only. |
| Software Architect | Documentation Agent | Draft or revise named Phase 1 files. | Explicit file list; `docs/01-planning/` only; templates applied; classification recorded. |
| Software Architect | Validation Agent | Independent review of designated Phase 1 deliverables. | Read-only; findings with severity and paths; cannot approve scope or budget. |
| Documentation Agent | Software Architect | Draft completion report and material-change report. | Reports what was written, what was assumed, what remains open, and what requires approval. |
| Research Agent | Software Architect | Research report with sources, limitations, alternatives, and confidence. | Does not write files and does not recommend an option as a decision. |
| Validation Agent | Software Architect | Findings and a phase-gate recommendation. | Recommendation only; cannot waive approvals or declare the phase complete. |

The Documentation Agent does not delegate work, does not request research directly, and does not decide scope. The Research Agent does not edit deliverables. The Validation Agent does not correct its own findings.

Where a feasibility or technology question is in substance a question about which OpenCode mechanism to use, the Software Architect handles it under `WF-010` rather than resolving it inside this workflow. The outcome is a recommendation presented to the human user; any installation or configuration is separate, requires explicit human authorization, and is outside both workflows.

---

## 9. Expected Outputs

| Output | Path (when persisted) | Status on production |
| --- | --- | --- |
| Project Charter | `docs/01-planning/project-charter.md` | `Draft` until reviewed; `Approved` only with recorded human approval. |
| Scope Statement | `docs/01-planning/scope-statement.md` | As above. |
| Stakeholder Analysis | `docs/01-planning/stakeholder-analysis.md` | As above. |
| Feasibility Study | `docs/01-planning/feasibility-study.md` | As above; conclusion is a recommendation until approved. |
| Budget Estimate | `docs/01-planning/budget-estimate.md` | As above; figures classified and sourced. |
| Project Roadmap | `docs/01-planning/project-roadmap.md` | As above; dates labeled as targets unless committed. |
| Risk Register | `docs/01-planning/risk-register.md` | As above; each risk has likelihood, impact, response, owner, status. |
| Assumptions Register | `docs/01-planning/assumptions-register.md` | As above; each assumption has basis, impact if wrong, and verification path. |
| Research reports (if persisted) | `docs/04-research/` | Persisted report; content not approved by persistence. |
| Validation reports (if persisted) | `docs/05-validation/` | Persisted report; findings not resolved by persistence. |
| Phase 1 completion summary | Presented by the Software Architect; persisted only if authorized | `RECOMMENDATION` until the phase gate is decided. |

File names are indicative: the authorization names the actual paths, and the project may use different names provided they follow `documentation-standards.md` §3.1.

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Project Brief template | [`framework/templates/project-brief.md`](../templates/project-brief.md) | Precondition input: the approved intake record that supplies the problem, objectives, preliminary scope, constraints, and integrations Phase 1 elaborates. |
| Project Charter template | [`framework/templates/project-charter.md`](../templates/project-charter.md) | Primary structure for objectives, stakeholders, success criteria, budget, milestones, assumptions, risks, and approval status. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Boundaries, deliverables, constraints, dependencies, and scope-level acceptance criteria. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | Criteria-first comparison of alternatives across technical, economic, operational, and schedule dimensions. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Persisted research evidence used by the feasibility and budget work. |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Persisted independent review of Phase 1 deliverables. |
| Documentation Standards | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Classification, identifiers, evidence, metadata, versioning, and completion criteria. |
| Scope Statement §2.3 | `docs/01-planning/scope-statement.md` §2.3 | Records how scope changes are requested and approved. This workflow requires that the recorded process follow `WF-009`; it does not replace the project's own record of who evaluates and who approves a scope change. |

**Template availability (observed 2026-11-10).** Templates exist for the Project Charter, Scope Statement, and Feasibility Study, and for the Project Brief. The Project Brief template is used as a precondition input, not as a Phase 1 deliverable. No template exists for a Stakeholder Analysis, a standalone Budget Estimate, a Project Roadmap, a Risk Register, or an Assumptions Register; the charter and scope templates carry partial sections for budget, milestones, risks, and assumptions. The Documentation Agent **MUST** apply `documentation-standards.md` §3 to those artifacts and **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Template compliance | Documentation Agent, reviewed by the Software Architect | Each deliverable follows its template or records a justified deviation. |
| Classification completeness | Documentation Agent | Every cost, date, boundary, stakeholder claim, and success criterion carries a label. |
| Evidence for figures | Documentation Agent | Cost, schedule, and capability statements cite a basis; unsourced figures are `ASSUMPTION` or `OPEN QUESTION`. |
| Single authoritative register | Software Architect | Risks, assumptions, and open questions are not duplicated across documents with divergent content. |
| Cross-document consistency | Software Architect | Charter, scope, feasibility, budget, and roadmap agree, or the disagreement is recorded as a conflict. |
| Approval-status honesty | Documentation Agent | No document describes itself as approved without a recorded human approval. |
| Independent validation | Validation Agent, under `WF-007` | Required for deliverables the Software Architect designates as important; findings recorded with severity and status. |
| Phase-gate separation | Software Architect | Document completeness is never presented as phase completion. |

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Whether to proceed with the project | Human user | After the charter and feasibility study are decision-ready | No downstream phase may rely on project approval before it is recorded. |
| Scope boundaries, including exclusions | Human user | After the scope statement is reviewed | A boundary excluded by decision differs from one merely absent; only a decision makes it out of scope. |
| Budget and cost commitments | Human user | After the budget estimate and feasibility economics are reviewed | No figure is `CONFIRMED` without approval; no agent commits cost. |
| Business priorities and success criteria | Human user | After objectives and success criteria are proposed | Priorities rank the work; agents may propose, not set, them. |
| Schedule commitments | Human user | After the roadmap is proposed | Target dates remain targets until committed. |
| Acceptance of material assumptions | Human user, with the Software Architect's recommendation | Before a decision depends on them | Accepted assumptions remain assumptions with their authority recorded. |
| Stakeholder authority | Human user | Where the decision-making stakeholder is contested | Agents do not assign decision authority to a stakeholder. |
| Phase 1 completion | Human user, on the Software Architect's gate proposal | After all Phase 1 exit criteria are verified | Handled by `WF-008`, not by this workflow. |

---

## 13. Completion Criteria

Phase 1 work under this workflow is complete when all of the following hold:

- [ ] Authorization for the Phase 1 work existed and is recorded.
- [ ] An approved Project Brief exists, with approver and date recorded, whether produced through `WF-001` or as an equivalent approved brief, and no Phase 1 deliverable was drafted before that approval.
- [ ] The initiation audit and work plan are available as persisted records under `docs/00-project-management/` — from `WF-001` or an equivalent documented statement of available material, gaps, and contradictions where `WF-001` was not run.
- [ ] Deliverable applicability was decided for all eight Phase 1 deliverables, with reasons for exclusions.
- [ ] Each applicable deliverable exists, follows the standard's metadata and structure rules, and carries accurate status.
- [ ] Every cost, date, boundary, and success criterion is classified and sourced.
- [ ] Risks, assumptions, and open questions are recorded in single authoritative registers with owners and status.
- [ ] Cross-document consistency has been checked and conflicts are recorded rather than reconciled.
- [ ] Independent validation has been performed for the deliverables the Software Architect designated, and findings have a recorded status.
- [ ] All decisions requiring human approval are presented and their outcomes recorded, including conditions.
- [ ] The phase completion summary has been presented and the phase-gate decision recorded.
- [ ] No application implementation, code, or privileged file modification occurred.

Meeting these criteria is the basis for a phase-gate proposal. It is not a phase completion until the decision in `WF-008` is recorded.

---

## 14. Exception Handling

### 14.1 Insufficient information

Do not invent objectives, stakeholders, costs, dates, or constraints. Record the gap as `OPEN QUESTION` with an owner and the decision it blocks; where a planning decision must proceed, record the `ASSUMPTION` with its basis, impact if wrong, and verification path. The Software Architect decides whether the phase can proceed with the gap open.

### 14.2 Contradictions

Contradictions between original material, between deliverables, or between a deliverable and an approved decision are recorded with both locations and escalated. Where the contradiction concerns scope, the scope statement's conflict table is used. Agents do not choose a winner.

### 14.3 Findings from independent validation

Findings are handled under `WF-007`. The Software Architect evaluates each finding, decides whether a correction is requested, and authorizes the Documentation Agent. A finding is not closed because a correction was drafted, described, or promised.

### 14.4 Missing research or weak evidence

Where research is unavailable, incomplete, or based only on vendor claims, the affected conclusion is downgraded to `ASSUMPTION` or `OPEN QUESTION` and the limitation is disclosed. The feasibility study's recommendation section states the conditions under which the recommendation holds.

### 14.5 Blockers

A blocker is a decision or piece of information without which a required decision cannot be made responsibly. The Software Architect designates blockers, records them, and presents them to the human user. This workflow pauses at a blocker; it does not proceed on a provisional scope or budget.

### 14.6 Changes to already approved content

Any change to an approved scope boundary, budget figure, priority, or success criterion follows `WF-009`. The Documentation Agent may not amend approved content under a drafting assignment.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-002-01` | Which Phase 1 artifacts require their own templates (stakeholder analysis, budget estimate, roadmap, risk register, assumptions register)? | Without templates, structure depends on each project's judgment and is harder to review consistently. | Software Architect |
| `OQ-WF-002-02` | Where should the single project-wide risk and assumption sequences be registered when several Phase 1 documents hold entries? | Duplicate identifier risk across charter, scope statement, and feasibility study. | Software Architect |
| `OQ-WF-002-03` | Is a separate phase-gate checklist artifact expected, or is the completion summary in the Architect's report sufficient? | Affects whether the gate evidence is persisted and reviewable. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | Predecessor: supplies the audit, gaps, contradictions, and the work plan this phase executes. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Successor phase: consumes the approved scope and objectives. |
| [`WF-005` — Research](./research.md) | Invoked for feasibility, cost, licensing, and technology-capability evidence. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked for every authorized draft or revision of a Phase 1 file. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked before deliverables are presented as decision-ready. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs the approval of scope, budget, and priorities, and the Phase 1 gate. |
| [`WF-009` — Change Control](./change-control.md) | Invoked for any change to an approved Phase 1 decision or baseline. |
| [`WF-010` — Technology Capability Assessment](./technology-capability-assessment.md) | Invoked when a feasibility or technology question turns on which OpenCode mechanism is appropriate; it recommends, and this workflow neither installs nor configures anything. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the Planning and Scope workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable Phase 1 procedure that keeps evidence, recommendations, and human decisions separate. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.2.0 | 2026-11-10 | Consolidated revision under Software Architect authorization: the approved Project Brief is now a mandatory Phase 1 precondition (§6.1, §6.2, §7 step 1, §13); the initiation audit, work plan, and Phase 1 authorization record are required as persisted records rather than "in substance" only (§6.2); `WF-010` is referenced for capability and technology-mechanism questions (§4.1, §7 step 4, §8, §10, §15); the Project Brief template is listed as a precondition input. | Apply the intake-to-planning gate and mandatory persistence requirements (DIAG-002) and align Phase 1 with the capability-assessment workflow. Versioning: MINOR (additive new stages, procedures, and requirements; no previously approved decision, boundary, or baseline is altered or superseded). | Documentation Agent | Approved by Human user on 2026-11-10. |
