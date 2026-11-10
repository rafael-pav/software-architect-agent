# Software Requirements Specification (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for a Software Requirements Specification (SRS) used in Phase 2 (Requirements Analysis) to record functional, non-functional, business-rule, security, and integration requirements in identified, classified registers. |
| Status | Approved |
| Version | 0.1.2 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings HIGH, MEDIUM and LOW resolved. |
| Applies to | Requirements specifications stored under `docs/02-requirements/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`use-case.md`](./use-case.md); [`requirements-traceability-matrix.md`](./requirements-traceability-matrix.md); [`scope-statement.md`](./scope-statement.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the template. | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. Copy everything from the *Project document skeleton* marker into the target file under `docs/02-requirements/`.
2. Define the requirement authoring rules and the priority scheme in §3 **before** populating the registers; an undefined priority value is a defect.
3. Replace every `{{ ... }}` placeholder. If a requirement's meaning is uncertain, classify the uncertainty rather than writing vague prose — terms such as "fast", "secure", or "user-friendly" must be measured or flagged `OPEN QUESTION`.
4. Remove all italic guidance notes and HTML comments before review.
5. Use only the defined prefixes `FR`, `NFR`, `BR`, `UC`, `INT`, `SEC`, in the form `PREFIX-NNN`. `BR` means **Business Rule**, never "Business Requirement".
6. Assign identifiers at first recording, keep them stable, and never renumber without recorded approval.
7. Record acceptance criteria and traceability links. The matrix template is the authoritative register for the chain Business Rule → Requirement → Use Case → Architecture Decision → Acceptance Criteria → Future Test.
8. Do not present a requirement as approved because it appears in this specification. Approval is a recorded human decision.

**Identifier scope.** Non-standard prefixes used in this template (`AC`, `TST`, `ASM`, `OQ`, `DEC`) are document-local register identifiers, not requirement prefixes defined by the documentation standard. Where the same item type appears in more than one document, the project must allocate a single project-wide sequence (see `documentation-standards.md` §5.4) so that the same identifier is not assigned to different items.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Software Requirements Specification

| Field | Value |
| --- | --- |
| Purpose | {{What this specification defines and which decisions or downstream work it supports.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | {{Responsible role}} |
| Authority / approval | {{Who authorized this specification; `Not approved` if no approval exists.}} |
| Related documents | {{Scope statement, traceability matrix, use cases, architecture overview, research reports.}} |

## 1. Introduction

### 1.1 Purpose

{{The purpose of this specification and the intended readers.}}

### 1.2 Product context

{{A short factual description of the product being specified and the organizational context it serves, at a level no more detailed than needed to interpret the requirements.}}

*Guidance: do not restate the scope statement. Reference it, and record any conflict between the two for the Software Architect.*

### 1.3 Definitions and acronyms

| Term or acronym | Definition | Source or authority |
| --- | --- | --- |
| {{Term}} | {{Definition}} | {{Source}} |

*Guidance: define each acronym on first use or here. If a glossary exists elsewhere, reference it and do not duplicate definitions. `BR` always means **Business Rule**.*

### 1.4 References

| Reference | Purpose | Location |
| --- | --- | --- |
| {{Document or source}} | {{What it supports}} | {{Repository-relative path, section anchor, or URL with access date}} |

## 2. Scope of the requirements

### 2.1 Requirements scope

{{Which capabilities this specification covers, and the boundary against other specifications if the project is split.}}

### 2.2 Excluded from this specification

| Excluded item | Reason | Classification | Source |
| --- | --- | --- | --- |
| {{Item}} | {{Reason}} | {{Label}} | {{Source}} |

### 2.3 Actors and external interfaces

| Actor or external system | Type | Description | Related requirements |
| --- | --- | --- | --- |
| {{Actor or system}} | {{Human actor / External system / Internal component}} | {{Role in relation to the product}} | {{FR-00N, INT-00N}} |

*Guidance: this table is an index, not the integration specification. Integration detail belongs in the `INT` register and its referenced documents.*

## 3. Requirement authoring rules

| Rule | Definition used in this specification |
| --- | --- |
| Atomicity | {{One obligation per requirement}} |
| Verifiability | {{Each requirement must be assessable by a stated method}} |
| Identifier scheme | `FR-NNN`, `NFR-NNN`, `BR-NNN`, `INT-NNN`, `SEC-NNN`, `UC-NNN`; other schemes used: {{AC-NNN, TST-NNN, ...}} |
| Priority scheme | {{Define the levels and their meaning. Do not use values that readers must guess.}} |
| Status vocabulary | {{Define the requirement status values used, for example Proposed / Approved / Rejected / Superseded / Withdrawn}} |
| Source requirement | {{Every requirement must cite its origin, or state "No originating business rule" and the reason}} |

*Guidance: keep this table only if it constrains how the registers below are read. Remove rows that add nothing beyond the documentation standard.*

## 4. Functional requirements

| ID | Requirement | Priority | Source | Acceptance criteria | Classification / status |
| --- | --- | --- | --- | --- | --- |
| `FR-001` | {{The system shall ...}} | {{Priority value from §3}} | {{BR-00N, stakeholder statement, or OPEN QUESTION}} | {{AC-00N or None — flagged}} | {{Label / status}} |

*Guidance: write each requirement as a single testable obligation. Requirements without an originating business rule are orphan candidates and must be reported. Requirements without acceptance criteria are defects, not gaps to fill later.*

## 5. Non-functional requirements

| ID | Category | Requirement and target | Measurement condition | Verification method | Priority | Classification / status |
| --- | --- | --- | --- | --- | --- | --- |
| `NFR-001` | {{Performance / Capacity / Availability / Reliability / Maintainability / Portability / Usability / Accessibility / Compliance / Other — as applicable}} | {{Statement including a measurable target, unit, and basis}} | {{Conditions under which the target applies}} | {{How compliance will be demonstrated}} | {{Priority value from §3}} | {{Label / status}} |

*Guidance: a non-functional requirement without a measurable target and measurement condition cannot be verified and must be flagged. Non-functional requirements often have no use case; record that as a documented traceability exception rather than leaving the link blank.*

## 6. Business rules

| ID | Business rule | Source and authority | Affected requirements | Status |
| --- | --- | --- | --- | --- |
| `BR-001` | {{Rule statement, including conditions and exceptions}} | {{Policy, regulation, or approved decision}} | {{FR-00N, SEC-00N, or None — flagged}} | {{Active / Proposed / Superseded / Withdrawn}} |

*Guidance: a business rule with no related requirement is an orphan business rule and must be reported. A rule asserted by an agent without a source is a `RECOMMENDATION` or `ASSUMPTION`, not a rule.*

## 7. Security requirements

| ID | Security requirement | Threat or control objective | Scope of application | Verification method | Classification / status |
| --- | --- | --- | --- | --- | --- |
| `SEC-001` | {{Requirement statement}} | {{What risk or control objective it addresses}} | {{Components, data, or actors affected}} | {{How it will be verified}} | {{Label / status}} |

*Guidance: security and privacy requirements require human approval before being treated as binding. Do not invent regulatory obligations; cite the applicable source or record an `OPEN QUESTION`.*

## 8. Integration requirements

| ID | External system or interface | Direction | Data or capability exchanged | Interface constraints | Owner | Classification / status |
| --- | --- | --- | --- | --- | --- | --- |
| `INT-001` | {{System or interface}} | {{Inbound / Outbound / Bidirectional}} | {{Data, events, or operations}} | {{Documented constraints, or Unknown — see open questions}} | {{Role or organization}} | {{Label / status}} |

*Guidance: `INT` means **Integration Requirement**. Interface details such as protocol or contract belong in the integration specification and must be referenced, not assumed. Unverified external capability must be classified accordingly.*

## 9. Assumptions

| ID | Assumption | Basis | Impact if wrong | Verification path and owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ASM-001` | {{Assumption}} | {{Basis}} | {{Affected requirements}} | {{How and by whom it will be verified}} | {{Open / Verified / Invalidated — with authority}} |

*Guidance: identifier scheme used here: `ASM-NNN`. Assumptions must not be written into the registers as if they were requirements.*

## 10. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Blocking for phase gate | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected requirements or decisions}} | {{Role}} | {{Date or milestone}} | {{Yes / No — decided by the Software Architect}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. Ambiguous or unverifiable requirements are recorded here with their identifiers.*

## 11. Acceptance criteria and traceability

- Acceptance criteria register: {{AC-NNN entries, their location, and the criteria that remain outstanding}}
- Traceability matrix: {{path to the requirements traceability matrix, with version}}
- Known traceability defects: {{defect references, or state that none have been identified}}

*Guidance: this section indexes traceability; it does not replace the matrix. Do not claim full coverage unless it was checked against the matrix in the same revision.*

## 12. Decisions and approval status

| ID | Decision | Approving role | Approval date | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| `DEC-001` | {{Decision, for example approval of the requirement set in §4}} | {{Human role}} | {{YYYY-MM-DD or Pending}} | {{Proposed / Approved / Rejected / Superseded}} | {{Recorded approval reference}} |

**Statement of approval status.** {{State which requirement groups are approved and which remain proposals.}}

## 13. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
