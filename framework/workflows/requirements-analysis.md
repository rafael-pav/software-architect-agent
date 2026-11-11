# Workflow WF-003 — Requirements Analysis

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-003` |
| Workflow name | Requirements Analysis |
| Version | `0.1.4` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-003` |
| Purpose | Define how Phase 2 (Requirements Analysis) produces identifiable, atomic, verifiable, and traceable requirements, use cases, acceptance criteria, business rules, and a traceability matrix, without inventing requirements or promoting assumptions into confirmed facts. |
| Status | `Approved` |
| Version | `0.1.4` |
| Last updated | `2026-11-11` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | v0.1.2 approved by Human user on 2026-11-10. |
| Validation | v0.1.2: PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. v0.1.3: PATCH documentary correction; affected scope re-reviewed by the Validation Agent on 2026-11-11. v0.1.4: PATCH documentary correction (residual VAL-P03) under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. |
| Applies to | Phase 2 work on any project whose scope has been established or proposed in Phase 1. |
| Related workflows | `WF-002` (predecessor phase), `WF-004` (successor phase), `WF-005` (research), `WF-006` (documentation production), `WF-007` (independent validation), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§6–7, 10; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§4–6, 8, 9; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §6; [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) §4.3–4.4. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. The six prefixes `FR`, `NFR`, `BR`, `UC`, `INT`, and `SEC` are defined by the standard and are used here with exactly those meanings; `BR` means **Business Rule**. Register schemes cited in this workflow (`AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `US`, `EXC`, `TRD`, `VAL`) keep the meanings given by the template or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items — **except** the section-structure convention described in the next paragraph, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines Phase 2: the conversion of approved or proposed scope and business intent into requirements that can be reviewed, questioned, traced, and eventually verified.

Its central discipline is origin. Every requirement must be attributable to a business rule, an approved decision, a stakeholder statement, or a documented technical constraint. A requirement that exists only because an agent considered it sensible is not a requirement; it is an unsolicited proposal that must be labeled as such and flagged.

---

## 3. Trigger / When to Use

Use this workflow when:

- The human user has authorized Phase 2 work, normally after the Phase 1 scope decision.
- An approved requirement set must be extended, clarified, or corrected within an authorized change.
- A Phase 3 design activity has exposed a requirement gap that must be resolved before design can proceed.

Do not use this workflow to design a solution. Where elicitation reveals that a requirement cannot be stated without choosing a design, record the design dependency as an `OPEN QUESTION` and refer it to `WF-004`.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Software Requirements Specification (SRS) and its registers.
- Functional requirements (`FR`), non-functional requirements (`NFR`), business rules (`BR`), integration requirements (`INT`), and security requirements (`SEC`).
- Use cases (`UC`), user stories where the project uses them, and acceptance criteria (`AC`).
- The requirements traceability matrix and its documented exceptions and defects.
- Identification and reporting of orphan requirements, orphan business rules, missing links, missing acceptance criteria, conflicting references, duplicate identifiers, and broken identifiers.

### 4.2 Deliberately excluded

- Approving requirements, priorities, or business rules. Those are human decisions.
- Converting assumptions into requirements. An assumption remains an assumption until verified or approved.
- Architecture, technology selection, interface contracts, and data design (`WF-004`).
- Test execution. Future tests are recorded at planning level only; their presence is never evidence that testing occurred.
- Implementation detail of any kind, including code, schemas, and executable specifications.
- Changing an approved requirement outside `WF-009`.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns the phase. Confirms the requirements scope against the approved scope statement, decides elicitation priorities, challenges ambiguous requirements, judges which open questions block the phase gate, reviews drafts, and presents requirement and priority decisions to the human user. Writes no files. |
| **Documentation Agent** | Drafts the SRS, use cases, registers, acceptance criteria, and traceability matrix under `docs/02-requirements/`, assigns identifiers at first recording, preserves stability, and reports defects to the Software Architect. |
| **Research Agent** | Read-only. Investigates whether a stated requirement is technically achievable, what an external interface actually supports, or what a vendor constraint applies, when assigned. Distinguishes documented capability from assumption. |
| **Validation Agent** | Read-only. Independently reviews requirement quality, traceability, and evidence when assigned. Reports findings; does not rewrite requirements or approve them. |
| **Human user / stakeholder** | Approves functional requirements, business rules, security and privacy requirements, priorities, and any change to an approved requirement. Resolves conflicting stakeholder intent. |

Stakeholder intent reaches the agents through the Software Architect. Agents do not conduct independent stakeholder interviews, and no agent may speak for a stakeholder.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- Explicit human authorization to begin Phase 2, or an authorized change scope covering the requirements work.
- A scope statement or equivalent approved record of boundaries, or a recorded decision that scope is proposed rather than approved.
- The Documentation Agent has read `documentation-standards.md` §§4–6 and the SRS, use case, and traceability matrix templates.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Phase 2 authorization | Human user, recorded by the Software Architect | **MUST** | Identifies the requirement scope and any exclusions. |
| Approved or proposed scope boundaries | Phase 1 scope statement | **MUST** | Requirements outside the boundary are escalated, not silently added. |
| Business rules and policies | Original material, approved decisions, or the human user | **SHOULD** | A rule with no source is a `RECOMMENDATION`, not a rule. |
| Stakeholder statements | Human user via the Software Architect | **MUST** where a requirement depends on them | Must be attributable. |
| Constraints | Scope statement, feasibility study, architecture constraints where already decided | **SHOULD** | A constraint asserted without a source is an assumption. |
| Research findings | Research Agent via `WF-005` | **SHOULD** | Required for integration and feasibility claims. |
| Prior approved requirements | `docs/02-requirements/` and `DEC-NNN` register | **MUST** be preserved | Stability and traceability rules apply. |

---

## 7. Workflow Steps

1. **Confirm the authorization and the requirements scope.** The Software Architect states which capabilities, actors, and interfaces the specification covers, and what it deliberately excludes. Scope comes from the approved scope statement; any divergence is escalated.
2. **Establish the authoring rules before content.** Define in the SRS: atomicity, verifiability, the identifier scheme, the priority scheme, the requirement status vocabulary, and the rule that every requirement cites its origin. A priority scheme that readers must guess is a defect.
3. **Record the actors and external interfaces at index level.** Identify human actors, external systems, and internal components relevant to the requirements. Interface detail belongs in `INT` entries and the integration documentation, not in an index table.
4. **Establish business rules first.** Record each `BR` with its source and authority, conditions, and exceptions. A rule asserted by an agent without a source is classified `RECOMMENDATION` or `ASSUMPTION` and flagged. This ordering gives requirements something to originate from.
5. **Elicit and draft functional requirements.** Each `FR` is one testable obligation with a stated origin (`BR-NNN`, approved decision, or stakeholder statement) and an acceptance criterion reference. Multiple obligations in one requirement are split.
6. **Draft non-functional requirements with measurable targets.** Each `NFR` states a target, a unit, the conditions under which it applies, and how compliance will be demonstrated. A quality adjective without a measure is either quantified or recorded as `OPEN QUESTION`.
7. **Draft security and privacy requirements.** Each `SEC` states the requirement, the threat or control objective, the scope of application, and the verification method. Regulatory or contractual obligations are cited or recorded as `OPEN QUESTION`; they are never invented.
8. **Draft integration requirements.** Each `INT` states the external system or interface, direction, data or capability exchanged, and known constraints. Unverified external capability is classified accordingly, with a reference to the research evidence.
9. **Commission research where a requirement's feasibility is unknown.** The Software Architect assigns specific questions to the Research Agent under `WF-005`. The requirement remains as stated, with its uncertainty flagged, until evidence arrives.
10. **Document use cases.** For each `UC`, record actors, preconditions, trigger, main flow, alternate flows, exceptions, postconditions, related requirements, and acceptance criteria. Describe observable behavior, not internal design. Steps without a responsible actor or component are defects.
11. **Write acceptance criteria.** Each criterion is evaluable and identifies what it verifies (a requirement, a use case, or a scope deliverable) and its verification method. A criterion that cannot fail is not a criterion. Future tests are identified as `TST` at planning level only.
12. **Build the traceability matrix as the authoritative register.** Record the chain Business Rule → Requirement → User Story / Use Case → Architecture Decision → Acceptance Criteria → Future Test, in both directions, using stable identifiers only. Where architecture decisions do not yet exist, the link is recorded as a pending link for Phase 3, not as an exception unless a decision is made that no decision is needed.
13. **Record documented exceptions explicitly.** A non-functional requirement with no use case, or a requirement with no originating business rule, is recorded as a reasoned exception or as a defect — never as an empty cell.
14. **Identify and log traceability defects.** Orphan requirements, orphan business rules, missing links, missing acceptance criteria, decision without requirement, non-verifying criterion, conflicting reference, duplicate identifier, and broken identifier are logged with identifiers, documents, sections, severity, owner, and open status; then reported to the Software Architect.
15. **Review internally.** The Software Architect checks atomicity, verifiability, consistency with objectives, and consistency across registers, and returns precise corrections.
16. **Obtain independent validation** under `WF-007` for the requirement set and the matrix, as designated by the Software Architect.
17. **Apply authorized corrections.** Editorial and clarifying corrections follow `WF-006`. Any change to an approved requirement, priority, or business rule follows `WF-009`.
18. **Present requirement and priority decisions.** Under `WF-008`, the Software Architect presents the requirement set, the unresolved ambiguities, the traceability defect status, and the recommended priority scheme for human approval.
19. **Record the outcome and prepare the gate proposal.** Approval status, conditions, and unresolved items are recorded; the phase completion summary is assembled for the gate decision.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Documentation Agent | Draft or revise named requirements files. | Explicit file list; `docs/02-requirements/` only; identifiers assigned at first recording; no renumbering. |
| Software Architect | Research Agent | Feasibility, interface capability, and constraint questions attached to specific requirements or integrations. | One question set per assignment; evidence and limits returned; no decisions. |
| Software Architect | Validation Agent | Independent review of requirement quality, traceability, and evidence. | Read-only; findings with identifiers, severity, and paths. |
| Documentation Agent | Software Architect | Draft report: registers produced, identifiers assigned, defects found, assumptions used, open questions. | Must include traceability defects rather than resolving them silently. |
| Research Agent | Software Architect | Findings that confirm, qualify, or contradict a stated requirement. | Does not rewrite the requirement; the Architect decides what changes. |
| Validation Agent | Software Architect | Findings and a phase-gate recommendation. | Cannot approve requirements, priorities, or the phase. |

---

## 9. Expected Outputs

| Output | Path (when persisted) | Notes |
| --- | --- | --- |
| Software Requirements Specification | `docs/02-requirements/software-requirements-specification.md` | Contains the `FR`, `NFR`, `BR`, `SEC`, and `INT` registers and the authoring rules. |
| Use cases | `docs/02-requirements/` (one file per use case, or a single file by project convention) | `UC` identifiers unique across the project. |
| Requirements traceability matrix | `docs/02-requirements/requirements-traceability-matrix.md` | Authoritative register for the traceability chain, its exceptions, and its defect log. |
| Acceptance criteria register | Within the SRS, use cases, or the matrix as the project convention states | `AC` identifiers unique and stable. |
| User stories (if used) | Recorded by the project-recorded user-story convention, with the `US` scheme declared in `requirements-traceability-matrix.md` §2 | No template currently exists; see §10. |
| Requirements defect report | Reported to the Software Architect; persisted only if authorized | Defects remain open until corrected and confirmed. |
| Research and validation reports (if persisted) | `docs/04-research/`, `docs/05-validation/` | Persistence is not approval and does not resolve findings. |
| Phase 2 completion summary | Presented by the Software Architect; persisted only if authorized | `RECOMMENDATION` until the gate decision. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Software Requirements Specification template | [`framework/templates/software-requirements-specification.md`](../templates/software-requirements-specification.md) | Structure for authoring rules and the `FR`, `NFR`, `BR`, `SEC`, and `INT` registers. |
| Use Case template | [`framework/templates/use-case.md`](../templates/use-case.md) | Structure for a single `UC`, its flows, exceptions, and traceability links. |
| Requirements Traceability Matrix template | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | Authoritative structure for the chain, documented exceptions, and the defect log. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Source of scope boundaries and scope-level acceptance criteria that requirements must respect. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Target of the requirement-to-decision link maintained for Phase 3. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Evidence structure for feasibility and integration findings. |
| Documentation Standards §§5–6 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Identifier format and stability, and the required traceability chain. |

**Template availability (observed 2026-11-10).** Templates exist for the SRS, a single use case, and the traceability matrix. No template exists for user stories or for a standalone acceptance criteria register; the SRS, use case, and matrix templates carry `AC` columns. The Documentation Agent **MUST** follow the project-recorded user-story convention, declaring the `US` scheme in `requirements-traceability-matrix.md` §2 as the identifier scheme for user stories, and **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Origin recorded | Documentation Agent | Every requirement cites a business rule, approved decision, stakeholder statement, or documented constraint, or is flagged as an orphan candidate. |
| Atomicity | Documentation Agent, checked by the Software Architect | One obligation per requirement; compound requirements are split. |
| Verifiability | Documentation Agent | Each requirement has evaluable acceptance criteria; unverifiable requirements are flagged, not left silently unsupported. |
| Measurable non-functional targets | Documentation Agent | Target, unit, conditions, and verification method present; otherwise `OPEN QUESTION`. |
| Identifier integrity | Documentation Agent, validated by the Validation Agent | `PREFIX-NNN` format, project-wide uniqueness, no reuse, no renumbering without recorded approval. |
| Traceability completeness | Documentation Agent, validated by the Validation Agent | Chain links exist or a documented exception is recorded; empty cells are never accepted. |
| Defect visibility | Documentation Agent | Defects are logged and reported; a proposed correction does not close a defect. |
| Assumption containment | Software Architect | Assumptions are not written into requirement registers as if they were requirements. |
| Independent validation | Validation Agent, under `WF-007` | Requirement quality and traceability findings with severity and status. |

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Functional requirements, including acceptance of the requirement set | Human user | After independent validation and the Software Architect's review | Requirements remain proposed until approved. |
| Business rules and their authority | Human user, or the source that owns the rule | Before requirements depend on them | An agent may not declare a business rule to exist. |
| Business priorities | Human user | With the approval of the requirement set | Priorities rank work; agents propose, users decide. |
| Security and privacy requirements | Human user | Before they are treated as binding | Includes regulatory applicability, which agents may investigate but not determine. |
| Changes to an approved requirement | Human user | On the Software Architect's impact analysis | Governed by `WF-009`; the Documentation Agent may not amend approved requirements under a drafting assignment. |
| Acceptance of a documented traceability exception affecting an approved requirement | Human user, on the Software Architect's recommendation | Before the exception is treated as accepted | Exceptions remain open until a decision records them. |
| Phase 2 completion | Human user, on the Software Architect's gate proposal | After all Phase 2 exit criteria are verified | Handled by `WF-008`. |

---

## 13. Completion Criteria

Phase 2 work under this workflow is complete when all of the following hold:

- [ ] Authorization for the Phase 2 work existed and is recorded.
- [ ] The requirements scope is stated and consistent with the approved scope statement, or the divergence is recorded.
- [ ] Authoring rules, including the identifier and priority schemes, are defined before the registers are read.
- [ ] All requirements use the six defined prefixes and the `PREFIX-NNN` format; identifiers are unique and stable.
- [ ] Every requirement has a recorded origin or a flagged orphan status.
- [ ] Every requirement has verifiable acceptance criteria, or a recorded defect.
- [ ] Non-functional requirements have measurable targets and measurement conditions, or are flagged.
- [ ] Security and integration requirements cite their basis or record the missing basis.
- [ ] Use cases exist for the behaviors the requirement set requires, or the absence is documented.
- [ ] The traceability matrix covers the chain in both directions, with documented exceptions and a defect log.
- [ ] Traceability defects have been reported to the Software Architect and have a current status.
- [ ] Independent validation has been performed as designated, and findings have a recorded status.
- [ ] Requirement, priority, and security decisions are presented and their outcomes recorded.
- [ ] The phase completion summary has been presented and the phase-gate decision recorded.
- [ ] No assumption was promoted to a requirement without recorded evidence or approval.
- [ ] No application implementation, code, or privileged file modification occurred.

---

## 14. Exception Handling

### 14.1 Insufficient information

A requirement that cannot be stated precisely is recorded in the register with its identifier and flagged, or recorded as `OPEN QUESTION` with an owner, rather than written as vague prose. Where a requirement must be stated provisionally, the basis is recorded as `ASSUMPTION` and the requirement's status reflects that it depends on verification.

### 14.2 Contradictions

Conflicting requirements, conflicting business rules, or a requirement that contradicts an approved scope boundary are recorded with all affected identifiers and locations, logged as traceability defects where applicable, and escalated. Agents do not select one statement and delete the other.

### 14.3 Ambiguous or unverifiable requirements

Terms such as "fast", "secure", "user-friendly", or "appropriate" are either quantified or flagged as `OPEN QUESTION`. Requirement quality findings from the Validation Agent are reported with identifiers and severity; the Software Architect decides whether the requirement is corrected, withdrawn, or accepted as a recorded exception.

### 14.4 Research that cannot resolve a question

Where research cannot confirm a capability, the requirement keeps its uncertainty: the integration or feasibility claim becomes `ASSUMPTION` or `OPEN QUESTION`. The research limitation is disclosed in the affected register and in the research report. An unverified claim is never upgraded because a decision is pending.

### 14.5 Findings and blockers

Findings follow `WF-007`. A blocker is an ambiguity, missing decision, or unresolved contradiction without which the requirement set cannot be approved; the Software Architect designates it, records it, and presents it. The workflow pauses at a blocker rather than proceeding with an unstated interpretation.

### 14.6 Changes after approval

Any change to an approved requirement, business rule, acceptance criterion, or priority follows `WF-009`. Withdrawn or superseded identifiers are retained with their disposition; they are never reused or deleted.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-003-01` | Should user stories have a dedicated template, or remain a project convention recorded in the SRS? | The traceability chain names user stories; their structure is currently undefined. | Software Architect |
| `OQ-WF-003-02` | Where is the authoritative acceptance criteria register when criteria appear in the SRS, use cases, and the matrix? | Duplicate `AC` identifiers across documents are a defect risk. | Software Architect |
| `OQ-WF-003-03` | Which identifier range allocation, if any, should the Architect assign per document to prevent duplicate numbering? | The standard permits distributed sequences but requires allocation to be recorded. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Predecessor phase: supplies approved scope, objectives, and constraints. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Successor phase: consumes requirements and adds architecture decision links to the matrix. |
| [`WF-005` — Research](./research.md) | Invoked for feasibility and interface-capability evidence attached to requirements. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked for every authorized draft or revision of a requirements file. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked for requirement quality, traceability, and evidence review. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs requirement, priority, and security approvals and the Phase 2 gate. |
| [`WF-009` — Change Control](./change-control.md) | Invoked for any change to an approved requirement, rule, criterion, or priority. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the Requirements Analysis workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable Phase 2 procedure that preserves origin, identifiers, and traceability. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), the user-story convention in §9 and §10 is repointed to the `US` scheme in `requirements-traceability-matrix.md` §2 (VAL-005), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.1.3 | 2026-11-11 | PATCH documentary correction: the §1 "Normative basis" now carves out the section-structure convention — which remains a `RECOMMENDATION` until a durable workflow-governance document is established — so that it is no longer read as already in effect as part of the approved workflow; the `Authority / approval` field now attributes the Human approval to v0.1.2; and the `Validation` field now attributes the PASS result to v0.1.2 and records this version as a PATCH documentary correction not requiring re-validation per WF-009 §11.2. No rule, procedural step, approval, or approved decision was changed; status remains `Approved`. | Resolve the systemic "Normative basis / Section structure" pattern under the carve-out recorded in WF-009 §16 and align the metadata attribution with the change history. Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.2 approved by Human user on 2026-11-10; v0.1.3 PATCH documentary correction; the v0.1.2 validation result stands. |
| 0.1.4 | 2026-11-11 | PATCH documentary correction: the `Validation` field no longer asserts that re-validation is not required for v0.1.3 by reference to WF-009 §11.2; it now records that the affected scope was re-reviewed by the Validation Agent on 2026-11-11, and a v0.1.4 entry records this residual correction (VAL-P03). Status remains `Approved`; "Normative basis" and "Authority / approval" are unchanged. No rule, procedural step, approval, or approved decision was changed. | Resolve validation finding VAL-P03 (residual). Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.2 approved by Human user on 2026-11-10; v0.1.4 PATCH documentary correction; the v0.1.2 validation result stands. |
