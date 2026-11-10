# Architecture Decision Record (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a single Architecture Decision Record (`ADR-NNN`) used in Phase 3 (System Design and Architecture) to record context, options, the decision, its rationale, consequences, and approval. |
| Status | Approved |
| Version | 0.1.4 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Architecture decision records stored under `docs/03-architecture/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`architecture-overview.md`](./architecture-overview.md); [`requirements-traceability-matrix.md`](./requirements-traceability-matrix.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.4 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/03-architecture/`. Use one file per decision and include the identifier in the file name if the project convention requires it.
2. Assign the `ADR-NNN` identifier once; identifiers are never reused or renumbered.
3. Replace every `{{ ... }}` placeholder and remove all italic guidance notes and HTML comments.
4. Record the context and options **before** the decision, so the record shows what was actually weighed. Do not write a record that only justifies a choice already made without stating the alternatives.
5. Preserve the record. Do not rewrite an accepted decision to improve its justification; record corrections and supersessions as dated amendments, and keep records whose decision status is `Superseded` visible with a link to their replacement.
6. Distinguish the decision from its approval. A decision is `Accepted` only when the authorized human role approved it and the approval is recorded; agent authorship is not approval.
7. Two status vocabularies apply to this document and must not be conflated. The decision-status vocabulary `Proposed / Accepted / Rejected / Superseded / Deprecated` is the item-level *decision* status recorded in §1 as `Decision status`; it does not replace the mandatory document-status vocabulary `Draft / In review / Approved / Superseded / Withdrawn` required by the documentation standard §9.2, which governs this document's own metadata `Status` field and its change history.

**Identifier scope.** Non-standard prefixes used in this template (`ADR`, `DRV`, `OPT`, `ASM`, `OQ`, `DEC`, `RISK`, `AC`, `TST`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items. `ADR-NNN` denotes architecture design decisions. It is distinct from the generic `DEC-NNN`, which denotes approval decisions recorded in the project decision register (including architecture-level approvals recorded outside the ADR register). `DEC` is referenced in this template only for disambiguation and is not used in its skeleton.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# `{{ADR-001}}` — {{Decision title}}

| Field | Value |
| --- | --- |
| Purpose | {{Why this record exists and which design question it settles.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Role accountable for maintaining the record}} |
| Authority / approval | {{Approver and approval date, or `Not approved` / `Pending` with the approver named.}} |
| Applies to | {{Component, interface, technology area, or architectural concern governed by this decision.}} |
| Related documents | {{Architecture overview, requirements specification, superseded or related decision records.}} |

## 1. Decision status and identification

| Field | Value |
| --- | --- |
| Decision ID | `ADR-001` |
| Decision title | {{Short imperative or descriptive title}} |
| Decision status | {{Proposed / Accepted / Rejected / Superseded / Deprecated}} |
| Decision status date | {{YYYY-MM-DD}} |
| Proposed by | {{Role}} |
| Approving role | {{Human role with authority, or Not assigned}} |
| Supersedes | {{ADR-00N or None}} |
| Superseded by | {{ADR-00N or None}} |
| Related decisions | {{ADR-00N or None}} |

*Guidance: a record whose decision status is `Superseded` must name its replacement, and the replacement must name the record it supersedes.*

## 2. Context and problem statement

{{The situation that requires a decision: the forces at play, the constraints, and the question to be answered.}}

| Aspect | Statement | Classification | Source |
| --- | --- | --- | --- |
| Driving requirement or constraint | {{Statement}} | {{Label}} | {{FR-00N, NFR-00N, SEC-00N, or other source}} |
| Problem to be resolved | {{Statement}} | {{Label}} | {{Source}} |

*Guidance: state the problem in terms a reviewer can disagree with. "We need a database" is not a problem statement.*

## 3. Decision drivers and constraints

| ID | Driver or constraint | Type | Weight or binding nature | Classification | Source |
| --- | --- | --- | --- | --- | --- |
| `DRV-001` | {{Driver}} | {{Requirement / Technical constraint / Organizational constraint / Regulatory / Cost / Schedule}} | {{Must satisfy / Should satisfy / Nice to have}} | {{Label}} | {{Source}} |

*Guidance: identifier scheme used here: `DRV-NNN`. Drivers must trace to requirements, constraints, or recorded stakeholder priorities; an agent's preference is not a driver.*

## 4. Options considered

| ID | Option | Description | Advantages | Disadvantages and risks | Classification |
| --- | --- | --- | --- | --- | --- |
| `OPT-001` | {{Option}} | {{Factual description}} | {{Advantages, with basis}} | {{Disadvantages and risks, with basis}} | {{Label}} |

*Guidance: identifier scheme used here: `OPT-NNN`. Include the option of not changing the current state where relevant, and include rejected options with the reason for rejection. Capability claims require a cited source.*

## 5. Decision

{{The decision, stated in one or two sentences, in the active voice, in terms that can be checked against the design.}}

*Guidance: if the decision is still under consideration, the status is `Proposed` and this section states the currently proposed option, not a settled outcome.*

## 6. Rationale

{{Why this option was chosen over the alternatives, referring to `DRV-NNN` and to the evidence gathered.}}

*Guidance: identify the trade-offs that were accepted, and state which drivers were not fully satisfied. A rationale that claims every advantage and no cost is not credible.*

## 7. Consequences

| Consequence type | Description | Affected elements | Follow-up action | Owner |
| --- | --- | --- | --- | --- |
| Positive | {{Benefit}} | {{Components, requirements}} | {{None}} | {{Role}} |
| Negative | {{Cost, limitation, or constraint introduced}} | {{Components, requirements}} | {{Mitigation or acceptance}} | {{Role}} |
| Risk | {{New risk introduced by the decision}} | {{Components}} | {{Mitigation, with `RISK-00N` reference}} | {{Role}} |
| Follow-up | {{Work required to realize or revisit the decision}} | {{Documents or components}} | {{Action}} | {{Role}} |

*Guidance: consequences include documentation, operational, and maintenance effects, not only functional ones. New risks must be entered in the risk register.*

## 8. Related requirements and traceability

| Business rule | Requirement | Use case or user story | Acceptance criteria | Future test |
| --- | --- | --- | --- | --- |
| {{BR-00N or None — reason}} | {{FR-00N, NFR-00N, SEC-00N}} | {{UC-00N or None — reason}} | {{AC-00N}} | {{TST-00N}} |

*Guidance: a decision with no supporting requirement or constraint is a traceability defect and must be reported. Mirror these links in the requirements traceability matrix.*

## 9. Verification of realization

{{How compliance with this decision can be observed in later reviews or validation activities, without turning this document into implementation guidance.}}

*Guidance: describe verification at the level of architecture review, configuration inspection, or acceptance criteria. Do not describe code, scripts, or infrastructure tooling.*

## 10. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Effect on the decision}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. An assumption underpinning an accepted decision must remain visible even after acceptance.*

## 11. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Status |
| --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Effect on the decision or its consequences}} | {{Role}} | {{Date or milestone}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. A decision made while a material question remains open must say so in §5 or §6.*

## 12. Approval record

| Field | Value |
| --- | --- |
| Approver | {{Named human role, or None}} |
| Approval date | {{YYYY-MM-DD or Pending}} |
| Approval basis | {{Review, validation reference, or decision meeting record}} |
| Approval evidence | {{Reference to where the approval is recorded, or None}} |
| Conditions attached | {{Conditions, or None}} |

*Guidance: validation by another agent is not approval. If only a recommendation exists, the status remains `Proposed` and this table must say so.*

## 13. Amendment log

| Date | Amendment | Reason | Authorized by |
| --- | --- | --- | --- |
| {{YYYY-MM-DD}} | {{What changed, and what was preserved}} | {{Why}} | {{Role}} |

*Guidance: amendments clarify or annotate a record. They must not rewrite the original decision or rationale. Delete this table only if no amendment has been made and state `Not applicable — no amendments`.*

## 14. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or source}} | {{What it supports}} | {{Repository-relative path, section anchor, or URL with access date}} |

## 15. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
