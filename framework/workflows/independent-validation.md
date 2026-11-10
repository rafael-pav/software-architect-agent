# Workflow WF-007 — Independent Validation

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-007` |
| Workflow name | Independent Validation |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-007` |
| Purpose | Define how deliverables are reviewed independently by the read-only Validation Agent, how findings are recorded and evaluated, how corrections are authorized and re-reviewed, and how a finding's resolution is established without confusing validation with approval. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Independent review of project deliverables, of persisted research reports, and of framework assets whose governance requires review. |
| Related workflows | `WF-002`, `WF-003`, `WF-004` (deliverables under review), `WF-005` (evidence review), `WF-006` (corrections and report persistence), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §8; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§6, 9, 10; [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) §§2–10; [`framework/standards/README.md`](../standards/README.md) §5.3. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Finding identifiers use `VAL-NNN`, established by the Validation Agent definition; register schemes cited here (`ASM`, `OQ`, `AC`, `TST`, `TRD`, `EXC`, `BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `ADR`, `DEC`) keep the meanings given by the standard or template that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines independent validation as an adversarial-but-fair review performed by an agent that did not write the material, cannot modify it, and cannot approve it.

Its purpose is to keep three outcomes distinct: a *finding* (a reviewer's observation with severity), a *correction* (an authorized author's change), and a *resolution* (the reviewer's confirmation that the correction addresses the finding). Collapsing any two of these is how documentation systems acquire a record of quality that does not exist.

---

## 3. Trigger / When to Use

Use this workflow when:

- A phase deliverable is being prepared for a decision or a phase gate and the Software Architect designates it for independent review.
- A framework asset is being proposed or changed and its governance requires independent review.
- A change under `WF-009` affects a deliverable that was previously validated and must be re-reviewed.
- A prior finding requires verification after an authorized correction.
- The Software Architect has reason to doubt the completeness or consistency of a deliverable.

Do not use this workflow as a substitute for the author's own quality checks, and do not use it to legitimize a decision already taken. Validation that is requested after approval has been presented is not independent validation of the decision.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Independent review of documentation for completeness, consistency, requirement quality, traceability, evidence and sources, technical feasibility, security and privacy, and architecture quality, where applicable.
- Review of framework assets against their own governance criteria and against repository instructions.
- Recording findings with identifiers, severity, precise affected locations, and recommended corrective action.
- Reporting a phase-gate recommendation to the Software Architect.
- Re-review after authorized corrections.
- Verification of whether a finding has been addressed.

### 4.2 Deliberately excluded

- Modifying any file, including the documents under review and the validation report itself.
- Writing findings into the repository; persistence is performed by the Documentation Agent under authorization.
- Approving deliverables, scope, budget, requirements, technology, architecture, or phase transitions.
- Waiving approvals, waiving findings, or downgrading a finding's severity as part of persistence.
- Conducting web research or verifying sources not supplied in the repository or by the Software Architect.
- Executing shell commands, prototypes, or tests.
- Reviewing documents it did not inspect, or extending conclusions to uninspected material.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Defines the review scope, criteria, and document versions; supplies the material; evaluates findings; decides priorities and whether corrections are requested; ensures findings are neither dismissed nor silently downgraded; authorizes corrections; requests re-review; presents outcomes to the human user. Writes no files. |
| **Validation Agent** | Performs the independent review. Read-only, non-authoring, non-approving. Records findings with severity and evidence, reports them to the Software Architect, and confirms or declines to confirm resolution after re-review. |
| **Documentation Agent** | Sole writer. Applies authorized corrections to named files, records version and change history, and persists the validation report when authorized, preserving findings, severity, and limitations. Does not adjudicate findings. |
| **Research Agent** | Read-only. May be asked to supply additional evidence to resolve an evidence-related finding. Does not review and does not decide. |
| **Human user / stakeholder** | Decides matters reserved to them, including acceptance of residual risk that affects scope, requirements, security, technology, architecture, or a previously approved deliverable. Does not receive validation findings filtered or softened. |

Independence requirement: the reviewer must not be the author of the reviewed material and must not rely on the author's own summary as evidence of its quality.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- The Software Architect has defined the review scope: which documents, which versions or dates, which criteria, and which lifecycle phase or milestone the review informs.
- The documents are available in the repository at the stated versions.
- The reviewer has not authored the material under review.
- The review will not be performed by the Documentation Agent, and the Documentation Agent's self-check is not presented as the review.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Review scope and criteria | Software Architect | **MUST** | Includes the phase exit criteria or governance criteria being applied. |
| Documents and versions under review | Repository paths | **MUST** | Named individually; unpresented documents are recorded as unavailable. |
| Repository instructions and standards | `AGENTS.md`, `framework/standards/` | **MUST** | Basis for compliance findings. |
| Templates | `framework/templates/` | **SHOULD** | Basis for structural completeness findings. |
| Prior validation reports and finding status | `docs/05-validation/` | **SHOULD** | Required for re-review; findings retain their identifiers. |
| Research evidence | `docs/04-research/` and Software Architect-supplied evidence | **SHOULD** | The reviewer does not research independently. |
| Known limitations of the review | Software Architect | **SHOULD** | Recorded in the report. |

---

## 7. Workflow Steps

1. **Confirm the review assignment.** The Software Architect states the phase, the documents and versions, the criteria, and the intended decision the review informs. The Validation Agent confirms it can review the material as scoped, or reports which required material is unavailable.
2. **Record review information.** Capture lifecycle phase, review scope, documents reviewed with versions, review basis, and review limitations. Documents not inspected **MUST NOT** appear as reviewed.
3. **Review each applicable dimension.** Completeness, consistency, requirements quality, traceability, evidence and sources, technical feasibility, security and privacy, and architecture quality. A dimension is marked `NOT APPLICABLE` only with a reason; it is never marked `PASS` on the basis of material that was not examined.
4. **Record findings precisely.** Each finding states: identifier (`VAL-NNN`, stable across iterations), severity, affected document with exact path, section or identifier, description, why it matters, and recommended corrective action. A finding without a location cannot be corrected and is not a usable finding.
5. **Assign and justify severity.** Use `CRITICAL`, `HIGH`, `MEDIUM`, `LOW`, `INFORMATIONAL`, and state why the severity applies. Do not exaggerate to force action and do not deflate to avoid it.
6. **Review traceability explicitly.** Walk the chain Business Rule → Requirement → User Story / Use Case → Architecture Decision → Acceptance Criteria → Future Test, and record missing, incomplete, or inconsistent links with their identifiers. Distinguish documented exceptions from defects.
7. **Review evidence without overclaiming.** Assess whether external claims have identifiable sources, whether versions are stated, and whether limitations are disclosed. Do not claim to have verified a URL or source that was not accessed.
8. **Report findings to the Software Architect only.** The Validation Agent does not write the report into the repository, does not edit the documents, and does not communicate corrections directly to the author.
9. **Provide a phase-gate recommendation.** Choose `PASS`, `PASS WITH CONDITIONS`, `FAIL`, or `INCOMPLETE REVIEW`, with reasoning, tracked conditions, and blocking findings. State explicitly that the recommendation is not an approval and cannot complete a phase.
10. **Architect evaluation.** The Software Architect evaluates each finding: accepted for correction, contested with reasons, deferred with a recorded rationale, or escalated to the human user. A finding **MUST NOT** be removed, downgraded, or closed without a recorded decision and rationale.
11. **Authorize corrections.** The Software Architect authorizes the Documentation Agent under `WF-006` with an explicit list of files and the findings each correction addresses. Where the correction alters an approved decision, scope, requirement, or architecture baseline, authorization first passes through `WF-009`.
12. **Apply authorized corrections.** The Documentation Agent applies only the authorized corrections, updates version and change history, and reports which findings it believes are addressed — as a claim, not as a resolution.
13. **Re-review.** The Validation Agent examines the corrected material against the original finding. It confirms `Resolved — verified` only where the correction actually addresses the finding; otherwise it records `Correction proposed`, `Open`, or a new finding with its own identifier.
14. **Record resolution status.** Findings retain their identifiers and status across iterations. A finding is `Resolved` only after re-review; `Accepted as risk` requires a recorded decision by the Software Architect and, where the matter requires it, human approval.
15. **Persist the report only if authorized.** The Documentation Agent persists the report under `docs/05-validation/` using the validation report template, preserving findings, severity, evidence, limitations, and attribution. Later decisions and corrections are recorded in the report's status section.
16. **Feed the outcome into the phase gate.** The Software Architect incorporates the validated state — not merely the fact that validation occurred — into the gate decision under `WF-008`.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Validation Agent | Independent review of named documents and versions against stated criteria. | Read-only; no file writes; no web research; findings to the Architect only. |
| Validation Agent | Software Architect | Findings with severity and locations; a phase-gate recommendation; stated limitations. | Recommendation only; cannot approve or waive anything. |
| Software Architect | Documentation Agent | Apply authorized corrections to named files. | File list and finding references required; no adjudication of findings. |
| Software Architect | Documentation Agent | Persist the validation report. | Preserve findings and severity; target path under `docs/05-validation/`. |
| Software Architect | Research Agent | Supply evidence needed to resolve an evidence-related finding. | Read-only; evidence returned to the Architect. |
| Software Architect | Human user | Decide matters reserved to the human user, including residual risk acceptance where required. | Findings presented as reported, not filtered. |

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Independent validation report | Validation Agent | Review information, results by dimension, findings, traceability review, assumptions and open questions, gate recommendation, recommendations, limitations. |
| Findings register | Validation Agent | Identified findings with severity, location, rationale, and recommended action. |
| Phase-gate recommendation | Validation Agent | One of four outcomes with reasoning and blocking findings. |
| Architect evaluation record | Software Architect | Disposition of each finding, with rationale for contested, deferred, or escalated items. |
| Authorized corrections | Documentation Agent | Changed files with version increments and change-history entries. |
| Re-review outcome | Validation Agent | Per-finding confirmation or rejection of resolution. |
| Persisted validation report (conditional) | Documentation Agent | File under `docs/05-validation/`, only on explicit authorization. |
| Gate input | Software Architect | Validated state incorporated into the phase-gate decision. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Structure for the persisted report, including findings, severities, traceability review, and finding status after review. |
| Requirements Traceability Matrix template | [`framework/templates/requirements-traceability-matrix.md`](../templates/requirements-traceability-matrix.md) | Source of the defect log whose entries the review cross-checks. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Evidence base against which source-quality findings are made. |
| Architecture Overview template | [`framework/templates/architecture-overview.md`](../templates/architecture-overview.md) | Structural baseline for completeness and architecture-quality findings. |
| Documentation Standards §§6, 9, 10 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Traceability defects, status vocabulary, and the criteria a complete document must satisfy. |
| Validation Agent definition | [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) | Review dimensions, severity definitions, procedure, report structure, and approval restrictions. |
| Standards governance README §5.3 | [`framework/standards/README.md`](../standards/README.md) | Review stage for standards, including the rule that findings are not dismissed. |

**Template availability (observed 2026-11-10).** A validation report template exists. No template exists for an Architect evaluation record or a finding-disposition log; those are recorded in the Software Architect's reporting and, where persisted, in the validation report's status section. The Documentation Agent **MUST NOT** create a template without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Independence | Software Architect | The reviewer did not author the material and does not rely on the author's summary as evidence. |
| Scope fidelity | Validation Agent | Only inspected documents are listed as reviewed; unavailable material is recorded as a limitation. |
| Location precision | Validation Agent | Every finding names a path and a section or identifier. |
| Severity discipline | Validation Agent, checked by the Software Architect | Severity is justified and not adjusted during persistence. |
| No silent dismissal | Software Architect | Contested or deferred findings carry a recorded rationale; none is removed without a decision. |
| No premature resolution | Validation Agent | A finding is not resolved until the correction has been re-reviewed. |
| Correction scope control | Documentation Agent | Only authorized files change; unrelated rewriting is avoided. |
| Persistence fidelity | Documentation Agent | Findings, severity, evidence, and limitations are preserved as reported. |
| Honest gate input | Software Architect | The gate decision reflects open findings, not merely the occurrence of a review. |

Independent validation of a workflow or standard is itself subject to this workflow; the fact that a document describes validation does not mean it has been validated.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Acceptance of a deliverable that contains open findings | Human user, on the Software Architect's presentation | Before approval is recorded | A deliverable with unresolved critical findings cannot be recorded as approved. |
| Acceptance of residual risk where a finding is not corrected | Human user | When the matter affects scope, budget, requirements, security or privacy, technology, architecture, or a previously approved deliverable | The acceptance and its authority are recorded; the finding is retained. |
| Approval of corrections that change approved content | Human user, through `WF-009` | Before the Documentation Agent executes the change | Corrections that alter approved decisions are not made under a validation assignment. |
| Phase transition | Human user, on the Software Architect's gate proposal | After validation and finding resolution | Handled by `WF-008`. Validation never completes a phase. |

No approval point exists inside the Validation Agent's own activity. The reviewer's output is a finding and a recommendation, and it acquires authority only through the Architect's and the human user's decisions.

---

## 13. Completion Criteria

An independent validation cycle is complete when all of the following hold:

- [ ] The review scope, criteria, and document versions were defined and recorded.
- [ ] Only documents actually inspected are listed as reviewed.
- [ ] Each applicable dimension has a result with evidence reviewed and stated limitations.
- [ ] Findings are recorded with identifiers, severity, exact locations, rationale, and recommended action.
- [ ] Traceability was reviewed along the required chain, with defects and exceptions distinguished.
- [ ] Evidence was assessed without claiming verification of sources that were not accessed.
- [ ] A phase-gate recommendation was provided with reasoning and blocking findings.
- [ ] The Software Architect recorded a disposition for every finding.
- [ ] Corrections were applied only under explicit authorization and only to the authorized files.
- [ ] Each finding's status reflects reality: re-reviewed where resolved, open where not.
- [ ] Persistence, if it occurred, was authorized and preserved attribution, severity, and limitations.
- [ ] No file was modified by the Validation Agent.
- [ ] No deliverable was described as approved because it was reviewed.

---

## 14. Exception Handling

### 14.1 Insufficient or unavailable material

Record the unavailable documents as a limitation and, where they are required for the review, return `INCOMPLETE REVIEW` rather than a `PASS` or `FAIL` that implies coverage. The Software Architect decides whether to supply the material or to proceed with a recorded limitation.

### 14.2 Contradictions found during review

Record the contradiction as a finding with both locations and its effect on the deliverable. Do not decide which statement is correct; that is a correction decision for the Software Architect and, where approved content is involved, a `WF-009` matter.

### 14.3 Findings the author disputes

The author's disagreement is stated to the Software Architect, not to the reviewer. The Software Architect evaluates the finding and records the disposition with reasons. Severity is not reduced to end the disagreement, and a finding is not withdrawn because it is inconvenient.

### 14.4 Corrections that do not resolve the finding

If re-review shows the correction is partial or addressed a different point, the finding remains open and a new finding is raised if the discrepancy is material. A correction that was drafted, promised, or described as complete is not a resolution.

### 14.5 Blocking findings and gate pressure

A `CRITICAL` or `HIGH` finding that remains open blocks the phase gate. Pressure to lower severity, to omit a finding from the report, or to record a phase as complete is refused and escalated; such a request is itself recorded.

### 14.6 Re-validation after change

Where `WF-009` authorizes a change to previously validated content, the affected scope is re-reviewed. Validation of the earlier version remains recorded as valid for that version only; it does not extend to the changed content.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-007-01` | Should the review of framework assets use the same report structure and severity scheme as project deliverables, or a governance-specific variant? | The templates and the validation definition are oriented towards project deliverables. | Software Architect |
| `OQ-WF-007-02` | Where is the Architect's finding disposition recorded when a validation report is not persisted? | Findings could be closed without a durable record of the decision. | Software Architect |
| `OQ-WF-007-03` | Is a re-review required after every correction, or only after corrections affecting `CRITICAL`/`HIGH` findings? | Affects effort and the trustworthiness of `Resolved` status. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Produces Phase 1 deliverables subject to this review. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Produces Phase 2 deliverables and the traceability matrix this review checks. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Produces Phase 3 deliverables subject to feasibility and architecture review. |
| [`WF-005` — Research](./research.md) | Supplies evidence whose quality this review may assess. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Applies authorized corrections and persists the validation report. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Consumes the validated state and the gate recommendation. |
| [`WF-009` — Change Control](./change-control.md) | Authorizes changes to validated deliverables and triggers re-review. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the independent validation workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a review procedure that keeps findings, corrections, and resolutions distinct and prevents validation from being treated as approval. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
