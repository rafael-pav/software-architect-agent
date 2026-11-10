# Project Documentation Audit and Manifest (Template)

| Field | Value |
| --- | --- |
| Asset type | Reusable framework template. Not a project document and not a filled example. |
| Purpose | Skeleton for the documentation audit and manifest produced during `WF-001` intake: a path-by-path record of the material supplied, its provenance and readability, the gaps and contradictions identified, version and duplicate analysis performed by content, and the classification summary that the work plan depends on. |
| Status | Approved |
| Version | 0.1.1 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Documentation audits and manifests produced during `WF-001` and stored under `docs/00-project-management/`. |
| Related documents | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md); [`project-brief.md`](./project-brief.md); [`research-report.md`](./research-report.md); [`project-initiation.md`](../workflows/project-initiation.md). |

**Change history**

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the documentation audit and manifest template, under explicit Software Architect authorization for the consolidated framework-expansion pass. | Give the `WF-001` audit a reusable structure with provenance, gap, contradiction, and duplicate analysis sections. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.1.1 | 2026-11-10 | Reinforces the methodology/evidence boundary: the `framework/` row in §1 now states that framework and configuration files are excluded from the §3 manifest and are not project evidence, and §3 carries a note that only project material is recorded. | Align the template with the normative boundary introduced in `project-initiation.md` v0.3.0. Made under explicit Software Architect authorization. Versioning: PATCH (reinforcement note; no manifest field, register, or intake-state definition changed). | Documentation Agent | Approved by Human user on 2026-11-10. |

---

## How to use this template

1. This template is used for every engagement, including a greenfield engagement where the manifest is expected to be empty. An empty manifest is a finding to be stated, not a reason to omit the record.
2. Copy everything from the *Project document skeleton* marker into the target file under `docs/00-project-management/`.
3. Record only paths that were actually opened. A row **MUST NOT** be completed from memory, from a file name, or from an expectation about what a document probably contains.
4. Treat every file under `input/existing-documentation/` as read-only. This audit references original material; it never edits, renames, moves, replaces, or deletes it.
5. Keep the two locations distinct throughout: originals (`input/existing-documentation/`) and generated documentation (`docs/`). Do not describe a generated document as if it were the original it analyses.
6. Where material cannot be read, record the limitation and request a readable version. Never summarize unreadable material as though it had been read.
7. Determine duplicates and stale versions by comparing content, not only by comparing file names. Record the basis for every `superseded` designation.
8. Complete §2 before completing §3: the intake state determines the audit depth and what counts as an expected document.
9. Remove every italic guidance note and HTML comment before review. Replace every `{{ ... }}` placeholder; an unfillable placeholder becomes an `OPEN QUESTION` in §9.
10. This audit is evidence about documentation. It is not a requirements document, does not approve the work plan, and does not complete any lifecycle phase.

**Identifier scope.** Non-standard prefixes used in this template (`DOC`, `GAP`, `CONFLICT`, `SRC`, `OQ`) are register identifiers local to this audit, not requirement prefixes defined by the documentation standard, and are documented here as required by `documentation-standards.md` §5.5. `DOC-NNN` identifies a manifest entry, `GAP-NNN` a gap, `CONFLICT-NNN` a contradiction, `SRC-NNN` a source or delivery record, and `OQ-NNN` an audit-level open question; `SRC-NNN` and `OQ-NNN` follow the schemes defined in [`research-report.md`](./research-report.md) §6 and [`project-charter.md`](./project-charter.md) §9 respectively, so a project that uses both must allocate one project-wide sequence (`documentation-standards.md` §5.4). Identifiers cited from other documents (`INT`, `FR`, `NFR`, `SEC`, `ADR`, `DEC`) keep the meaning given by the standard or template that establishes them and are never renumbered here.

**Placeholder convention.** `{{ ... }}` marks a value to be supplied. Italic notes (`*Guidance: ...*`) and HTML comments (`<!-- ... -->`) are instructions to the author and are removed from the finished document. No text in this skeleton is confirmed project information.

---

<!-- ===== BEGIN PROJECT DOCUMENT SKELETON ===== -->

# {{Project name}} — Documentation Audit and Manifest

| Field | Value |
| --- | --- |
| Purpose | {{Why this audit exists, which engagement it opens, and which decisions it supports.}} |
| Status | {{Draft / In review / Approved / Superseded / Withdrawn}} |
| Version | {{0.1.0}} |
| Last updated | {{YYYY-MM-DD}} |
| Owner role | Documentation Agent, under Software Architect coordination. |
| Authority / approval | {{Who authorized the audit and its persistence; use `Not approved` if no approval exists.}} |
| Audit date | {{YYYY-MM-DD}} |
| Intake state | {{Idea (greenfield) / Partial documentation / Complete documentation / Existing system modification}} |
| Audit basis | {{Directories, deliveries, and conversations actually inspected}} |
| Related documents | {{Project Brief, work plan, authorization record, and other dependent documents.}} |

## 1. Scope and treatment of material

| Location | Class of material | Treatment in this audit |
| --- | --- | --- |
| `input/existing-documentation/` | Original project material supplied by the human user. | Read and referenced. **Read-only:** never edited, renamed, moved, replaced, or deleted. |
| `docs/` | Generated project documentation, written only by the Documentation Agent under authorization. | Recorded as generated output. Never treated as an original, and never substituted for one. |
| `framework/` | Reusable framework standards, templates, and workflows. | Reference only, for the conventions this audit follows. **Excluded from the §3 manifest:** framework and repository configuration files are rules, not project evidence, and are never recorded as project material. |

**Statement on original material.** This audit does not modify, re-create, or replace any original document. Every statement about an original is traceable to the path in §3. Where an original is incomplete, contradictory, or unreadable, that condition is recorded rather than corrected.

*Guidance: state which locations were actually inspected and which were empty or absent. An absent directory is recorded as absent; it is not described as if it had been reviewed.*

## 2. Intake state classification

| Field | Value |
| --- | --- |
| Intake state | {{Idea (greenfield) / Partial documentation / Complete documentation / Existing system modification — exactly one}} |
| Basis for classification | {{The material and statements that support the selection, with paths or `SRC-00N` references}} |
| Confirmed by | {{Human role and date, or `Not confirmed`}} |
| Classification | {{CONFIRMED / ASSUMPTION / RECOMMENDATION}} |
| Audit-depth consequence | {{What this state required this audit to cover, and what it deliberately did not cover}} |

*Guidance: the four intake states and their effect on questioning and audit depth are defined authoritatively in [`project-initiation.md`](../workflows/project-initiation.md) §4.3, and restated in [`project-brief.md`](./project-brief.md) §1.2 for the reader. Do not define them again here. Record the selected state, the basis, and the depth actually applied. For `Existing system modification`, application source code is out of scope: only documented behaviour, interfaces, and constraints are audited.*

## 3. Document manifest

*Guidance: only project material is recorded here — the files under `input/existing-documentation/` and `docs/`, plus any source the human user explicitly authorizes. Framework files and repository configuration (`AGENTS.md`, `README.md`, `.opencode/`, `opencode.json`, `.gitignore`), and application source code, are **excluded** from this manifest: they supply rules, not evidence about the project, and no row is completed from a repository file that is not an authorized project source (`project-initiation.md` §4.4).*

### 3.1 Original and generated documents

| ID | Path | Apparent title and purpose | Format | Apparent status | Version or date stated | Language | Stated owner | Delivery source | Delivery date | Channel | Readability |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `DOC-001` | `{{repository-relative path}}` | {{Title and apparent purpose, as the document states them}} | {{Markdown / PDF / Office document / Image or diagram / Other — specify}} | {{Approved / Draft / Unknown — as apparent, not as verified}} | {{Version and date as stated, or `Not stated`}} | {{Language code or name}} | {{Owner as stated, or `Not stated`}} | {{Person, role, or organization that delivered it}} | {{YYYY-MM-DD or `Unknown`}} | {{File delivery / Pasted text / Verbal / Referenced but not provided / Link}} | {{Readable / Partially readable / Not readable}} |

*Guidance: `DOC-NNN` is a manifest identifier, not a requirement identifier. "Apparent status" records what the document says about itself; it is not an approval of that status. Delivery source, delivery date, and channel are required for every entry: material without provenance is unreliable as evidence, even when its content looks authoritative.*

### 3.2 Verbal, pasted, and referenced material

| ID | Description | Provided by | Date | Channel | How recorded | Standing |
| --- | --- | --- | --- | --- | --- | --- |
| `SRC-001` | {{What was said, pasted, or referenced}} | {{Human role or organizational unit}} | {{YYYY-MM-DD}} | {{Verbal / Pasted text / Link / Referenced but not provided}} | {{Verbatim note, message reference, or conversation record}} | {{CONFIRMED as a record of the statement / ASSUMPTION / OPEN QUESTION}} |

*Guidance: a recorded statement confirms what the user said on that date; it does not by itself confirm the behaviour of an existing system. A document that is referenced but not provided is recorded here and as a `GAP-NNN` in §4, and the human user is asked to supply it.*

## 4. Gap register

| ID | Expected information | Why it is expected | Deliverable or decision that depends on it | Owner / resolver | Status | Classification |
| --- | --- | --- | --- | --- | --- | --- |
| `GAP-001` | {{The information that is missing}} | {{The phase deliverable, decision, or standard requirement that expects it}} | {{FR-00N, ADR-00N, Phase 1 deliverable, or `None identified`}} | {{Role}} | {{Open / Requested from user / Resolved — with reference}} | {{ASSUMPTION / OPEN QUESTION}} |

*Guidance: absence is a gap only where a deliverable or decision depends on it; state that dependency. A gap is not closed by an assumption. Where the gap was filled by a later delivery, keep the row and record the resolution and its source.*

## 5. Contradiction register

| ID | Statement A — location | Statement B — location | Nature of the conflict | Decision affected | Escalated to | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `CONFLICT-001` | {{Quoted or precisely paraphrased statement, with path and section}} | {{Quoted or precisely paraphrased statement, with path and section}} | {{What conflicts: scope, date, version, owner, figure, capability, or other}} | {{The decision that cannot be made until this is resolved}} | {{Software Architect; human user where authoritative designation is required}} | {{Open / Decided — with decision reference}} |

*Guidance: both locations are mandatory. Do not merge, average, or silently prefer one source. Where the conflict concerns which original governs, the human user designates the authoritative source and the designation is recorded, not inferred.*

## 6. Version and duplicate analysis

| ID (items compared) | Content comparison basis | Finding | Evidence | Designation | Basis for designation | Classification |
| --- | --- | --- | --- | --- | --- | --- |
| `DOC-001` / `DOC-002` | {{How content was compared: section-by-section, identifier comparison, diff of extracted text, date and change-history review}} | {{Duplicate / Earlier draft / Later revision / Same title but different content / Unrelated documents with similar names / Not comparable — unreadable}} | {{The specific similarity or difference observed}} | {{Current / Superseded by DOC-00N / Unknown standing}} | {{Why this designation follows, and who decided it}} | {{Label}} |

*Guidance: duplicate and stale detection **MUST** be based on content, not on file name, timestamp alone, or directory position. A document is designated `superseded` only with a recorded basis; where the basis is an agent's judgement, the designation is a `RECOMMENDATION` pending the Software Architect's or the human user's decision. Superseded or duplicate files are neither deleted nor renamed.*

## 7. Format and readability limitations

| Path | Format | Text extractable | Treatment applied | Limitation recorded | Action requested |
| --- | --- | --- | --- | --- | --- |
| `{{path}}` | {{PDF / Office document / Image / Diagram / Scanned document / Other}} | {{Yes — with page or section mapping / Partially / No}} | {{Read directly from extracted text / Read from a textual description supplied with the file / Recorded as unreadable}} | {{What could not be established, and its effect on the audit}} | {{None / Textual description requested / Readable version requested — owner and date}} |

*Guidance: a PDF or Office document whose text can be extracted is readable evidence, and the extraction method and page or section reference are recorded. A scanned document, image, or diagram requires a textual description; that description is attributed to its author and is not invented by an agent. Material that cannot be read at all is recorded as a limitation and a readable version is requested (`WF-001` §14.3). A binary artifact should not be the only representation of information the project depends on (`documentation-standards.md` §3.4).*

## 8. Classification summary

| Classification | Count | Items | Notes |
| --- | --- | --- | --- |
| `CONFIRMED` | {{count}} | {{DOC-00N, SRC-00N}} | {{Requires a citable source or recorded approval}} |
| `ASSUMPTION` | {{count}} | {{Items}} | {{Each has a basis and a verification path}} |
| `RECOMMENDATION` | {{count}} | {{Items}} | {{Not a decision; approval pending where required}} |
| `OPEN QUESTION` | {{count}} | {{GAP-00N, CONFLICT-00N, OQ-00N}} | {{Items requiring information or a decision}} |

**Manifest completeness statement.** {{State what proportion of the supplied material this manifest covers, what was excluded, and what remains unverified. Example shape: "All 12 supplied files are recorded; 2 could not be read. The manifest is not evidence that the project's documentation is complete."}}

*Guidance: the summary classifies the audit's statements, not the project. A manifest that records much `ASSUMPTION` and `OPEN QUESTION` is accurate, not deficient.*

## 9. Open questions

| ID | Question | Why it matters | Owner / resolver | Needed by | Status |
| --- | --- | --- | --- | --- | --- |
| `OQ-001` | {{Question}} | {{Affected findings, gaps, or decisions}} | {{Role}} | {{Date or milestone}} | {{Open / Resolved — with resolution}} |

*Guidance: identifier scheme used here: `OQ-NNN`. Audit questions are distinct from project open questions; where an item affects a phase deliverable, reference it from the project's own register as well.*

## 10. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| {{0.1.0}} | {{YYYY-MM-DD}} | {{Summary of the change}} | {{Reason}} | {{Author role}} | {{Draft / In review / Approved / Superseded / Withdrawn}} |

*Guidance: on re-baselining, keep earlier rows and earlier findings. A new delivery is recorded as a new version with the added or changed entries, not by rewriting the previous conclusion.*

<!-- ===== END PROJECT DOCUMENT SKELETON ===== -->
