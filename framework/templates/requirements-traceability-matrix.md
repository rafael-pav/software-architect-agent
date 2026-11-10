# Requirements Traceability Matrix (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Requirements Traceability Matrix (RTM) used in Phase 2 (Requirements Analysis) to record the chain Business Rule → Requirement → User Story / Use Case → Architecture Decision → Acceptance Criteria → Future Test, its documented exceptions, and its defects. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Traceability matrices stored under `docs/02-requirements/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`software-requirements-specification.md`](./software-requirements-specification.md); [`use-case.md`](./use-case.md); [`architecture-decision-record.md`](./architecture-decision-record.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/02-requirements/`.
2. Decide the matrix granularity before populating it: one row per requirement is the recommended default. Record the decision in §1.
3. Replace every `{{ ... }}` placeholder and remove all italic guidance notes and HTML comments.
4. Use stable identifiers only. Prose descriptions, section titles, and file names are not traceability links.
5. Record a documented exception for every link that genuinely does not apply. An empty cell is never an acceptable substitute for an exception or a defect entry.
6. Log every defect you find in §6 and report it to the Software Architect. Do not fix conflicts between documents by editing them silently, and do not close a defect because a correction was proposed.
7. Do not present planned tests as performed tests. A future test identifier is planning evidence only.

**Identifier scope.** Non-standard prefixes used in this template (`US`, `ADR`, `AC`, `TST`, `EXC`, `TRD`, `ASM`, `OQ`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Requirements Traceability Matrix

| Field | Value |
| --- | --- |
| Purpose | {{Which traceability questions this matrix answers and which phase gate or review depends on it.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role}} |
| Authority / approval | {{Who authorized this document; `Not approved` if no approval exists.}} |
| Related documents | {{Requirements specification, use cases, architecture decision records, acceptance criteria register, test plan.}} |

## 1. Purpose and scope

{{What is traced, at what granularity, and what lies outside the matrix.}}

| Aspect | Value |
| --- | --- |
| Granularity of a matrix row | {{For example one row per requirement — state the rule actually applied}} |
| Requirement sources included | {{Documents, registers, and their versions}} |
| Chain coverage | {{Which links of the chain are maintained here; state any link maintained elsewhere and where}} |
| Excluded from this matrix | {{Items and reason}} |

*Guidance: if user stories are not used in the project, state that and record the consequence for the chain rather than leaving the column ambiguous.*

## 2. Identifier schemes used

| Prefix | Meaning | Defined in |
| --- | --- | --- |
| `BR` | Business Rule | {{Source document}} |
| `FR` | Functional Requirement | {{Source document}} |
| `NFR` | Non-Functional Requirement | {{Source document}} |
| `UC` | Use Case | {{Source document}} |
| `INT` | Integration Requirement | {{Source document}} |
| `SEC` | Security Requirement | {{Source document}} |
| `US` | User Story | {{Source document, or Not used in this project}} |
| `ADR` | Architecture Decision Record | {{Source document}} |
| `AC` | Acceptance Criterion | {{Source document}} |
| `TST` | Future Test | {{Source document}} |

*Guidance: the six prefixes `BR`, `FR`, `NFR`, `UC`, `INT`, and `SEC` are fixed by the documentation standard. The remaining schemes are project-level conventions and must be documented here or in the document that defines them. Delete rows for schemes the project does not use, and never reuse an identifier for a different item.*

## 3. Forward traceability matrix

| Row | Business Rule | Requirement | User Story / Use Case | Architecture Decision | Acceptance Criteria | Future Test | Link status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | `{{BR-001}}` | `{{FR-001}}` | `{{UC-001}}` | `{{ADR-001}}` | `{{AC-001}}` | `{{TST-001}}` | {{Complete / Exception EXC-001 / Defect TRD-001}} | {{Note or None}} |

*Guidance: list multiple references in one cell when a link is many-to-many, for example `BR-001, BR-004`. Every `Link status` value must resolve either to `Complete`, to a documented exception in §5, or to a defect in §6.*

## 4. Reverse traceability view

| Artifact | Identifier | Traces back to | Forward status | Notes |
| --- | --- | --- | --- | --- |
| Architecture decision | `{{ADR-001}}` | {{FR-00N or No supporting requirement — reason}} | {{Verified / Broken / Exception}} | {{Note}} |
| Acceptance criterion | `{{AC-001}}` | {{FR-00N}} | {{Verified / Broken / Exception}} | {{Note}} |
| Future test | `{{TST-001}}` | {{AC-00N}} | {{Verified / Broken / Exception}} | {{Note}} |
| Business rule | `{{BR-001}}` | {{FR-00N or No related requirement — flagged}} | {{Verified / Broken / Exception}} | {{Note}} |

*Guidance: the reverse view detects artifacts that no forward row claims. A decision with no supporting requirement, or a test with no criterion, appears here first.*

## 5. Documented exceptions

| ID | Chain link | Item | Reason the link does not apply | Approved by | Status |
| --- | --- | --- | --- | --- | --- |
| `EXC-001` | {{Link, for example Acceptance Criteria → Future Test}} | {{Identifier}} | {{Reason}} | {{Role, with date or Pending}} | {{Open / Accepted / Rejected}} |

*Guidance: identifier scheme used here: `EXC-NNN`. An exception is traceable; an empty cell is not. Exceptions affecting a phase gate must be visible to the Software Architect.*

## 6. Defect log

| ID | Defect type | Affected identifiers | Affected document and section | Severity | Description | Owner | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `TRD-001` | {{Orphan requirement / Orphan business rule / Missing link / Missing acceptance criteria / Decision without requirement / Non-verifying criterion / Conflicting reference / Duplicate identifier / Broken identifier}} | {{Identifiers}} | {{Path and section}} | {{CRITICAL / HIGH / MEDIUM / LOW / INFORMATIONAL}} | {{What is wrong and why it matters}} | {{Role}} | {{Open / Correction proposed / Resolved — verified / Accepted as exception}} |

*Guidance: identifier scheme used here: `TRD-NNN`. Defect types must come from the standard's defined set. `Resolved` requires that the correction was checked, not merely drafted.*

## 7. Coverage summary

| Prefix | Items recorded | Fully traced | Orphaned | Missing acceptance criteria | Other open defects |
| --- | --- | --- | --- | --- | --- |
| `BR` | {{Number}} | {{Number}} | {{Number}} | {{Not applicable — business rules do not carry criteria}} | {{Number}} |
| `FR` | {{Number}} | {{Number}} | {{Number}} | {{Number}} | {{Number}} |
| `NFR` | {{Number}} | {{Number}} | {{Number}} | {{Number}} | {{Number}} |
| `SEC` | {{Number}} | {{Number}} | {{Number}} | {{Number}} | {{Number}} |
| `INT` | {{Number}} | {{Number}} | {{Number}} | {{Number}} | {{Number}} |
| `UC` | {{Number}} | {{Number}} | {{Number}} | {{Number}} | {{Number}} |

*Guidance: state the counting basis and the revision the counts were taken from. Counts must be reproducible from §3 to §6; unreproducible figures are not evidence.*

## 8. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption, for example that an upstream document will not change identifier scope}} | {{Basis}} | {{Affected links}} | {{Verification path}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`.*

## 9. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected links or identifiers}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`.*

## 10. Matrix status and approval

| Field | Value |
| --- | --- |
| Traceability check performed on | {{YYYY-MM-DD and source revisions checked}} |
| Open critical or high defects | {{Number, with defect references}} |
| Known limitation of this matrix | {{What could not be checked, and why}} |
| Approval status | {{Not approved / Approved — approver and date}} |
| Phase-gate implication | {{Not assessed by the author; the Software Architect determines the phase gate}} |

*Guidance: this section records the state of the matrix. It does not declare a phase complete, and it does not substitute for independent validation.*

## 11. References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or register}} | {{What it supports}} | {{Repository-relative path and section anchor}} |

## 12. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
