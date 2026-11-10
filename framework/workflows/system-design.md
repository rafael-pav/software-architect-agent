# Workflow WF-004 — System Design and Architecture

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-004` |
| Workflow name | System Design and Architecture |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-004` |
| Purpose | Define how Phase 3 (System Design and Architecture) documents architecture and design decisions — components, data, interfaces, integrations, security, user experience, and deployment — at a documentary level, with technology and architecture decisions reserved for human approval. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Phase 3 work on any project whose requirements set has been established or proposed in Phase 2. |
| Related workflows | `WF-003` (predecessor phase), `WF-005` (research), `WF-006` (documentation production), `WF-007` (independent validation), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§2, 6–7, 10, 13; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§4–9; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §7; [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) §§4.6–4.8. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `DRV`, `OPT`, `CMP`, `VAL`) keep the meanings given by the standard, template, or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines Phase 3: the production of architecture documentation that explains how the system is structured, why, and what consequences follow, and that records architecturally significant decisions as reviewable decisions rather than as prose embedded in diagrams.

Its boundary is documentary. The phase produces architecture descriptions, decision records, and specifications. It does not produce code, interface implementations, schemas as executable artifacts, infrastructure definitions, or deployment automation.

---

## 3. Trigger / When to Use

Use this workflow when:

- The human user has authorized Phase 3 work, normally after the Phase 2 requirements decision.
- An approved architecture must be extended or revised through an authorized change.
- Requirements analysis has revealed an architecturally significant constraint that must be evaluated before the requirement can be settled.

Do not use this workflow to implement, prototype, or validate an architecture by building it. Feasibility is established through research evidence and review, not through implementation.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Architecture Overview, including C4 context, container, and component views where they support review.
- Technology stack specification and technology comparisons, as recommendations pending approval.
- Data model and entity relationships at the conceptual and logical level, including ownership.
- API and interface contracts at the specification level.
- Integration specifications and boundary definitions.
- Security architecture, including control placement and residual risk.
- UX/UI specifications at the level required by the approved scope.
- Architecture Decision Records (`ADR`) for architecturally significant decisions.
- Deployment architecture at the structural level: environments, placement, operational constraints.

### 4.2 Deliberately excluded

- Any implementation: source code, executable specifications, prototypes, scripts, infrastructure definitions, configuration templates, database migrations, or automation.
- Approving technology selections or architecture decisions. These are human decisions presented by the Software Architect.
- New functional requirements. A design activity that exposes a requirement gap refers it back to `WF-003`.
- Performance or security claims presented as verified without evidence.
- Declaring Phase 3 complete (`WF-008`).

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns the phase. Identifies architecturally significant requirements and decisions, defines options, assesses trade-offs, commissions technical research, reviews drafts, judges blocking questions, and presents technology and architecture decisions to the human user. Writes no files. |
| **Documentation Agent** | Drafts the authorized architecture documents under `docs/03-architecture/`, applies the templates and standard, records classification, and maintains decision records and their traceability links. |
| **Research Agent** | Read-only. Investigates technology capability, version compatibility, licensing, integration constraints, security capability, and operational characteristics when assigned. Provides evidence with limitations; does not select technology. |
| **Validation Agent** | Read-only. Independently reviews architecture quality, feasibility, traceability, security, and consistency between diagrams and descriptions when assigned. |
| **Human user / stakeholder** | Approves technology selection, architecture decisions, security and privacy posture, and any change to an approved architecture. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- Explicit human authorization to begin Phase 3, or an authorized change scope covering the architecture work.
- A requirements baseline — approved, or explicitly proposed with its status recorded — including `NFR`, `SEC`, and `INT` entries.
- The Documentation Agent has read `documentation-standards.md` §§4–6 and the architecture overview and decision record templates.
- Approved Phase 1 constraints, including budget and organizational constraints that bound technology choice, are available.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Phase 3 authorization | Human user, recorded by the Software Architect | **MUST** | Identifies which architecture documents are in scope. |
| Requirements baseline | Phase 2 outputs | **MUST** | The architecture must state which requirements revision it responds to. |
| Scope boundaries and constraints | Phase 1 outputs | **MUST** | A design that contradicts an approved constraint is a defect, not an innovation. |
| Approved decisions | `DEC-NNN` register, prior `ADR` records | **MUST** be preserved | Superseded decisions remain visible with their replacement. |
| Technical research | Research Agent via `WF-005` | **SHOULD**, **MUST** for external capability claims | Version-specific and licensing claims require cited sources. |
| Validation findings | `docs/05-validation/` where persisted | **SHOULD** | Open findings constrain what may be presented as settled. |

---

## 7. Workflow Steps

1. **Confirm the authorization and the architecture scope.** The Software Architect states which documents are authorized, which requirements revision they respond to, and which aspects (data, integration, security, UX/UI, deployment) are deferred or excluded, with reasons.
2. **Identify architecturally significant requirements.** Select the `NFR`, `SEC`, `INT`, and constraint entries that materially shape structure or technology. Record the selection basis. A selection that omits an approved significant requirement is a defect.
3. **Identify the decisions that need records.** For each significant question, decide whether it warrants an `ADR`. Decisions that bind future work, are expensive to reverse, or trade off quality attributes require a record; routine choices generally do not.
4. **Commission technical research.** For each technology or integration question, the Software Architect defines the question, scope, comparison criteria, and evidence threshold, and assigns it to the Research Agent under `WF-005`. Criteria are defined before options are assessed.
5. **Define options and assess trade-offs.** For each decision, record drivers (`DRV`), options (`OPT`), advantages, disadvantages, risks, and the classification of each claim. Include the option of not changing the current state where relevant, and retain rejected options with the reason for rejection.
6. **Draft the decision record before the architecture description asserts the outcome.** Each `ADR` records context, problem, drivers, options, the proposed decision, rationale, consequences, and related requirements. A record that justifies a choice without stating alternatives is incomplete.
7. **Issue the drafting assignment.** The Software Architect authorizes the Documentation Agent under `WF-006` with an explicit list of files under `docs/03-architecture/`, the document type for each, the inputs, and constraints. No architecture file is created without that assignment.
8. **Draft the Architecture Overview.** Describe the system boundary, context, containers, and components that support a decision or a review; record responsibilities; identify which requirements each element serves. Keep diagrams reproducible from text and pair each with a textual description that can be reviewed without rendering.
9. **Specify data ownership and flows.** One authoritative owner per data entity. Consumers, sensitivity, and lifecycle basis are recorded where known; disputed ownership is recorded as a conflict rather than decided by the author.
10. **Specify integration boundaries.** For each `INT`, record participants, direction, mechanism or contract reference, data crossing the boundary, whether a trust boundary is crossed, and status. An undefined mechanism remains an `OPEN QUESTION`, never an implied design choice.
11. **Specify security architecture.** Map `SEC` requirements to controls, protected assets, boundaries, and residual risk. Regulatory or contractual obligations are cited or recorded as `OPEN QUESTION`; they are never asserted by an agent.
12. **Specify UX/UI requirements where in scope.** Record interaction, information, and accessibility requirements at the specification level required by the approved scope. Visual assets are described in reproducible text where possible.
13. **Specify deployment architecture structurally.** Record environments, placement of containers, and operational constraints at architectural level. Deployment procedures, scripts, and infrastructure implementation are out of scope and must not appear.
14. **Maintain traceability.** Link each `ADR` to the requirements or constraints it addresses, and mirror the links in the requirements traceability matrix. A decision with no supporting requirement or documented constraint is reported as a defect.
15. **Check consistency.** Diagrams against descriptions, components against responsibilities, data owners against consumers, security controls against `SEC` requirements, deployment statements against approved constraints. Conflicts are recorded, not silently corrected.
16. **Review internally.** The Software Architect reviews the documents against their purpose and returns precise corrections; implementation-level detail is removed.
17. **Obtain independent validation** under `WF-007` for the architecture documents designated as important, including technical feasibility and diagram/description agreement.
18. **Apply authorized corrections.** Editorial and clarifying corrections follow `WF-006`. Changes that would alter an accepted decision or approved architecture follow `WF-009` and are recorded as amendments or supersession, never as silent rewrites.
19. **Present the decisions.** Under `WF-008`, the Software Architect presents each technology and architecture decision with context, alternatives, consequences, recommendation, residual risks, and the current status. Technology selection and architecture decisions **MUST** be presented for human approval.
20. **Record approvals and decision status.** Approved decisions move from `Proposed` to `Accepted` only when the approval is recorded with approver and date. Superseded decisions remain visible and name their replacement.
21. **Prepare the gate proposal.** The Software Architect assembles the phase completion summary: documents produced, decisions accepted or pending, unresolved open questions, validation status, and residual risks.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Research Agent | Technology capability, compatibility, licensing, integration, and security-capability questions. | Criteria defined before assessment; version applicability stated; no recommendation presented as a decision. |
| Software Architect | Documentation Agent | Draft or revise named architecture files. | Explicit file list; `docs/03-architecture/` only; templates applied; no implementation artifacts. |
| Software Architect | Validation Agent | Independent review of architecture, feasibility, security, and traceability. | Read-only; findings with severity and paths; cannot approve technology or architecture. |
| Documentation Agent | Software Architect | Draft report: documents written, decisions recorded, defects and conflicts found, open questions. | Implementation detail discovered in a draft is removed and reported, not retained. |
| Research Agent | Software Architect | Findings, alternatives, limitations, and confidence. | Does not select technology and does not write architecture documents. |
| Validation Agent | Software Architect | Findings and a phase-gate recommendation. | Recommendation only. |

---

## 9. Expected Outputs

| Output | Path (when persisted) | Notes |
| --- | --- | --- |
| Architecture Overview | `docs/03-architecture/architecture-overview.md` | Context, container, and component views with textual descriptions; component register; data ownership; integration boundaries; security and deployment considerations. |
| Architecture Decision Records | `docs/03-architecture/` (one file per decision, or a register by project convention) | `ADR` identifiers unique and stable; decision status distinct from document status. |
| Technology stack specification | `docs/03-architecture/technology-stack.md` | Recommendations with evidence, limitations, and approval status. |
| Data model | `docs/03-architecture/data-model.md` | Conceptual and logical entities, relationships, ownership, sensitivity. |
| API contracts and integration specifications | `docs/03-architecture/` | Specification-level interface definitions; referenced from the architecture overview rather than duplicated. |
| Security architecture | `docs/03-architecture/security-architecture.md` | Controls mapped to `SEC` requirements, boundaries, residual risk. |
| UX/UI specifications | `docs/03-architecture/` where in scope | Interaction and accessibility requirements at specification level. |
| Deployment architecture | `docs/03-architecture/deployment-architecture.md` | Structural and environmental description only. |
| Updated traceability links | Requirements traceability matrix | Requirement-to-decision links added in Phase 3. |
| Phase 3 completion summary | Presented by the Software Architect | `RECOMMENDATION` until the gate decision. |

File names are indicative; the authorization names the actual paths, and naming follows `documentation-standards.md` §3.1.

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Architecture Overview template | [`framework/templates/architecture-overview.md`](../templates/architecture-overview.md) | Structure for context, containers, components, integration boundaries, data ownership, decisions, non-functional and security considerations, and deployment notes. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Structure for one decision: drivers, options, decision, rationale, consequences, traceability, approval record, amendment log. |
| Requirements Traceability Matrix template | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | Receives requirement-to-decision links and reports decisions without supporting requirements. |
| Software Requirements Specification template | [`framework/templates/software-requirements-specification.md`](../templates/software-requirements-specification.md) | Source of the requirements the architecture must satisfy. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Evidence structure for technology and integration findings. |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Persisted independent review of architecture deliverables. |
| Documentation Standards §§5–6 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Identifier and traceability rules that the architecture must respect. |

**Template availability (observed 2026-11-10).** Templates exist for the Architecture Overview and the Architecture Decision Record. No template exists for a technology stack specification, data model, API contract, integration specification, security architecture, UX/UI specification, or deployment architecture. The Documentation Agent **MUST** apply `documentation-standards.md` §3 to those artifacts and **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Requirements baseline stated | Documentation Agent | Every architecture document names the requirements revision it responds to. |
| Decision records complete | Documentation Agent, reviewed by the Software Architect | Context, alternatives, rationale, consequences, and approval status are present; rejected options are retained. |
| No implementation content | Documentation Agent, checked by the Validation Agent | No code, executable specification, script, infrastructure definition, or migration appears. |
| Diagram/description agreement | Documentation Agent, checked by the Validation Agent | Each diagram has a textual description that agrees with it; disagreements are recorded. |
| Single data owner | Documentation Agent | One authoritative owner per entity, or a recorded ownership conflict. |
| Evidence for capability claims | Documentation Agent | External capability, compatibility, and licensing claims cite a source and a version, or are classified as unverified. |
| Classification of proposals | Documentation Agent | Design proposals are `RECOMMENDATION` until accepted; accepted decisions cite their approval. |
| Traceability to requirements | Documentation Agent, checked by the Validation Agent | Each decision links to a requirement or documented constraint, or is reported as a defect. |
| Independent validation | Validation Agent, under `WF-007` | Feasibility, architecture quality, security, and consistency findings with severity and status. |

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Technology selection | Human user | After research and option comparison, before the architecture depends on it | Agents may recommend; they may not commit to a technology. |
| Architecture decisions | Human user | With the decision package for each significant `ADR` | A decision remains `Proposed` until approval is recorded. |
| Security and privacy posture, including residual risk acceptance | Human user | Before the architecture is presented as satisfying `SEC` requirements | An agent may not accept residual risk on the user's behalf. |
| Data ownership and retention decisions where the organization is affected | Human user | Before the architecture asserts ownership | Ownership conflicts are escalated, not resolved by the author. |
| Scope of integration commitments with external parties | Human user | Before an integration is documented as agreed | A proposed integration is not an agreed integration. |
| Changes to an accepted decision or approved architecture | Human user | On the Software Architect's impact analysis | Governed by `WF-009`; amendments and supersession are recorded. |
| Phase 3 completion | Human user, on the Software Architect's gate proposal | After all Phase 3 exit criteria are verified | Handled by `WF-008`. |

---

## 13. Completion Criteria

Phase 3 work under this workflow is complete when all of the following hold:

- [ ] Authorization for the Phase 3 work existed and is recorded.
- [ ] The requirements revision the architecture responds to is identified in each architecture document.
- [ ] Architecturally significant requirements and constraints are identified, with the selection basis recorded.
- [ ] Each significant decision has a record with context, options, rationale, consequences, and status.
- [ ] Technology and architecture decisions have been presented and their outcomes recorded, including conditions.
- [ ] The architecture overview describes boundary, context, containers, and components consistently with its textual descriptions.
- [ ] Data ownership, integration boundaries, security controls, and deployment structure are documented to the depth the approved scope requires.
- [ ] External capability, compatibility, and licensing claims cite evidence or are classified as unverified.
- [ ] Requirement-to-decision links exist in the traceability matrix, or the absence is a logged defect.
- [ ] Independent validation has been performed as designated, and findings have a recorded status.
- [ ] No implementation artifact was produced.
- [ ] The phase completion summary has been presented and the phase-gate decision recorded.

---

## 14. Exception Handling

### 14.1 Insufficient information

Where a requirement, constraint, or external capability needed for a design decision is unknown, record it as `OPEN QUESTION` with an owner and its effect on the decision. Do not fill the gap with a design assumption presented as fact; if a working assumption is unavoidable, classify it `ASSUMPTION` with its impact if wrong and a verification path.

### 14.2 Contradictions

Contradictions between requirements, between an approved constraint and a proposed design, between diagrams and descriptions, or between two decision records are recorded with both locations and escalated. Where a proposed design contradicts an approved decision, the conflict is documented and the decision to supersede belongs to the human user.

### 14.3 Unverifiable technical claims

A capability claim that research could not confirm remains unverified: it is classified `ASSUMPTION` or `OPEN QUESTION`, its source limitation is recorded, and no decision may be presented as resting on confirmed capability. Vendor marketing material is not proof.

### 14.4 Findings and blockers

Findings follow `WF-007`. A blocker is an unresolved question, contradiction, or missing approval without which the architecture cannot responsibly be presented for approval; the Software Architect designates and records it, and the workflow pauses rather than proceeding on an implied design.

### 14.5 Requests to implement

Requests to write code, produce a prototype, define infrastructure, or generate schemas as executable artifacts are refused, explained as outside the system's boundaries, and reported to the Software Architect. The refusal is recorded; the request is not satisfied indirectly by embedding implementation detail in a specification.

### 14.6 Changes after approval

Any change to an accepted decision, an approved architecture description, or a linked requirement follows `WF-009`. Accepted decisions are amended or superseded with dated records; they are never rewritten to appear to have always been correct.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-004-01` | Which Phase 3 artifacts require their own templates (technology stack, data model, API contracts, integration specification, security architecture, UX/UI, deployment)? | Currently several Phase 3 deliverables have no reusable structure, so consistency depends on each project. | Software Architect |
| `OQ-WF-004-02` | Is one decision record per file the intended convention, or a single decision register? | Affects identifier allocation and how amendments and supersession are traced. | Software Architect |
| `OQ-WF-004-03` | Should the architecture overview carry deployment structure, or does a separate deployment architecture document supersede its §9? | Avoids duplicated and potentially divergent descriptions. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Predecessor phase: supplies the requirements the architecture must satisfy. |
| [`WF-005` — Research](./research.md) | Invoked for technology, compatibility, licensing, and integration evidence. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked for every authorized draft or revision of an architecture file. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked for architecture quality, feasibility, security, and consistency review. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs technology and architecture approvals and the Phase 3 gate. |
| [`WF-009` — Change Control](./change-control.md) | Invoked for any change to an accepted decision or approved architecture, including amendments and supersession. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the System Design and Architecture workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable Phase 3 procedure that documents architecture without implementing it and reserves decisions for human approval. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
