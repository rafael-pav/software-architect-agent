# Workflow WF-005 — Research

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-005` |
| Workflow name | Research |
| Version | `0.2.1` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-005` |
| Purpose | Define how an external research assignment is scoped, conducted, evidenced, and reported by the read-only Research Agent, and how its findings are persisted and used without being mistaken for decisions or validation. |
| Status | `Approved` |
| Version | `0.2.1` |
| Last updated | `2026-11-11` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | v0.1.2 and earlier: approved by Human user on 2026-11-10. v0.2.0: approved by Human user on 2026-11-10; change authorized by the Software Architect on 2026-11-10. |
| Validation | v0.1.2: PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. v0.2.0: Independent validation PASS WITH CONDITIONS — corrections verified as resolved (VAL-001/002/003/004/006/008/009/010/011); deferred items accepted as pending (VAL-005, VAL-007, VAL-100). |
| Applies to | Any research assignment commissioned during Phase 1, Phase 2, or Phase 3, and any framework-level research the Software Architect commissions. |
| Related workflows | `WF-002`, `WF-003`, `WF-004` (phase workflows that commission research), `WF-006` (report persistence), `WF-007` (independent validation), `WF-008` (approval), `WF-009` (change control), `WF-011` (document extraction). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§5, 9; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§4, 7, 9; [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md) §§2–7; [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) §4.5. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`FND`, `SRC`, `OPT`, `REC`, `RISK`, `OQ`, `ASM`, `BR`, `FR`, `NFR`, `INT`, `SEC`, `ADR`, `DEC`, `VAL`) keep the meanings given by the standard, template, or agent definition that establishes them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: the workflow was approved by the Human user on 2026-11-10 and independently validated — v0.1.2 PASS, and v0.2.0 PASS WITH CONDITIONS, with corrections verified as resolved and `VAL-005`, `VAL-007`, and `VAL-100` deferred as pending items — so those conventions are no longer pending `RECOMMENDATION` items — **except** the section-structure convention described in the next paragraph, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines research as a controlled activity with a defined question, a defined evidence threshold, and a defined output — not as open-ended browsing.

Its purpose is to make the difference between four things unavoidable to a reader: what a source actually documents, what an agent infers from it, what an agent recommends, and what remains unknown. Research informs decisions. It does not make them, and persisting a research report does not approve its content.

---

## 3. Trigger / When to Use

Use this workflow when:

- A phase workflow requires external evidence for a feasibility, capability, compatibility, licensing, pricing, security, or integration claim.
- The Software Architect needs alternatives compared against defined criteria.
- A validation finding cannot be resolved without additional evidence.
- A previously accepted finding is challenged by new information and must be re-examined.

Do not use this workflow to confirm a decision that has already been made, to justify a preferred option, or to produce documentation. Research output is evidence and findings; documentation is produced under `WF-006`.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Defining research questions, scope, exclusions, comparison criteria, and evidence thresholds.
- Searching for and reading primary and official sources.
- Verifying material claims against official documentation.
- Recording sources with the fields required by `documentation-standards.md` §7.2.
- Comparing alternatives on consistent, pre-defined criteria.
- Recording limitations, version applicability, dependencies, and licensing conditions.
- Classifying findings and stating confidence.
- Reporting findings to the Software Architect.
- Persisting a report, on authorization, under `docs/04-research/`.

### 4.2 Deliberately excluded

- Making project decisions or approving options.
- Writing, editing, or deleting any repository file by the Research Agent. The Research Agent is read-only.
- Producing project deliverables, specifications, or architecture descriptions.
- Independent validation of the research by the researcher.
- Application implementation, integration prototypes, or environment testing.
- Citing sources that were not consulted, or reconstructing URLs, dates, or capabilities from memory.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Commissions the assignment: question, decision supported, scope, exclusions, criteria, evidence threshold, and required output. Evaluates findings, decides how they affect project decisions, and authorizes persistence. Writes no files. |
| **Research Agent** | Conducts the research. Read-only: no file creation, modification, deletion, shell execution, or delegation. Reports findings, sources, limitations, alternatives, and open questions to the Software Architect. |
| **Documentation Agent** | Persists the research report only when the Software Architect authorizes it, preserving attribution, findings, evidence, severity of limitations, and open questions. Applies the research report template. Does not conduct research. |
| **Validation Agent** | Read-only. May assess whether evidence in a deliverable is sufficient and identifiable, using only material supplied in the repository and by the Software Architect. Does not perform web research and does not verify sources it cannot access. |
| **Human user / stakeholder** | Approves the decisions the research supports, where those decisions require human approval. Does not approve the research report by receiving it. |

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- The Software Architect has defined a research question that is answerable with evidence.
- The decision or requirement the research supports is identified, so that the evidence threshold can be set proportionately.
- The Research Agent's read-only boundary is understood by all participants.
- Web access requests are subject to the permission model in force; the Research Agent does not bypass a denied or unapproved access request.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Research question and the decision it supports | Software Architect | **MUST** | A question with no stated decision cannot be scoped or evaluated for sufficiency. |
| Scope and exclusions | Software Architect | **MUST** | Includes products, versions, editions, and time period of interest. |
| Comparison criteria, if alternatives are assessed | Software Architect | **MUST** where options are compared | Defined before assessment to prevent reverse-engineered ratings. |
| Evidence threshold | Software Architect | **SHOULD** | States what would count as sufficient, for example official documentation of the specific version. |
| Project constraints | Phase 1 and Phase 2 outputs | **SHOULD** | Alternatives are assessed against the project's constraints, not general popularity. |
| Prior research | `docs/04-research/` | **MAY** | Prior findings are reused with their limitations, not presented as fresh evidence. |

---

## 7. Workflow Steps

1. **Receive and restate the assignment.** The Research Agent confirms the question, the decision or requirement it supports, the scope, the exclusions, and the evidence threshold. If the question is ambiguous or unanswerable as stated, it is returned to the Software Architect before work begins.
2. **Define the search plan.** Identify the categories of primary sources likely to hold the answer: official vendor documentation, official API references, official pricing and licensing documentation, standards bodies, official release notes. Record the plan only as far as it supports review of coverage.
3. **Search for primary sources first.** Secondary material is used only to add context or to locate primary sources. Marketing material is not treated as proof of capability.
4. **Consume non-textual sources only through an extraction performed under `WF-011`.** A source supplied as DOCX, PDF, XLSX, PPTX, or an image is not read directly by the Research Agent. The Software Architect coordinates a local extraction to text under [`WF-011`](./document-extraction.md) and supplies the extracted fragments together with the extraction record — tool and version, encoding, output location, and recorded losses. The Research Agent does not extract, does not install or run tools, does not request a shell, and does not attempt to read a document format it cannot open. Where the material is not readable, the Research Agent records the source as inaccessible with the reason and does not cite it as though it had been read; where the material arrives as an extract, the Research Agent states which fragments it actually read and what the extraction did not preserve.
5. **Verify material claims against official documentation.** Distinguish documented capability, documented limitation, vendor claim, third-party report, and agent inference. Where documentation is silent, the gap is recorded.
6. **Record each source with the required fields.** Title, publisher or organization, URL, publication or update date, access date, relevant version or edition, the finding supported, and limitations. Where a field is genuinely unavailable, record `Not available` rather than omitting it.
7. **State version applicability.** A version-specific claim names its version. Where applicability to other versions is unknown, state that it is unknown.
8. **Note dependencies and licensing conditions.** Record operational prerequisites, contractual constraints, licensing models, and cost conditions that affect the finding. Pricing is recorded with its basis, currency, and the date and source of the figure.
9. **Compare alternatives on the pre-defined criteria.** Apply the same criteria to each option. Include rejected options and the reason for rejection. Where an alternative could not be assessed, record `Not assessed` with the reason rather than scoring it arbitrarily.
10. **Record limitations and uncertainties explicitly.** Include limitations of the evidence base itself, such as reliance on a single vendor, absence of primary sources, or unavailability of a paid tier.
11. **Classify each finding.** Use `CONFIRMED` only where reliable cited evidence supports it; `ASSUMPTION` where the finding is provisionally accepted; `RECOMMENDATION` for professional judgement; `OPEN QUESTION` where information is still required. Do not merge findings that carry different classifications.
12. **State confidence and its basis.** Confidence is expressed with the reason it is high, medium, or low — for example, single source, undated documentation, or a behavioral claim not documented anywhere.
13. **Separate recommendation from evidence.** Recommendations are stated with their reasoning and marked as not approved. A recommendation never appears inside the findings register as a finding.
14. **List what remains unresolved.** Record open questions, including what further investigation would resolve them and whether the Research Agent or a third party must act.
15. **Report to the Software Architect using the required report structure.** The report follows the structure in the Research Agent definition §7 and the research report template: objective, scope, findings, technical details, alternatives, sources and evidence, risks and limitations, open questions, recommendations, executive summary.
16. **Support evaluation.** The Software Architect assesses whether the evidence meets the threshold, whether the limitations undermine the conclusion, and which decisions the findings can inform. The Research Agent answers clarification requests; it does not defend a recommendation.
17. **Persist the report only if authorized.** Under `WF-006` conventions, the Documentation Agent writes the report to `docs/04-research/` using the research report template, preserving attribution, date or session context, findings, severity of limitations, and open questions. Persistence is not validation and not approval.
18. **Use the findings in the commissioning workflow.** The findings feed `WF-002`, `WF-003`, or `WF-004` decisions. The receiving workflow records which findings were used, and any decision taken in spite of a stated limitation.
19. **Re-examine when evidence changes.** If later evidence contradicts a persisted finding, do not rewrite the original finding; record the new evidence, the correction, and its effect under `WF-009` where the finding supported an approved decision.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Research Agent | A defined research question with scope, exclusions, criteria, and evidence threshold. | One coherent question set per assignment; no instruction to reach a particular conclusion. |
| Research Agent | Software Architect | Findings, sources, limitations, alternatives, open questions, recommendations. | No file writes; no decisions; no claims about sources not consulted. |
| Software Architect | Documentation Agent | Persist a specific research report. | Explicit target path under `docs/04-research/`; preserve attribution and findings verbatim in substance. |
| Documentation Agent | Software Architect | Report of what was persisted and what could not be preserved as supplied. | Must not strengthen, soften, merge, or reorder findings. |
| Software Architect | Validation Agent | Review whether evidence in deliverables is sufficient and identifiable. | Read-only; cannot verify sources it did not access; cannot conduct web research. |
| Validation Agent | Software Architect | Evidence-quality findings with severity. | Does not verify or endorse the research conclusion. |

The Research Agent does not delegate, does not request its own follow-on work, and does not communicate directly with the human user. All findings travel through the Software Architect.

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Research report | Research Agent | Structured findings report delivered to the Software Architect. |
| Source register | Research Agent | Sources with title, publisher, URL, dates, version, supported finding, and limitations. |
| Findings register | Research Agent | Classified findings with confidence and limits. |
| Alternatives comparison | Research Agent | Options assessed on pre-defined criteria, including rejected options. |
| Limitations and open questions | Research Agent | What could not be established and what would establish it. |
| Recommendations | Research Agent | Professional judgement with reasoning and an explicit not-approved status. |
| Persisted research report (conditional) | Documentation Agent | File under `docs/04-research/`, only on explicit authorization, following the research report template. |
| Decision input record | Software Architect | Which findings informed which decision, recorded in the receiving workflow. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Structure for a persisted report, aligned with the Research Agent's required report structure. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | Consumer of research evidence in Phase 1; its sources and limitations sections mirror the research evidence fields. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Consumer of technology research; options and drivers reference research findings. |
| Software Requirements Specification template | [`framework/templates/software-requirements-specification.md`](../templates/software-requirements-specification.md) | Consumer of integration and feasibility evidence attached to `INT` and `NFR` entries. |
| Documentation Standards §7 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Source preference order, required source record fields, and evidence discipline. |
| Research Agent definition | [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md) | Research method, required evidence fields, and required report structure. |

**Template availability (observed 2026-11-10).** A research report template exists and is the only artifact of this workflow with a dedicated template. Source registers and findings registers are sections of that template. No separate template is required by this workflow, and none may be created without authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Question scoped before search | Software Architect | No research proceeds on an undefined question or an undefined decision. |
| Criteria before assessment | Software Architect | Comparison criteria are fixed before alternatives are scored. |
| Source record completeness | Research Agent | Every material external claim has the §7.2 fields, with `Not available` where a field is genuinely missing. |
| Extraction before consumption | Software Architect, Research Agent | No source in DOCX, PDF, XLSX, PPTX, or image form is consumed before a `WF-011` extraction has produced readable text with a recorded tool, version, encoding, and losses; the Research Agent neither extracts nor requests shell access. |
| No false reading claims | Research Agent | The Research Agent does not claim to have read or validated a source it did not access, states which fragments of an extract it actually read, and reports unreadable sources as inaccessible rather than citing them. |
| No invented sources | Research Agent | Nothing is cited that was not consulted; nothing is reconstructed from memory. |
| Capability versus claim | Research Agent | Documented capability, vendor claim, third-party report, and inference are distinguished. |
| Version applicability | Research Agent | Version-specific claims name the version; unknown applicability is stated. |
| Limitation disclosure | Research Agent | Limitations affecting a finding appear with the finding, not only in a closing note. |
| Classification integrity | Research Agent | Findings carry one label each; recommendations are not recorded as findings. |
| Persistence fidelity | Documentation Agent | The persisted report preserves findings, severity, and limitations as reported. |
| Independent evidence review | Validation Agent, under `WF-007` | Reviews whether cited evidence is identifiable and adequate for the claim, using only available material. |

Persisting a report is not independent validation. Neither the Documentation Agent nor the Research Agent may describe a persisted report as validated or approved.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Whether a research-dependent decision is accepted | Human user | At the decision point in `WF-002`, `WF-003`, or `WF-004` | Research informs the decision; it does not constitute it. |
| Acceptance of a recommendation derived from research | Human user | With the decision package presented by the Software Architect | A recommendation remains a recommendation until approved. |
| Acceptance of residual uncertainty in a decision | Human user, on the Software Architect's presentation | When the evidence threshold was not met | The limitation is recorded against the decision, not absorbed into the prose. |
| Approval of expenditure implied by a researched option | Human user | Before any cost is committed | Research provides pricing evidence, not budget approval. |
| Approval for external access or paid source retrieval, where required by the permission model | Human user or the configured permission authority | Before the access occurs | The Research Agent does not bypass an access decision. |

This workflow has no intrinsic approval gate of its own. Its outputs acquire approval status only through the decisions they inform, recorded through `WF-008`.

---

## 13. Completion Criteria

A research assignment under this workflow is complete when all of the following hold:

- [ ] The question, the decision it supports, the scope, the exclusions, and the evidence threshold are recorded.
- [ ] Comparison criteria were defined before alternatives were assessed, where alternatives were compared.
- [ ] Primary and official sources were preferred, and secondary sources are identified as such.
- [ ] Every material claim has a source record with the required fields, or an explicit statement that a field is unavailable.
- [ ] Documented capability is distinguished from vendor claim, third-party report, and inference.
- [ ] Version applicability and dependencies are stated.
- [ ] Limitations of the evidence are recorded with the affected findings.
- [ ] Each finding carries exactly one classification, and confidence is stated with its basis.
- [ ] Recommendations are separate, reasoned, and marked as not approved.
- [ ] Unresolved questions are listed with what would resolve them.
- [ ] The report was delivered to the Software Architect in the required structure.
- [ ] Persistence, if it occurred, was explicitly authorized, and the persisted record preserves attribution and findings.
- [ ] No repository file was written by the Research Agent.

---

## 14. Exception Handling

### 14.1 Insufficient information

Where the available evidence cannot answer the question, the report says so and classifies the affected conclusion as `OPEN QUESTION`. A partial answer is reported as partial, with the boundary of what was established stated explicitly. Silence from the documentation is a finding about the documentation, not proof of absence.

### 14.2 Contradictory sources

Where two sources disagree, both are recorded with their locations, dates, and versions, and the discrepancy is reported as unresolved rather than reconciled. Where an official source and a secondary source disagree, the official source is identified as such and the discrepancy still stands as a finding for the Software Architect.

### 14.3 Inaccessible sources

Paywalled, region-restricted, removed, or login-gated sources are recorded as inaccessible with the reason, and the affected finding is downgraded or marked unverified. An inaccessible source is not cited as if it had been read.

### 14.4 Unverifiable claims

Claims that cannot be verified are marked unverified and classified `ASSUMPTION` or `OPEN QUESTION`, with the reason and the effect on the conclusion. The Research Agent does not present an inference as a documented capability and does not describe an untested behavior as supported.

### 14.5 Findings and blockers

A finding from the Validation Agent about evidence quality is handled under `WF-007`. A blocker for research is a question that cannot be answered with available access or evidence; it is reported to the Software Architect with the reason, rather than answered by loosening the evidence threshold without authorization.

### 14.6 Persistence requests and report integrity

Persistence is an authorization, not an expectation. If the Software Architect has not authorized persistence, the Research Agent's report remains a report to the Architect. If a persisted report is later found to have altered a finding's severity or limitations, the correction is recorded as an amendment with its reason, and the original text is preserved.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-005-01` | Is a report date always available, or should the persistence convention accept `Not available`? | The research report template requires a date or session context; behavior when neither exists is unstated. | Software Architect |
| `OQ-WF-005-02` | Should framework-level research (for example, research supporting a standards change) be persisted under `docs/04-research/` or kept outside project documentation? | `docs/04-research/` is described as project records, and a framework research record may not belong there. | Software Architect |
| `OQ-WF-005-03` | When research findings are reused in a later phase, must a new report be produced or may the earlier report be referenced? | Affects whether findings can be relied upon after their original decision context has closed. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Primary consumer for feasibility, cost, and licensing evidence. |
| [`WF-003` — Requirements Analysis](./requirements-analysis.md) | Consumer for integration capability and feasibility evidence attached to requirements. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Consumer for technology, compatibility, and security-capability evidence. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked to persist a research report when authorized. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked when evidence quality in a deliverable requires independent review. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs approval of the decisions research informs. |
| [`WF-009` — Change Control](./change-control.md) | Invoked when new evidence affects a persisted finding or an approved decision. |
| [`WF-011` — Document Extraction](./document-extraction.md) | Invoked before a source supplied in DOCX, PDF, XLSX, PPTX, or image form is consumed; supplies the extracted text and its provenance to the Research Agent. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the research workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable, evidence-disciplined research procedure that separates findings, inferences, recommendations, and unknowns. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.2.0 | 2026-11-10 | Adds step 4 to §7: a source supplied as DOCX, PDF, XLSX, PPTX, or an image is consumed only through a `WF-011` extraction performed by the Software Architect, with the extraction record and its losses, and the Research Agent neither extracts nor claims to have read an inaccessible source; adds the §11 controls on extraction before consumption and on false reading claims; adds `WF-011` to the related-workflow references (metadata and §15). Correction applied within the same version after independent validation: the history reason now separates the verified shell permission from the reported model limitation (VAL-001), and the status is corrected to `In review` (VAL-008). | Record two distinct operating constraints, which are not of equal evidential standing: shell permission — verified from the agent definitions (`.opencode/agents/*.md`: Research, Validation, and Documentation have `shell: deny`; the Software Architect has `shell: ask`) — and model input modality (the models do not accept PDF or image input) — reported by the Software Architect from observation on 2026-11-10, not independently verified by a durable in-repository source. Together they mean that no non-textual source can be read directly in this system. Versioning: MINOR (additive step, control, and reference; no approved finding, rule, or boundary altered). Deferred findings VAL-005 and VAL-007 are not addressed by this correction. | Documentation Agent | Approved by Human user on 2026-11-10 — independent validation PASS WITH CONDITIONS; corrections for VAL-001 and VAL-008 verified as resolved. VAL-005 (duplicated metadata), VAL-007 ('Section structure' note), and VAL-100 ('Office document' terminology in the manifest template) are accepted as deferred/pending items, not as corrected or resolved. |
| 0.2.1 | 2026-11-11 | PATCH documentary correction: the §1 "Normative basis" now records the actual validation results — v0.1.2 PASS and v0.2.0 PASS WITH CONDITIONS, with `VAL-005`, `VAL-007`, and `VAL-100` deferred as pending items — instead of stating without qualification that the workflow was validated (PASS), and it carves out the section-structure convention, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. The already version-qualified `Authority / approval` and `Validation` metadata fields were verified and left unchanged; status remains `Approved`. No rule, procedural step, approval, or approved decision was changed. | Resolve the systemic "Normative basis / Section structure" pattern recorded in WF-009 §16 (carve-out) and correct the validation statement to the recorded result. Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — the v0.1.2 and v0.2.0 approval records stand, including PASS WITH CONDITIONS on v0.2.0 and its deferred items; v0.2.1 is a PATCH documentary correction. |
