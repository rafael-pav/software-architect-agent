# Research Report (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for persisting a Research Agent report under `docs/04-research/`, following the report structure required by the Research Agent definition. |
| Status | Approved |
| Version | 0.1.3 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Persisted research reports stored under `docs/04-research/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`feasibility-study.md`](./feasibility-study.md); `.opencode/agents/research-agent.md` §7. |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.3 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. This template is used by the Documentation Agent when the Software Architect authorizes persistence of a Research Agent report. The Research Agent does not write repository files.
2. Copy everything from the *Project document skeleton* marker into the target file under `docs/04-research/`.
3. Preserve the Research Agent's findings, evidence, classifications, and limitations as reported. Do not strengthen, soften, summarise away, or reorder findings to make them more conclusive.
4. Replace every `{{ ... }}` placeholder except placeholders inside quoted agent findings; a finding that was not supplied must not be reconstructed. Where the Research Agent reported no value, write `Not available` rather than inventing one.
5. Remove all italic guidance notes and HTML comments before review.
6. Record the report's provenance (author, date, session context, and the authorization for persistence) in the metadata block.
7. State explicitly that persisting the report is not independent validation and not approval.
8. Keep the agent's original findings distinguishable from any later Software Architect decision or human approval. Later decisions belong in §11, not in a rewritten §3.

**Identifier scope.** Non-standard prefixes used in this template (`FND`, `OPT`, `SRC`, `RISK`, `OQ`, `REC`, `ASM`, `ADR`, `DEC`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items. Two of these prefixes are cross-referenced schemes rather than schemes local to this template: `ADR-NNN` denotes architecture decisions and is defined in [`architecture-decision-record.md`](./architecture-decision-record.md) §1, and `DEC-NNN` denotes the project-wide decision register and is defined in [`project-charter.md`](./project-charter.md) §11 (used for architecture-level approvals in [`architecture-overview.md`](./architecture-overview.md) §12). Identifiers cited here must match the originating register and must not be renumbered or duplicated in this report.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# Research Report — {{Research topic}}

| Field | Value |
| --- | --- |
| Purpose | {{The decision or requirement this research supports, and why the report is being retained.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | Documentation Agent (persistence and maintenance only; findings remain attributed to the Research Agent). |
| Authority / approval | {{Persistence authorized by the Software Architect on YYYY-MM-DD. Report content not approved; approvals of resulting decisions are recorded separately.}} |
| Related documents | {{Requirements, feasibility study, architecture decision records, and other documents that use these findings.}} |
| Report author | Research Agent. |
| Report date or session context | {{Date, or the session or assignment reference supplied by the Software Architect.}} |
| Classification of report | {{CONFIRMED / ASSUMPTION / RECOMMENDATION / OPEN QUESTION as a whole, or `Mixed — see per-statement classifications`.}} |
| Independent validation | {{Not independently validated / Validated — with validation report reference and date}} |

## 1. Research Objective

{{The question investigated and the decision or requirement it supports, as stated in the research assignment.}}

| Aspect | Value |
| --- | --- |
| Research question | {{Question}} |
| Decision or requirement supported | {{FR-00N, ADR-00N, feasibility question, or other reference}} |
| Requester | {{Software Architect}} |
| Date assigned | {{YYYY-MM-DD or Not available}} |

## 2. Scope

**Investigated:** {{Topics, products, versions, and criteria included in the investigation.}}

**Excluded:** {{Topics deliberately not investigated, and the reason.}}

*Guidance: state which product versions, editions, or time periods the findings apply to. Findings without a stated applicability scope cannot be reused safely.*

## 3. Findings

### 3.1 Findings register

| ID | Finding | Classification | Evidence reference | Confidence and limits |
| --- | --- | --- | --- | --- |
| `FND-001` | {{Finding as reported by the Research Agent}} | {{CONFIRMED / ASSUMPTION / RECOMMENDATION / OPEN QUESTION}} | {{SRC-00N or internal reference}} | {{Certainty, version dependency, or limitation}} |

*Guidance: identifier scheme used here: `FND-NNN`. `CONFIRMED` requires reliable cited evidence. Vendor claims, inferences, and community reports must not be recorded as confirmed capability. Do not merge findings that carry different classifications.*

### 3.2 Assumptions recorded during research

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Effect on the findings}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. Assumptions must not be promoted to `CONFIRMED` by the act of persistence.*

### 3.3 Unverified claims

| Claim | Why it could not be verified | Effect on the conclusions | Status |
| --- | --- | --- | --- |
| {{Claim}} | {{Reason}} | {{Effect}} | {{Open / Withdrawn}} |

*Guidance: keep unverified claims visible. Delete this subsection only if no unverified claim was recorded, and state that explicitly.*

## 4. Technical Details

{{Relevant capabilities, limitations, dependencies, compatibility, version considerations, operational requirements, and licensing conditions, as reported.}}

| Aspect | Detail | Applies to version | Classification | Source |
| --- | --- | --- | --- | --- |
| {{Aspect}} | {{Detail}} | {{Version, generation, or edition}} | {{Label}} | {{SRC-00N}} |

*Guidance: distinguish documented capability from inference. Where applicability to other versions is unknown, say so.*

## 5. Alternatives

| ID | Alternative | Assessment | Advantages | Disadvantages | Classification |
| --- | --- | --- | --- | --- | --- |
| `OPT-001` | {{Alternative}} | {{What was examined}} | {{Advantages, with evidence}} | {{Disadvantages, with evidence}} | {{Label}} |

*Guidance: identifier scheme used here: `OPT-NNN`. Compare alternatives on consistent criteria; state the criteria. Do not recommend an option because it is popular.*

## 6. Sources and Evidence

| ID | Source title | Publisher or organization | URL | Publication or update date | Access date | Version or edition | Finding supported | Limitations |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `SRC-001` | {{Title}} | {{Publisher}} | {{URL}} | {{Date or Not available}} | {{YYYY-MM-DD}} | {{Version or Not stated}} | {{FND-00N}} | {{Limitations, uncertainty, licensing}} |

*Guidance: identifier scheme used here: `SRC-NNN`. Record only sources actually consulted or supplied. Where a field is genuinely unavailable, write `Not available`. Never reconstruct a URL, date, or capability from memory.*

## 7. Risks and Limitations

| ID | Risk or limitation | Affected findings | Severity or impact | Mitigation or handling | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-001` | {{Risk, for example a version dependency or an unsupported claim}} | {{FND-00N}} | {{Impact}} | {{Handling}} | {{Open / Mitigated / Accepted}} |

*Guidance: identifier scheme used here: `RISK-NNN`. Include limitations of the evidence base itself, such as reliance on vendor documentation or absence of primary sources.*

## 8. Open Questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Status |
| --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected findings or decisions}} | {{Role}} | {{Date or milestone}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. Items that require further investigation by the Research Agent must say so.*

## 9. Recommendations

| ID | Recommendation | Reasoning | Depends on findings | Approval status |
| --- | --- | --- | --- | --- |
| `REC-001` | {{Recommendation}} | {{Why, referring to findings and alternatives}} | {{FND-00N}} | {{Not approved / Approved — approver and date}} |

*Guidance: identifier scheme used here: `REC-NNN`. Recommendations are professional judgement, not decisions. Do not describe a recommendation as approved unless a recorded human approval exists.*

## 10. Executive Summary

{{A concise summary for the Software Architect: the question, the key findings, the principal uncertainty, and what decision the research supports.}}

*Guidance: the summary must not state more certainty than the findings support, and must not omit material limitations.*

## 11. Status of findings after review

| Finding or recommendation | Status after review | Decision reference | Date | Note |
| --- | --- | --- | --- | --- |
| {{FND-00N or REC-00N}} | {{Open / Accepted / Rejected / Superseded}} | {{ADR-00N, DEC-00N, or None}} | {{YYYY-MM-DD}} | {{Reason or correction}} |

*Guidance: this table records later decisions and corrections without altering the original findings. Delete this section only if no review has yet occurred, and write `Not applicable — no review recorded`.*

## 12. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

*Guidance: persistence edits (formatting, metadata, and attribution) must be described as such and must not be presented as changes to the research conclusions.*

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
