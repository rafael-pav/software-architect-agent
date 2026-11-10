# Validation Report (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for persisting an independent Validation Agent report under `docs/05-validation/`, following the report structure required by the Validation Agent definition. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Persisted validation reports stored under `docs/05-validation/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`requirements-traceability-matrix.md`](./requirements-traceability-matrix.md); `.opencode/agents/validation-agent.md` §7. |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. This template is used by the Documentation Agent when the Software Architect authorizes persistence of a Validation Agent report. The Validation Agent does not write repository files.
2. Copy everything from the *Project document skeleton* marker into the target file under `docs/05-validation/`.
3. Preserve every finding, its severity, its identifiers, and its affected document path exactly as reported. Findings must not be removed, softened, merged, or downgraded during persistence.
4. Replace every `{{ ... }}` placeholder except quoted findings. Do not infer a result or a finding that the Validation Agent did not report.
5. Remove all italic guidance notes and HTML comments before review.
6. Mark the report as an independent review of the documents inspected. Do not extend its conclusions to documents that were not reviewed.
7. Record the report's provenance and the authorization for persistence. Persisting a validation report does not make its findings resolved and does not approve any document.
8. Record subsequent corrections and decisions in §10, with their status, rather than rewriting the original findings.

**Identifier scope.** Non-standard prefixes used in this template (`VAL`, `ASM`, `OQ`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# Independent Validation Report — {{Scope of review}}

| Field | Value |
| --- | --- |
| Purpose | {{What was reviewed, for which phase or milestone, and what decision the report informs.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | Documentation Agent (persistence and maintenance only; findings remain attributed to the Validation Agent). |
| Authority / approval | {{Persistence authorized by the Software Architect on YYYY-MM-DD. Report content not approved; phase-gate outcome determined by the Software Architect with the required human approvals.}} |
| Related documents | {{Reviewed documents, earlier validation reports, traceability matrix, and affected deliverables.}} |
| Report author | Validation Agent (independent reviewer). |
| Review date or session context | {{Date, or the session or assignment reference supplied by the Software Architect.}} |
| Review iteration | {{First review / Re-review of `VAL-00N` findings / Follow-up review}} |

## 1. Review Information

| Field | Value |
| --- | --- |
| Lifecycle phase | {{Phase 1 Planning and Scope / Phase 2 Requirements Analysis / Phase 3 System Design and Architecture / Cross-phase}} |
| Review scope | {{Deliverables, sections, identifiers, and criteria within scope}} |
| Documents reviewed | {{Paths with versions or dates — see §1.1}} |
| Review basis | {{Instructions, standards, and criteria applied}} |
| Review limitations | {{Constraints affecting the review, or None identified}} |

### 1.1 Documents reviewed

| Document | Path | Version or date reviewed | Sections or identifiers examined | Completeness of review |
| --- | --- | --- | --- | --- |
| {{Title}} | {{Repository-relative path}} | {{Version or date}} | {{Sections, identifiers, or Whole document}} | {{Complete / Partial — reason}} |

*Guidance: list only documents actually inspected. A document that was unavailable must appear in §9, not as reviewed.*

## 2. Executive Summary

{{Overall quality of the submitted material and the most important concerns, in a few sentences.}}

**Overall assessment:** {{Sound / Sound with concerns / Significant concerns / Not assessable}}

**Most significant findings:** {{VAL-00N, VAL-00N — one line each}}

*Guidance: the summary must be consistent with §3 and §4. Do not describe the material as approved, accepted, or final.*

## 3. Validation Results

| Dimension | Result | Evidence reviewed | Limitations |
| --- | --- | --- | --- |
| Completeness | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Consistency | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Requirements quality | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Traceability | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Evidence and sources | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Technical feasibility | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Security and privacy | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |
| Architecture quality | {{PASS / PARTIAL / FAIL / NOT APPLICABLE}} | {{What was checked}} | {{Limitation or None}} |

*Guidance: `NOT APPLICABLE` must state why the dimension does not apply to this review. A dimension cannot be marked `PASS` on the basis of material that was not examined.*

## 4. Findings

### 4.1 Findings register

| ID | Severity | Affected document and path | Section or identifier | Description | Why it matters | Recommended corrective action | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `VAL-001` | {{CRITICAL / HIGH / MEDIUM / LOW / INFORMATIONAL}} | {{Title and exact repository-relative path}} | {{Section number or FR-00N}} | {{The issue, stated precisely}} | {{Consequence if uncorrected}} | {{Action for the Documentation Agent or Software Architect}} | {{Open / Correction requested / Correction proposed / Resolved — verified / Accepted as risk}} |

*Guidance: keep finding identifiers stable across review iterations. Severity must not be reduced during persistence. A finding is `Resolved` only after the corrected document was checked, not when a correction was merely proposed.*

### 4.2 Critical and high findings requiring action before the phase gate

| ID | Finding | Required action | Owner |
| --- | --- | --- | --- |
| {{VAL-00N}} | {{One-line description}} | {{Action}} | {{Role}} |

*Guidance: if no critical or high findings were raised, write `None` and state the basis on which that conclusion was reached.*

## 5. Traceability Review

{{Summary of missing, incomplete, or inconsistent relationships found during the review.}}

| Chain link | Assessment | Affected identifiers | Finding reference |
| --- | --- | --- | --- |
| Business Rule → Requirement | {{Complete / Incomplete / Not assessable}} | {{Identifiers}} | {{VAL-00N or None}} |
| Requirement → User Story / Use Case | {{Complete / Incomplete / Not assessable}} | {{Identifiers}} | {{VAL-00N or None}} |
| User Story / Use Case → Architecture Decision | {{Complete / Incomplete / Not assessable}} | {{Identifiers}} | {{VAL-00N or None}} |
| Architecture Decision → Acceptance Criteria | {{Complete / Incomplete / Not assessable}} | {{Identifiers}} | {{VAL-00N or None}} |
| Acceptance Criteria → Future Test | {{Complete / Incomplete / Not assessable}} | {{Identifiers}} | {{VAL-00N or None}} |

*Guidance: document the exceptions that were accepted as justified and the defects that were not. Unresolved gaps remain open findings.*

## 6. Assumptions and Open Questions

| ID | Item | Type | Effect on the validation | Owner / resolver | Status |
| --- | --- | --- | --- | --- | --- |
| {{ASM-00N or OQ-00N}} | {{Assumption or question}} | {{ASSUMPTION / OPEN QUESTION}} | {{How it limits or conditions the conclusions}} | {{Role}} | {{Open / Resolved — with resolution}} |

*Guidance: use the identifiers already assigned by the reviewed documents where they exist; otherwise describe the item and its source. Do not leave unresolved information that materially weakens the review undocumented.*

## 7. Phase Gate Recommendation

| Field | Value |
| --- | --- |
| Recommendation | {{PASS / PASS WITH CONDITIONS / FAIL / INCOMPLETE REVIEW}} |
| Reasoning | {{Why this outcome follows from §3 and §4}} |
| Conditions to be tracked | {{Conditions and owners, or None}} |
| Blocking findings | {{VAL-00N references, or None}} |

*Guidance: `PASS` requires that no blocking findings remain and the applicable criteria are satisfied. `PASS WITH CONDITIONS` requires named, tracked, non-blocking actions. `FAIL` requires at least one blocking finding. `INCOMPLETE REVIEW` applies when required evidence or documents were unavailable.*

**Authority statement.** {{State that this is a recommendation only: the Validation Agent cannot approve scope, budget, requirements, technology, or architecture, cannot waive approvals, and cannot declare the phase complete.}}

## 8. Recommendations

| Priority | Recommendation | Addressed to | Related findings |
| --- | --- | --- | --- |
| {{1}} | {{Action}} | {{Software Architect / Documentation Agent}} | {{VAL-00N}} |

*Guidance: order recommendations by importance for the next decision point. Recommendations are not corrections and do not imply that corrections were made.*

## 9. Validation Limitations

{{What could not be verified, and why: unavailable documents, inaccessible systems, unverifiable claims, or scope restrictions.}}

| Limitation | Affected conclusions | Effect |
| --- | --- | --- |
| {{Limitation}} | {{Sections or findings}} | {{How the conclusion is weakened}} |

*Guidance: include limitations that arise from the review method itself, such as review of a summary rather than a primary source. Do not present an inference as a verified fact.*

## 10. Finding status after review

| Finding | Status after review | Corrective action taken | Verified by | Date | Note |
| --- | --- | --- | --- | --- | --- |
| {{VAL-00N}} | {{Open / Resolved — verified / Accepted as risk / Superseded}} | {{What was changed, with document and version}} | {{Reviewer or role}} | {{YYYY-MM-DD}} | {{Reason or residual concern}} |

*Guidance: this table records outcomes without rewriting §4. A correction that has not been re-reviewed stays `Correction proposed`. Downgrading or dismissing a finding requires a recorded Software Architect decision, not a persistence edit.*

## 11. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
