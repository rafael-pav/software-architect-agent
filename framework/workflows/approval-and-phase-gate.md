# Workflow WF-008 — Approval and Phase Gate

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-008` |
| Workflow name | Approval and Phase Gate |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-008` |
| Purpose | Define how decisions are prepared for human review, how the human decision is obtained and recorded without inference, and how a lifecycle phase is verified and closed only through an explicit phase-gate decision that is distinct from approving a deliverable. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Every decision that requires human approval, every phase transition, and every gate proposal in the three supported lifecycle phases. |
| Related workflows | `WF-001`, `WF-002`, `WF-003`, `WF-004` (phase workflows), `WF-005` (research), `WF-006` (documentation production), `WF-007` (independent validation), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§7, 8, 10, 13; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§8.3, 8.5, 9.2; [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) §§6, 9; [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) §7 (required report structure) and the section titled *Restrictions on approvals*. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Decision identifiers use `DEC-NNN` as established by the project decision register convention; `VAL`, `ASM`, `OQ`, `RISK`, `ADR`, and `AC` keep the meanings given by the template or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines the boundary between agent work and human authority. Everything before the boundary is preparation: analysis, alternatives, evidence, recommendations. The boundary itself is a decision that only the human user can make, and it is valid only if it is explicit, attributable, and recorded.

The workflow also enforces a distinction that is frequently lost: approving a deliverable is not the same as approving a phase transition. A charter can be approved while Phase 1 remains open; a phase can be judged ready while an individual document remains in review. Each is decided, and recorded, separately.

---

## 3. Trigger / When to Use

Use this workflow when:

- A decision reserved to the human user is ready for decision: project go-ahead, scope, budget, priorities, requirements, security and privacy, technology selection, architecture, or a change to a previously approved deliverable.
- A lifecycle phase is being proposed for completion.
- A previously approved decision must be revisited, suspended, or superseded.
- A validation outcome is being converted into a gate proposal.

Do not use this workflow to solicit a vague endorsement of work in progress. A decision package that does not state what is being decided, what the alternatives are, and what remains unresolved is not ready to be presented.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Identifying which decisions require human approval and who holds the authority.
- Preparing decision packages: context, alternatives, consequences, recommendation, unresolved findings, and current status.
- Presenting decisions in the language required by the language policy.
- Obtaining and recording explicit decisions, including conditions and refusals.
- Verifying phase exit criteria and assembling a phase completion summary.
- Recording deliverable approval and phase-gate approval separately.
- Recording authorization for the next phase or for a subsequent activity.

### 4.2 Deliberately excluded

- Deciding on the human user's behalf, including by inference, by default, or by proceeding.
- Presenting a recommendation as a decision.
- Presenting an approved decision as one that was merely discussed.
- Treating an ambiguous or conditional reply as an unqualified approval.
- Closing a phase because its documents exist.
- Overriding or omitting validation findings in the presentation.
- Recording an approval without an identifiable approving role and date.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Prepares and presents decisions; states alternatives, consequences, recommendation, and unresolved items; verifies exit criteria; records the decision as reported; requests the next authorization. Does not decide and does not write files. |
| **Documentation Agent** | Records approved outcomes in the affected documents under an explicit write assignment, using the mandatory status vocabulary, and records the change in the affected change histories. Does not decide or infer approval. |
| **Validation Agent** | Supplies the validation findings and gate recommendation that the decision package must reflect. Cannot approve, waive, or complete a phase. |
| **Research Agent** | Supplies evidence relevant to the decision where assigned. Read-only; makes no recommendation that is presented as a decision. |
| **Human user / stakeholder** | Holds the decision. States the decision, any conditions, and any refusal. May delegate decision authority explicitly; a delegated authority is recorded, not assumed. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- The decision has been identified as one reserved to the human user, or the phase has been proposed for completion.
- The material supporting the decision is available at known versions.
- Required independent validation has been performed where the matter is important, or its absence is stated in the package.
- The Software Architect has verified the current approval status of the documents involved, rather than trusting an earlier report.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Decision statement: what exactly is being decided | Software Architect | **MUST** | One decision per presentation, or clearly separated decision items. |
| Alternatives and consequences | Software Architect, with research evidence | **MUST** | Including the consequence of not deciding. |
| Recommendation and reasoning | Software Architect | **MUST** | Explicitly a recommendation pending decision. |
| Validation findings and recommendation | Validation Agent | **MUST** where validation was performed | Presented as reported, including severity. |
| Open questions, assumptions, and risks | Phase registers | **MUST** | Including which are blocking, as judged by the Software Architect. |
| Phase exit criteria | `AGENTS.md` §10 and the phase workflow | **MUST** for gate decisions | The basis for the gate verification. |
| Decision authority | Human user, as established for the project | **MUST** | The approver must be identifiable. |
| Prior approvals and their conditions | Decision register, document metadata | **MUST** | Prior conditions are checked before new approval is requested. |

---

## 7. Workflow Steps

1. **Classify the decision.** Determine whether the matter is a deliverable approval, a decision within a phase, a phase transition, a change to previously approved content, or an authorization to start an activity. The classification determines the criteria and the record required.
2. **Identify the decision owner.** Name the human role with authority for this class of decision. Where authority is unclear or contested, that ambiguity is itself the decision to be resolved first; it is not resolved by assuming the most likely owner.
3. **Verify the current state before presenting.** Re-read the status of the affected documents, confirm the validation state, and confirm that prior conditions were met or are still open. A package built on an outdated status misleads the approver.
4. **Assemble the decision package.** Include: the decision statement; the context that makes it necessary; viable alternatives including not deciding; advantages, disadvantages, costs, risks, and dependencies; the recommendation and its reasoning; validation findings with severity and status; open questions and assumptions with their effect; and the current approval status of the material.
5. **State what is not settled.** Unresolved findings, unverified assumptions, and open questions are presented explicitly with their effect on the decision. Presenting a decision as cleaner than the evidence allows is a misrepresentation.
6. **Present in the required language.** The presentation follows the language used by the human user, per the language policy, and follows the structure: current situation, findings, risks and limitations, recommendations, pending decisions, next actions.
7. **Request the decision explicitly.** State the decision requested, the options available, and what each option authorizes. Do not phrase the request so that silence, a question, or a request for more information can be read as consent.
8. **Receive the response and check its explicitness.** A response is an approval only if it identifies the decision, indicates acceptance, and is attributable to the authority identified in step 2. Questions, requests for changes, expressions of interest, and conditional statements are not approvals.
9. **Resolve ambiguity by asking.** Where the response is ambiguous or conditional, restate the decision and the proposed reading ("you are approving X subject to Y — is that correct?") and wait. The agent **MUST NOT** proceed on the more convenient interpretation.
10. **Record the decision.** Record: decision identifier (`DEC-NNN`), what was decided, deciding role, date, conditions, basis or evidence reference, and status (`Approved`, `Rejected`, `Deferred`, `Superseded`). Record refusals and deferrals with their reasons; a refused decision is a decision.
11. **Distinguish deliverable approval from phase approval.** If a deliverable was approved, record that approval on the deliverable only. Phase status changes only through the gate decision in steps 15 to 18.
12. **Authorize the documentation update.** The Software Architect authorizes the Documentation Agent under `WF-006` to record the outcome in the named documents: metadata approval fields, decision registers, and change histories. The Documentation Agent does not decide what the outcome was.
13. **Update statuses honestly.** Document status moves to `Approved` only where human approval was recorded and no blocking validation finding remains. A document that was approved with conditions records the conditions rather than appearing unqualified.
14. **Track conditions.** Each condition attached to an approval is recorded with an owner, a due point, and a status. Conditions are not treated as satisfied because the approval was granted.
15. **Prepare the phase-gate proposal.** For a phase transition, verify each exit criterion and record the evidence for it: deliverables present, validation performed, critical inconsistencies resolved, assumptions and open questions documented, and required approvals obtained.
16. **Present the gate proposal separately.** The gate package states which phase is proposed for completion, the exit criteria and their verification, the open findings and their severity, the tracked conditions, and the outstanding assumptions and open questions. It names the decision requested: that the phase be considered complete and that the next phase be authorized, or not.
17. **Obtain the gate decision explicitly.** The human user decides. A gate decision that is not explicit is recorded as pending; the phase remains open and no next-phase work begins.
18. **Record the gate outcome.** Record the phase, the decision, the deciding role, the date, the conditions, and the basis. Record the authorization for the next phase, or the decision not to authorize it, with reasons.
19. **Publish the phase completion summary.** State what was produced, what was validated, what remains open, and what was approved — without implying that approval covers anything beyond its stated scope.
20. **Hand over.** Where the next phase is authorized, hand to `WF-002`, `WF-003`, or `WF-004` as appropriate, with the recorded authorization as its precondition. Where changes are required before a gate can pass, hand to `WF-009`.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Validation Agent | Provide the findings and gate recommendation for the decision package. | Read-only; recommendation only; no approval authority. |
| Software Architect | Research Agent | Provide evidence relevant to a pending decision. | Read-only; findings returned to the Architect. |
| Software Architect | Human user | Present the decision package and request the decision. | Alternatives, consequences, recommendation, and unresolved items must be stated. |
| Software Architect | Documentation Agent | Record the decision in named documents. | Explicit file list; the outcome as reported; status vocabulary from the standard. |
| Documentation Agent | Software Architect | Confirm what was recorded and flag anything that could not be recorded as instructed. | Must not upgrade or infer an approval. |

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Decision package | Software Architect | Context, alternatives, consequences, recommendation, findings, open items, current status. |
| Decision record | Software Architect, then documented by the Documentation Agent | `DEC` entry with statement, approver, date, conditions, basis, and status. |
| Updated document status | Documentation Agent | Approval fields and change histories reflecting the recorded outcome. |
| Condition tracker | Software Architect | Conditions with owners, due points, and status. |
| Phase-gate proposal | Software Architect | Exit criteria, verification evidence, open findings, tracked conditions, and the decision requested. |
| Phase-gate record | Software Architect, then documented by the Documentation Agent | Phase, decision, approver, date, conditions, and next-phase authorization. |
| Phase completion summary | Software Architect | What was produced, validated, approved, and left open. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Project Charter template | [`framework/templates/project-charter.md`](../templates/project-charter.md) | §11 carries the decisions and approval-status statement for the project. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | §10 records scope decisions and which boundaries remain proposals. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | §12 records the recommendation and its approval status. |
| Software Requirements Specification template | [`framework/templates/software-requirements-specification.md`](../templates/software-requirements-specification.md) | §12 records requirement and priority decisions. |
| Architecture Overview template | [`framework/templates/architecture-overview.md`](../templates/architecture-overview.md) | §12 records which parts of the architecture are accepted. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | §12 approval record and §1 decision status. |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | §7 gate recommendation that the gate package must reflect. |
| Requirements Traceability Matrix template | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | §10 records matrix status and explicitly defers the phase gate to the Software Architect. |

**Template availability (observed 2026-11-10).** No template exists for a decision package, a phase-gate proposal, a phase completion summary, or a condition tracker. Decision and approval-status sections exist within the templates listed above. The Documentation Agent **MUST** apply `documentation-standards.md` §3 where persistence is authorized and **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Decision classification | Software Architect | Each presentation states what class of decision is requested. |
| Authority identification | Software Architect | The decision owner is named; unresolved authority is escalated, not assumed. |
| State verification | Software Architect | Current document and validation status is re-read before presentation. |
| Findings presented as reported | Software Architect | Severity and status are not softened, merged, or omitted. |
| Recommendation labelled | Software Architect | A recommendation is never phrased as a decision. |
| Explicitness test | Software Architect | Approval requires an identifiable acceptance by the identified authority; ambiguity is resolved by asking. |
| Record completeness | Software Architect, Documentation Agent | Approver, date, scope, conditions, basis, and status are recorded. |
| Separation of approvals | Software Architect | Deliverable approval and phase approval are recorded as separate decisions. |
| Exit-criteria verification | Software Architect | Each criterion has recorded evidence, not an assertion. |
| Status honesty | Documentation Agent | `Approved` is used only where approval is recorded and no blocking findings remain. |

---

## 12. Human Approval Points

This workflow exists to serve these decisions; each is reserved to the human user and none may be inferred.

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Project go-ahead | Human user | After the Phase 1 decision package | No phase work proceeds without it. |
| Scope boundaries | Human user | Phase 1 and on any scope change | Exclusions become binding only by decision. |
| Budget and costs | Human user | Phase 1 and on any cost-affecting change | No agent commits or approves expenditure. |
| Business priorities | Human user | Phase 1 and Phase 2 | Priorities order the work; agents do not set them. |
| Functional requirements and business rules | Human user | Phase 2 | Requirements remain proposed until approved. |
| Security and privacy requirements, including residual risk | Human user | Phase 2 and Phase 3 | Agents may not accept security risk on the user's behalf. |
| Technology selection and architecture decisions | Human user | Phase 3 | Decisions remain `Proposed` until approved. |
| Changes to previously approved deliverables | Human user | Whenever proposed, under `WF-009` | The change is authorized before it is executed. |
| Approval of an individual deliverable | Human user | As each deliverable becomes decision-ready | Applies only to that deliverable. |
| Phase completion and next-phase authorization | Human user | At each phase gate | Applies only to the named phase and the named next activity. |

---

## 13. Completion Criteria

A decision cycle under this workflow is complete when all of the following hold:

- [ ] The decision class and the decision owner were identified.
- [ ] The current status of the affected documents and validation findings was verified before presentation.
- [ ] The package stated context, alternatives, consequences, recommendation, findings, and unresolved items.
- [ ] The decision was presented in the required language and in an explicit-decision form.
- [ ] The response was unambiguous, or ambiguity was resolved by asking.
- [ ] The decision was recorded with identifier, statement, approver, date, conditions, basis, and status.
- [ ] Deliverable approval and phase approval were recorded as distinct decisions.
- [ ] Conditions were recorded with owners and status.
- [ ] Document status reflects the recorded decision, and no document claims an approval that did not occur.
- [ ] For a gate: every exit criterion was verified with evidence, and blocking findings were resolved or explicitly tracked.
- [ ] The phase completion summary was presented, and the next-phase authorization was recorded or refused.

---

## 14. Exception Handling

### 14.1 No response or a silent approver

Absence of a response is not approval. The decision remains pending, the phase remains open, and the next activity does not start. The Software Architect records the pending decision and re-presents it when the approver is available.

### 14.2 Ambiguous or conditional responses

Restate the decision and the proposed reading, and wait for confirmation. A conditional statement is recorded as an approval with conditions only after the condition's meaning is confirmed; otherwise it is recorded as `Deferred` with the open point stated.

### 14.3 Approval requested for material with open blocking findings

Present the findings and the fact that they are blocking. Do not propose a deliverable as approvable while a critical or high finding remains unresolved; if the user wishes to accept the risk, that acceptance is recorded explicitly as a risk acceptance, with its authority and consequence.

### 14.4 Authority unclear or contested

If no one can be identified as holding the decision authority, record that as the blocking question. Do not assign authority by seniority, by role title, or by whoever responded first.

### 14.5 Decision reversed after being recorded

Record the reversal as a new decision with its own identifier, date, and reason; mark the earlier decision `Superseded` and keep it visible. Downstream documents affected by the reversal are updated under `WF-009`, not silently.

### 14.6 Pressure to proceed without a decision

A request to begin the next phase, or to describe work as approved, without an explicit decision is refused and escalated. The refusal, and the request, are recorded. Neither an agent's confidence nor the completeness of the documents substitutes for the decision.

### 14.7 Validation incomplete

Where validation was required but incomplete, the gate proposal states that. A gate decision taken on incomplete validation is recorded as such, with the missing review named, so that it is not later mistaken for a validated pass.

### 14.8 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-008-01` | Should a phase-gate checklist be a persisted project artifact, and if so where? | Gate evidence currently exists only in the Architect's presentation and in individual documents. | Software Architect |
| `OQ-WF-008-02` | How should a decision taken verbally or in conversation be recorded so that it is attributable and durable? | The standard requires an approver and date; the recording medium is unspecified. | Software Architect |
| `OQ-WF-008-03` | Is a "PASS WITH CONDITIONS" validation recommendation treated as a gate passed with tracked conditions, or as a gate deferred? | Affects whether a phase can close while non-blocking conditions remain. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | Its work plan and first-phase authorization are decisions processed here. |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Produces the scope, budget, and priority decisions presented here. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Produces the requirement, priority, and security decisions presented here. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Produces the technology and architecture decisions presented here. |
| [`WF-005` — Research](./research.md) | Supplies evidence used in the decision package. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Records the outcome in the affected documents. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Supplies the findings and gate recommendation the package must reflect. |
| [`WF-009` — Change Control](./change-control.md) | Handles changes required before a gate can pass, and changes to any approved decision. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the approval and phase-gate workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a procedure that requires explicit human decisions, separates deliverable approval from phase transition, and never infers approval. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
