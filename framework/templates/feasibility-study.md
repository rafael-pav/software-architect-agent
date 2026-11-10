# Feasibility Study (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Feasibility Study used in Phase 1 (Planning and Scope) to assess alternatives against technical, economic, operational, and schedule criteria and to record a recommendation with its approval status. |
| Status | Approved |
| Version | 0.1.3 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Feasibility studies stored under `docs/01-planning/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`project-charter.md`](./project-charter.md); [`research-report.md`](./research-report.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.3 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/01-planning/`.
2. Define the evaluation criteria and the comparison method **before** assessing alternatives, so that ratings cannot be reverse-engineered from a preferred option.
3. Replace every `{{ ... }}` placeholder. Figures without a documented basis must remain placeholders and be listed as `OPEN QUESTION`.
4. Remove all italic guidance notes and HTML comments before review.
5. Classify findings as `CONFIRMED`, `ASSUMPTION`, `RECOMMENDATION`, or `OPEN QUESTION`. Technical capability claims require a cited source; vendor claims are not proof.
6. Keep the recommendation explicitly a recommendation. Feasibility assessment does not select a technology, approve a budget, or authorize the project.

**Identifier scope.** Non-standard prefixes used in this template (`CRIT`, `OPT`, `ASM`, `OQ`, `RISK`, `SRC`, `DEP`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items. `DEP-NNN` denotes dependencies and is defined in [`scope-statement.md`](./scope-statement.md) §5; it is a cross-referenced scheme, so copies of its identifiers must stay consistent with the scope statement and must not diverge into a separate sequence.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Feasibility Study

| Field | Value |
| --- | --- |
| Purpose | {{The decision this study informs, for example whether to proceed, and between which alternatives.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role}} |
| Authority / approval | {{Who authorized this study; `Not approved` if the conclusion has not been approved.}} |
| Related documents | {{Charter, scope statement, research reports, decision records.}} |

## 1. Objective and decision supported

{{The question this study answers and the decision that depends on it.}}

| Aspect | Statement | Classification | Source |
| --- | --- | --- | --- |
| Decision to support | {{Decision}} | {{Label}} | {{Source}} |
| Decision owner | {{Role with authority to decide}} | {{Label}} | {{Source}} |

*Guidance: if the decision owner is unknown, this is an `OPEN QUESTION` and the study cannot be treated as decision-ready.*

## 2. Evaluation criteria

| ID | Criterion | Definition or measure | Weight or threshold | Basis | Classification |
| --- | --- | --- | --- | --- | --- |
| `CRIT-001` | {{Criterion}} | {{How it is measured or judged}} | {{Scale, weight, or minimum acceptable value}} | {{Why this criterion matters to the project}} | {{Label}} |

*Guidance: identifier scheme used here: `CRIT-NNN`. Criteria must be defined before alternatives are scored. Weights and thresholds that are proposed rather than approved stay `RECOMMENDATION`.*

## 3. Alternatives considered

| ID | Alternative | Description | Status | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| `OPT-001` | {{Alternative}} | {{Short factual description, including the option of not proceeding where relevant}} | {{Candidate / Shortlisted / Withdrawn — with reason}} | {{Label}} | {{Source}} |

*Guidance: identifier scheme used here: `OPT-NNN`. Include rejected alternatives and the reason for rejection; deleting them would hide the comparison.*

## 4. Technical feasibility

{{Whether the alternatives can be built and operated with available technology, skills, and constraints.}}

| Aspect | Finding | Affected alternatives | Classification | Evidence or source | Open question |
| --- | --- | --- | --- | --- | --- |
| {{Capability, compatibility, or limitation}} | {{Finding}} | {{OPT-00N}} | {{Label}} | {{Source reference}} | {{OQ-00N or None}} |

*Guidance: distinguish documented capability from inference and from vendor claim. Version-specific claims must name the version.*

## 5. Economic feasibility

| Cost or benefit | Alternative | Basis of estimate | Amount | Currency | Confidence | Classification | Source |
| --- | --- | --- | --- | --- | --- | --- | --- |
| {{Cost or benefit}} | {{OPT-00N}} | {{Method, assumption, or quotation}} | {{Amount or TBD}} | {{Currency}} | {{High / Medium / Low with basis}} | {{Label}} | {{Source}} |

*Guidance: no figure may be presented as confirmed without a documented basis. Total cost, recurring cost, and cost of ownership periods must state their time basis.*

## 6. Operational feasibility

{{Whether the organization can adopt, operate, support, and maintain the alternatives, including staffing, process change, and operational risk.}}

| Aspect | Finding | Affected alternatives | Classification | Evidence or source |
| --- | --- | --- | --- | --- |
| {{Aspect, for example skills, process change, support model}} | {{Finding}} | {{OPT-00N}} | {{Label}} | {{Source}} |

## 7. Schedule feasibility

| Alternative | Earliest realistic delivery | Binding dependencies | Confidence | Classification | Basis |
| --- | --- | --- | --- | --- | --- |
| {{OPT-00N}} | {{Date or duration with basis}} | {{DEP-00N or external dependency}} | {{High / Medium / Low with basis}} | {{Label}} | {{Reasoning or source}} |

*Guidance: an estimate without a stated method is not evidence. Record the method or mark the entry `OPEN QUESTION`.*

## 8. Comparative assessment

| Criterion | `{{OPT-001}}` | `{{OPT-002}}` | Basis for the rating |
| --- | --- | --- | --- |
| `CRIT-001` | {{Rating and short justification}} | {{Rating and short justification}} | {{Evidence or reasoning}} |

*Guidance: every rating must be traceable to a stated basis; unexplained scores are not decision evidence. Where an alternative could not be assessed, write `Not assessed — {{reason}}`.*

## 9. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Effect on the conclusion}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. A study whose conclusion depends on unverified assumptions must say so in §12.*

## 10. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected alternatives or criteria}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`.*

## 11. Risks and limitations of this study

| ID | Risk or limitation | Effect on the study's conclusions | Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-001` | {{Risk, for example missing cost data or unverified capability}} | {{How it weakens the assessment}} | {{Response}} | {{Role}} | {{Open / Mitigated / Accepted / Closed}} |

*Guidance: identifier scheme used here: `RISK-NNN`. Limitations of the available evidence belong here, not only in the sources table.*

## 12. Recommendation and approval status

**Recommendation.** {{The recommended alternative, stated as a recommendation.}}

**Reasoning.** {{Why this alternative is preferred, referring to `CRIT-NNN` and the evidence in §4 to §8.}}

**Conditions and caveats.** {{What must be true, verified, or decided for the recommendation to hold.}}

| Field | Value |
| --- | --- |
| Classification | `RECOMMENDATION` |
| Approval status | {{Not approved / Approved — with approver and date}} |
| Approving role | {{Role with authority to select the option}} |
| Evidence of approval | {{Recorded approval reference, or None}} |

*Guidance: a feasibility study informs a decision; it does not make one. If approval exists, cite where it was recorded, and do not describe the recommendation as confirmed until then.*

## 13. Sources and evidence

| ID | Source title | Publisher or organization | URL | Publication or update date | Access date | Version or edition | Finding supported | Limitations |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `SRC-001` | {{Title}} | {{Publisher}} | {{URL}} | {{Date or Not available}} | {{YYYY-MM-DD}} | {{Version or Not stated}} | {{Finding or section}} | {{Limitations or uncertainty}} |

*Guidance: identifier scheme used here: `SRC-NNN`. Cite only sources actually consulted or supplied. Where a field is genuinely unavailable, write `Not available` rather than omitting it. No source may be reconstructed from memory.*

## 14. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Internal document or register}} | {{What it supports}} | {{Repository-relative path and section anchor}} |

## 15. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
