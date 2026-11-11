# Workflow WF-011 — Document Extraction

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-011` |
| Workflow name | Document Extraction |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-011` |
| Purpose | Convert non-textual project material — DOCX, PDF, XLSX, PPTX, and images — into Markdown or plain text, locally, so that read-only agents without shell access can consume it, while the originals under `input/existing-documentation/` remain unmodified and every extraction carries its provenance and a record of what was lost. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-11` |
| Owner role | Documentation Agent, under Software Architect coordination. |
| Authority / approval | v0.1.0 approved by Human user on 2026-11-10; creation authorized by the Software Architect on 2026-11-10. |
| Validation | Independent validation PASS WITH CONDITIONS — corrections verified as resolved (VAL-001/002/003/004/006/008/009/010/011); deferred items accepted as pending (VAL-005, VAL-007, VAL-100). |
| Applies to | Any assignment in which a read-only agent must consume project material supplied in a format it cannot read directly, and any re-extraction after a change of tool, version, or environment. |
| Related workflows | `WF-001` (initiation), `WF-005` (research), `WF-007` (independent validation), `WF-006` (documentation production and persistence), `WF-010` (mechanism assessment), and `WF-002`/`WF-003`/`WF-004` as downstream consumers. |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§3.1, 5, 9; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§3.5, 4, 5.5, 7, 9; [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md); [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md); [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md); [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md). |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them.

This workflow additionally uses one local identifier scheme for its own records, documented here as §5.5 requires:

| Scheme | Meaning | Format and discipline |
| --- | --- | --- |
| `EXT-NNN` | Extraction record — one record per extraction of one original, with one recorded tool, version, and environment. | Pattern `EXT-NNN` with a zero-padded three-digit number. Assigned before extraction begins, so that a failed attempt is traceable. Stable once assigned and never reused. Unique within the engagement or, where extraction records are not persisted, within the session scope recorded in the record itself. A re-extraction with a different tool, version, or environment receives a new identifier and references the earlier record. Splitting a long document into fragments does not create new records: the fragments are listed inside the record. |

`EXT` is not one of the six standard prefixes and must not be used for a requirement. Other identifiers cited in this workflow (`SRC`, `DOC`, `GAP`, `CONFLICT`, `VAL`, `ASM`, `OQ`, `RISK`, `DEC`, `BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`) keep the meanings given by the standard, template, or agent definition that establishes them; this workflow does not redefine them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced here and not fixed by those sources are in effect as part of an approved workflow: v0.1.0 was approved by the Human user on 2026-11-10 and independently validated **PASS WITH CONDITIONS** — corrections verified as resolved, with `VAL-005`, `VAL-007`, and `VAL-100` deferred as pending items — so those conventions are no longer pending `RECOMMENDATION` items, **except** the section-structure convention described in the next paragraph, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines how project material that no agent can read directly is turned into text that an agent can read.

Some project material arrives as DOCX, PDF, XLSX, PPTX, or images. The agents that must analyse that material are read-only and have no shell access, and the models configured for them do not accept PDF or image input — a limitation reported by the Software Architect from observation and classified in §4.1, not independently verified by an in-repository source. Without a controlled conversion step, the material is either unreadable or — worse — described from expectation by an agent that never saw it.

This workflow converts such material to Markdown or plain text, locally, before it is consumed. Its output is a **derivative**: it is evidence of what the original contains only to the extent that the extraction record says so. The workflow exists to make three things explicit and auditable: which original produced which extract, with which tool and version, and what the extraction could not preserve.

It does not authorize modifications to the originals, it does not change agent permissions or models, and it does not establish that any extracted content has been verified.

---

## 3. Trigger / When to Use

Use this workflow when:

- A read-only agent is assigned to consume project material supplied in DOCX, PDF, XLSX, PPTX, or image form.
- An initiation audit (`WF-001`) must record the readability of non-textual material.
- A research assignment (`WF-005`) depends on a source supplied in a non-textual format.
- An independent review (`WF-007`) requires a deliverable or its evidence in a readable form.
- An extraction must be repeated because the tool, version, environment, or the requested extent of the document changed.
- The existing extracted text is reported as unreadable, truncated, mis-encoded, or lossy in a way that affects the task.

Do not use this workflow to alter, clean up, or re-author the original material, and do not use it to produce project documentation. Documentation is produced under `WF-006`.

---

## 4. Scope and Boundaries

### 4.1 The operating constraint this workflow addresses

The constraints below fall into two classes and are not classified alike. The two shell-permission rows are `CONFIRMED` from a durable in-repository source: the agent definitions in `.opencode/agents/*.md`. The model-input row is an `ASSUMPTION`: it was reported by the Software Architect from observation on 2026-11-10, and no durable in-repository source records it. No external source is cited in this file for any of them.

| Constraint | Effect on the assignment | Classification |
| --- | --- | --- |
| The models configured for the agent roles (`deepseek` `v4-pro` and `flash`) do not accept PDF or image input. | A PDF or an image cannot be supplied to an agent as an attachment or read as a document. The blocking factor is the model's accepted input, not the file size. | `ASSUMPTION` — reported by the Software Architect from observation on 2026-11-10; not independently verified by a durable in-repository source. Verification route: a recorded model-capability check — the input modalities reported by the provider for the configured model and variant, with date and source — before an assignment relies on this distinction as a settled fact. |
| The Research, Validation, and Documentation Agents have no `shell` permission. | No read-only agent can run a conversion tool, inspect a binary container, or test a locally installed utility. | `CONFIRMED` — verified from the agent definitions (`.opencode/agents/*.md`: Research, Validation, and Documentation have `shell: deny`). |
| The Software Architect is the only role with shell access, and that access is `ask`. | Extraction is coordinated and executed by the Software Architect on behalf of the consuming agent. Every shell invocation requires approval at the moment of use; there is no standing authorization to run extraction commands. | `CONFIRMED` — verified from the agent definitions (`.opencode/agents/*.md`: the Software Architect has `shell: ask`). |

No agent may respond to these constraints by changing a model, granting a permission, enabling a plugin, or installing an MCP server. Mechanism questions follow `WF-010`, and any such change requires separate explicit human authorization (`AGENTS.md` §§2, 11).

### 4.2 In scope

- Detecting the actual format of supplied material, rather than trusting its file extension.
- Selecting a local extraction mechanism per format (§4.4).
- Performing extraction locally, through the Software Architect's shell, into a working location outside the repository.
- Recording provenance, encoding, output location, coverage, and losses for every extraction.
- Splitting long extracted content into fragments that keep their reference to the original and to a page, section, slide, or sheet.
- Verifying that the intended consumer agent can actually read the extract before its task begins.
- Recording which extents of the extract the consumer actually read.
- Verifying the procedure itself against real DOCX and PDF material and against XLSX and PPTX samples (§7.4).

### 4.3 Deliberately excluded

- Editing, renaming, moving, converting in place, or deleting any original under `input/existing-documentation/` (`AGENTS.md` §3.1).
- Writing extracted text into the repository as a deliverable. Extracts are working derivatives, not project documentation; persistence of any record under `docs/` requires separate authorization.
- Installing, upgrading, or configuring extraction software without authorization (§12).
- Enabling OCR, plugins, MCP servers, or external conversion services to work around an unreadable document (§4.5, §4.7).
- Changing a model, an agent definition, or a permission to make a document readable.
- Claiming that tables, images, pagination, layout, or formatting are preserved. Fidelity is recorded, not assumed (§4.6).
- Treating extracted text as verified content. An extract is evidence about the original, not a substitute for it when the original governs.
- Producing requirements, architecture, or decisions from extracted content. This workflow supplies readable material; the consuming workflow decides.
- Application implementation, code, scripts, or executable automation.

### 4.4 Format detection and mechanism selection

Format is detected from the file's content signature where feasible, cross-checked against the extension and against what the human user stated when supplying it. A file whose extension and content disagree (for example, a legacy binary document renamed `.docx`) is recorded as a format mismatch and handled according to its detected format; the extension is never accepted as proof of format on its own.

| Format | Detection | Candidate local mechanism | Structures to check for loss, not assumed preserved | Notes |
| --- | --- | --- | --- | --- |
| DOCX (Office Open XML word processing) | Extension plus ZIP package signature and package part names | Local document-to-text/Markdown conversion tool | Tables, images, page layout, headers and footers, footnotes and endnotes, comments, tracked changes, floating shapes, embedded objects | The declared format must be confirmed; a renamed legacy `.doc` is not a DOCX. |
| PDF | File signature (`%PDF`) and presence or absence of a text layer | Local PDF text extraction | Multi-column reading order, tables, figures, headers and footers, page boundaries | A PDF without a text layer (a scan) is not extractable by text extraction; §4.7 applies. |
| XLSX | Extension plus ZIP package signature | Per-sheet cell extraction to text or tables | Formulas versus cached values, merged cells, charts, hidden sheets, cell formatting semantics, cell comments | The extraction must state whether formula text, cached value, or both were captured. |
| PPTX | Extension plus ZIP package signature | Per-slide text extraction, including speaker notes where the mechanism exposes them | Visual reading order, grouped shapes, diagrams, charts, images, slide numbers, layouts | Text order may differ from the visual order of the slide; the extraction states that it may. |
| Image or scan (PNG, JPEG, TIFF, and similar) | File signature | None by default. An attributed textual description supplied with the material, or optional local OCR (§4.7) | Everything: an image has no text layer, so any text produced from it is a derivative of a derivative | Not accepted as model input. A description is attributed to its supplier and never invented by an agent. |
| Legacy binary Office (`.doc`, `.xls`, `.ppt`) | File signature differing from the OOXML package | Not covered by default | As for the corresponding OOXML format, plus conversion error inside the legacy parser | Treated as an unsupported format unless the Software Architect obtains an explicit decision to handle it. |

The mechanisms named above are candidates, not verified capabilities. Claiming that a specific tool converts a specific format correctly requires the verification in §7.4 and a recorded source, and is outside what this workflow asserts.

Selection rule: prefer a mechanism that runs entirely on the local machine, requires no network access, and preserves enough structure for the consumer's task. Where two candidates are equally suitable, the simpler one is preferred and the reason for the choice is recorded in the extraction record.

### 4.5 Processing and privacy boundary

- **Local only.** Extraction runs on the local machine. No document, excerpt, or extracted text is transmitted to an external service, an online converter, a hosted model, or any network endpoint.
- **No mechanism escalation.** Plugins, MCP servers, background services, and model or permission changes are not used to make a document readable. They are outside this workflow and follow `WF-010`, with their own authorization.
- **No OCR by default.** OCR is optional and gated (§4.7).
- **Originals untouched.** The original is read by the extraction tool and remains byte-identical afterwards. The tool writes only to the working location.
- **Output outside the repository.** Extracted text is written to a temporary or working directory outside the repository — not to `docs/`, `input/`, `framework/`, or the repository root. A working path is not a deliverable and is not referenced as one.
- **No executable carry-over.** Extracted output must not contain executable content, macros, or embedded objects. Where a mechanism emits HTML or rich markup, it is reduced to text or Markdown, or the residual markup is recorded as a limitation.

Where the only mechanism available for a format would transmit the document off the machine, extraction does not proceed. The Software Architect reports the situation and requests a decision (§12).

### 4.6 Fidelity boundary

The extract is a **derivative**. This workflow does not claim that extraction preserves tables, images, pagination, layout, formatting, comments, or field content, and no agent may describe an extract as a faithful reproduction of the original.

- Every extraction completes the mandatory **Losses detected** block (§9). `None detected` is recorded only after the checks listed in §7.3, not by default.
- A loss that affects meaning — a table whose rows no longer align with their headers, a page that did not extract at all, a figure that carried the only statement of a requirement — makes the extract insufficient for the claim it would support. It is recorded, and the limitation travels with the extract to the consumer.
- Where extracted content and the original could differ on a point that matters to a decision, the original governs, and a human must check it. No agent may resolve such a difference by preferring the extract.
- An extract that could not be produced at all is recorded as such. It is never summarized from expectation.

### 4.7 OCR (optional capability)

OCR converts images of text into characters. It is **not** part of the default procedure and is **not** required by this workflow.

- OCR output is a derivative of a derivative. It may contain substitution errors that read fluently. An OCR passage is therefore labeled `unverified derivative` and is never presented as verified content, quoted as exact wording, or used as the sole basis for a requirement, a security statement, or a decision.
- Before OCR is used, a **local** alternative must be evaluated — for example a locally installed `tesseract` build — and its actual operation must be verified on a sample of the project's own material: correct invocation, correct language data, correct reading order for the tested pages, and an accuracy check against the original by a human.
- A tool being installed, or being reported as supporting a language, is not evidence that it works. Only a recorded test result counts.
- Enabling OCR requires human authorization (§12). No OCR tool is asserted here to be installed, configured, or functional; that status is an `OPEN QUESTION` (`OQ-WF-011-03`).
- Every OCR'd page records the tool, its version, the language data used, and the pages affected, so that a later reviewer can find the passages that were not read as text.

### 4.8 Reference environment (`RECOMMENDATION`)

The environment below is a **reference**, not a decision. No tool or version is fixed by this workflow; the tool and version actually used are recorded in the provenance block of each extraction record (§9), and every such block is authoritative for that extraction only.

| Element | Reference value | Status |
| --- | --- | --- |
| Execution environment | A dedicated, isolated Python virtual environment (for example Python 3.14 in its own `venv`), used only for extraction | `RECOMMENDATION` — pending approval; not verified in this repository. |
| Conversion tool | A local document-conversion tool installed into that environment (for example `markitdown`) | `RECOMMENDATION` — pending approval. Capability, version, and format coverage are not verified in this document. |
| Invocation | Performed by the Software Architect through its shell, on behalf of the named consumer | `CONFIRMED` constraint (only role with shell, and that permission is `ask`, so each invocation is approved at the moment of use) combined with a `RECOMMENDATION` for the specific invocation. |
| Recording obligation | Tool name, version as reported by the tool, interpreter version, and environment path recorded per extraction | `CONFIRMED` requirement of this workflow. |

No verification evidence for any specific tool or version is recorded in this repository as of 2026-11-10. The tests required by §7.4 are a precondition for relying on the tool, not a formality.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns and coordinates the workflow. Receives the need from the consuming assignment, detects the format, selects the mechanism, performs the extraction through its shell in the approved environment, verifies encoding and correspondence, verifies that the named consumer can actually read the extract, hands over the fragments with the extraction record, and records the result. Writes no repository files. |
| **Documentation Agent** | Sole writer of framework assets and project documentation. Has no shell and does not extract. May consume extracted text as a reader like any other read-only agent, and reports the extents it actually read. Writes the extraction record into the repository only if the Software Architect authorizes persistence. |
| **Research Agent** | Read-only consumer. Requests extracted material through the Software Architect, does not extract, does not install or run tools, and reports limits: which fragments it read and which it could not. Never asserts that it read a source it did not access. |
| **Validation Agent** | Read-only consumer. Reviews the extracted content together with its provenance and losses. Returns `INCOMPLETE REVIEW` when required material is not accessible in a readable form, and never states or implies that it reviewed content it could not access. |
| **Human user / stakeholder** | Authorizes OCR, any network-transmitting mechanism, tool installation or environment change, and acceptance of residual losses where the lost content matters to a decision. Supplies a readable version when extraction cannot produce one. |

Only the Software Architect executes extraction. No agent may obtain extraction capability by changing a model, a permission, an agent definition, or a plugin configuration.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- A named consumer agent and a stated purpose exist. Extraction without a consumer is not performed.
- The original file is present at a recorded path, and its provenance (delivery source, date, channel) is known or explicitly recorded as unknown.
- The Software Architect has shell access and an approved extraction environment, or has an explicit decision to use an available local tool for this extraction.
- A working location outside the repository is available for the output.
- The consumer agent can be asked to read a named fragment, so that access can be verified rather than assumed.
- Where OCR, external services, or installation is required, the authorization described in Section 12 has been obtained.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Original document | `input/existing-documentation/` or another human-authorized source | **MUST** | Read-only. Path and provenance recorded. |
| Stated format and supply context | Human user, through the Software Architect | **SHOULD** | Cross-checked against the detected format; a mismatch is recorded. |
| Named consumer and purpose | Software Architect | **MUST** | Determines the required extent and the acceptable losses. |
| Extraction mechanism, tool, and version | Software Architect, in the approved environment | **MUST** | Recorded per extraction; never carried over by assumption from an earlier extraction. |
| Prior extraction records | Session record or `docs/` if persisted | **MAY** | Reused with their losses and version applicability, not presented as a fresh extraction. |
| Human authorization for OCR, external services, or installation | Human user, recorded by the Software Architect | **MUST** where applicable | Absence of authorization means the activity does not occur. |
| Working location outside the repository | Software Architect | **MUST** | Output path recorded; not a deliverable location. |

---

## 7. Workflow Steps

The steps are grouped into four stages: request and detection, extraction, verification and handover, and procedure verification.

### 7.1 Stage A — Request, detection, and mechanism selection

1. **Receive and record the extraction request.** The Software Architect records which assignment needs the material, which agent will consume it, and what the consumer needs from it (a whole document, a named section, a table, a set of pages). A request without a named consumer and purpose is not processed.
2. **Confirm the original and its read-only status.** The file is recorded by repository-relative path and provenance. The workflow confirms that the file will be read only: no rename, move, in-place conversion, or overwrite. The extract is written elsewhere (§4.5).
3. **Detect the actual format.** Determine the format from the file's content signature where feasible, then cross-check the extension and the supply statement. Record the declared format, the detected format, and any mismatch. A mismatch is a finding for the consumer and for the record, not a reason to guess.
4. **Select the extraction mechanism** using §4.4. Record the selected mechanism and, where more than one candidate was viable, the reason for the selection.
5. **Confirm the processing boundary.** Confirm that the mechanism runs locally, that no network transmission occurs, that no plugin, MCP server, or external service is involved, and that the output goes to a working location outside the repository. Where this cannot be confirmed, stop and escalate (§12).
6. **Open the extraction record.** Assign the next `EXT-NNN` and record the fields already known: original reference, provenance of the original, request context, declared and detected format. The identifier is assigned before extraction so that a failed attempt remains traceable.

### 7.2 Stage B — Extraction

7. **Prepare the environment and record it.** Confirm that the approved environment is in use and that the tool is present. Record the tool name, the version it reports, the interpreter version, and the environment path. Do not install, upgrade, or enable anything during the extraction without the authorization in Section 12.
8. **Extract to a working location outside the repository.** Produce UTF-8 text or Markdown. Record the encoding actually produced, which may differ from UTF-8; a non-UTF-8 result is converted or recorded as a limitation, not silently accepted. Keep headings and table text where the mechanism supports it, without claiming that it does.
9. **Split long output into fragments when required.** When the extract exceeds a practical reading size, split it into fragments. Each fragment names the original and the extent it covers — pages, sections, slides, or sheets — and an index fragment lists every fragment in order. Splitting must not drop content silently: any gap between fragments is recorded in the losses block.
10. **Record the losses.** Complete the mandatory **Losses detected** block of the record: tables, images, page or slide layout, headers and footers, footnotes, comments, tracked changes, formulas, charts, embedded objects, reading order, and pages that did not extract at all. State `None detected` only for a category that was actually checked.
11. **Record the result.** One of `Extracted`, `Partially extracted`, or `Failed`, with the reason. A partial or failed extraction is recorded as such and is never described as a complete conversion.
12. **Do not rescue a failed extraction by changing the boundary.** OCR is not enabled to compensate for a failed text extraction without the authorization in Section 12, and an external conversion service is never used to compensate for it at all.

### 7.3 Stage C — Verification and handover

13. **Spot-check correspondence against the original.** Verify the opening content, at least one table or list, one mid-document section, and the closing content. Record what was checked and what was not checked. A spot check is not a full verification, and the record says which it was.
14. **Verify encoding and file safety.** Confirm that the output opens as text, is UTF-8 or has its actual encoding recorded, contains no executable content, macros, or embedded objects, and has no truncated final fragment.
15. **Verify accessibility for the named consumer.** Before the consumer's task begins, confirm that the consumer can actually open and read the extract — for example by having it read a named fragment and report the first heading, one table caption, and the final line. Record the result and who verified it. Sharing a path is not evidence of access; a readable path for the Software Architect may be unreadable for another agent, and a temporary location may not be reachable at all.
16. **Hand over the extract with its provenance.** Deliver to the consumer: the fragment paths, the `EXT-NNN` identifier, the original reference, the tool and version, the losses block, and an explicit statement of what the extract does not contain. The consumer treats the extract as derivative evidence, not as the original.
17. **Record the reading extents reported by the consumer.** The consumer reports which fragments it actually read and which it did not. Material not read is not reviewed, and the consumer says so rather than leaving the extent implied.
18. **Close or hold the record.** Mark the record `Complete` when the handover succeeded and the losses are recorded; `Held` when a readable form must be requested from the human user; `Failed` when the material cannot be made readable. A held or failed record remains visible.

### 7.4 Stage D — Procedure verification and re-verification

The procedure is verified against real material, not against the tool's description of itself.

19. **Build the test set.** At least one real DOCX and one real PDF taken from the project's own authorized material, plus an XLSX sample and a PPTX sample. Where project material of a format is unavailable, a sample supplied or approved by the human user is used and identified as a sample.
20. **Run the extraction and record per-format results.** For each test file record: the result, whether tables survived as recognizable tables, the output encoding, whether the content corresponds to the original on spot check, and whether page, section, slide, or sheet references are usable.
21. **Record the limitations.** Write the observed limitations per format — for example, that a table was flattened, that a multi-column page was read in the wrong order, or that a scanned PDF produced no text. Do not generalise one result into an unqualified capability claim, and do not describe an untested format as supported.
22. **Re-verify after any change.** A change of tool, version, or environment invalidates the earlier test evidence for the changed element. Re-run the affected tests and record the new evidence before relying on the new combination.

Verification results are session evidence unless persisted; they are not project documentation, and their absence in the repository must not be read as a passing result.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Software Architect (own execution) | Perform the extraction through shell with the approved local tool. | Local only; no plugin, MCP server, or external service; originals read-only; output outside the repository. |
| Software Architect | Research Agent | Consume the extracted fragments for a defined research question. | Read-only; no shell; no extraction; must report which fragments were read. |
| Software Architect | Validation Agent | Review content from the extract together with its provenance and losses. | Read-only; returns `INCOMPLETE REVIEW` if the material is not readable; never claims access it does not have. |
| Software Architect | Documentation Agent | Consume the extract in an authorized drafting assignment, or persist an extraction record if authorized. | Read-only regarding extraction; writes only the authorized files. |
| Software Architect | Human user | Authorize OCR, external services, tool installation, or acceptance of losses that matter. | Presented with the effect on the assignment, not only with the technical option. |
| Consumer agent | Software Architect | Report access failures, reading extents, and limitations encountered with the extract. | A failed read is reported, not retried blindly and not omitted. |

Interactions are mediated by the Software Architect. No agent delegates to another agent, no read-only agent requests shell capability, and no agent resolves an access failure by assuming the content.

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Extraction record (`EXT-NNN`) | Software Architect | Provenance, tool and version, encoding, output location, fragments, losses, result, and access verification for one original. |
| Extracted text or Markdown fragments | Software Architect | UTF-8 derivative output in a working location outside the repository, split where required and indexed. |
| Losses block | Software Architect | Mandatory record of what the extraction did not preserve, per category and per page or section. |
| Access verification result | Software Architect, confirmed by the consumer | Which agent opened which fragment and what it reported. |
| Reading-extents report | Consumer agent | Which fragments were actually read and which were not. |
| Test evidence per format | Software Architect | Results of the DOCX, PDF, XLSX, and PPTX checks in §7.4, with observed limitations. |
| Persisted extraction record (conditional) | Documentation Agent | Written under `docs/` only if the Software Architect authorizes persistence; not created by default. |

### 9.1 Extraction record fields

| Field | Requirement | Content |
| --- | --- | --- |
| Identifier | **MUST** | `EXT-NNN`, assigned before extraction, stable, never reused. |
| Original reference | **MUST** | Repository-relative path, file name, declared and detected format, size, and a content fingerprint where obtainable. |
| Provenance of the original | **MUST** | Delivery source, date, and channel, or an explicit statement that one is unknown; `SRC-NNN` where a source record exists. |
| Request context | **MUST** | The assignment that needs the material and the named consumer agent. |
| Tool and version | **MUST** | Product name and the version string the tool reports, plus the interpreter version and environment path. |
| Invocation | **SHOULD** | The command actually executed, recorded so that the extraction can be repeated and audited. |
| Encoding | **MUST** | Encoding actually produced; expected UTF-8. |
| Output location | **MUST** | Working path outside the repository, with the statement that it is not a deliverable. |
| Fragments and extents | **MUST** where split | Each fragment path with the page, section, slide, or sheet range it covers, plus the index. |
| Losses detected | **MUST** | Per category: tables, images, layout, headers and footers, footnotes, comments, tracked changes, formulas, charts, embedded objects, reading order, unextracted pages. |
| Result | **MUST** | `Extracted`, `Partially extracted`, or `Failed`, with the reason. |
| OCR | **MUST** where used | Tool, version, language data, pages affected, and the `unverified derivative` label. |
| Consumer access verification | **MUST** | Which consumer verified access, to which fragment, with what result. |
| Reading extents reported by the consumer | **SHOULD** | Fragments actually read, and fragments not read. |
| Other limitations | **SHOULD** | Anything else that affects reliance on the extract. |

### 9.2 Record shape

The record is plain text or Markdown. The block below is a shape for the fields, not a command and not executable content.

```text
Extraction record EXT-NNN
Original:        input/existing-documentation/<file> (declared <fmt>, detected <fmt>, <size>, fingerprint <value>)
Original provenance: <source> / <date> / <channel> / <SRC-NNN or "not recorded">
Requested by:    <assignment> for <consumer agent>
Tool and version: <product> <version> | interpreter <version> | environment <path>
Invocation:      <command actually executed>
Encoding:        <encoding produced>
Output:          <working path outside the repository>
Fragments:       EXT-NNN-part-01 (pages 1-12), ... | index: EXT-NNN-index
Losses detected: tables <n preserved / n flattened / n absent>; images <...>; layout <...>;
                 headers/footers <...>; footnotes <...>; comments <...>; tracked changes <...>;
                 formulas <...>; charts <...>; embedded objects <...>; reading order <...>;
                 unextracted pages <...>
Result:          Extracted | Partially extracted | Failed — <reason>
OCR:             not used | <tool> <version>, <language data>, pages <...>, unverified derivative
Access verified: <consumer> read <fragment> and reported <evidence>
Read extents:    <fragments read> / <fragments not read>
Limitations:     <...>
Status:          Complete | Held | Failed
```

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Documentation Standards §§3.5, 4, 5.5, 7, 9 | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Literal marking, classification labels, the rule that other identifier schemes are documented in the asset that defines them, evidence discipline, and status vocabulary. |
| Repository agent instructions | [`AGENTS.md`](../../AGENTS.md) | Read-only treatment of original material, research and evidence rules, persistence rules, and the prohibition on modifying original documentation. |
| Project Documentation Audit and Manifest template | [`framework/templates/project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md) | Consumer of the readability and provenance findings this workflow produces during `WF-001`. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Consumer in `WF-005`. **Intended behaviour, not yet supported by the template:** a source record for a source read from an extract should state that it was read from an extract and what that extract did not contain. The current template has no dedicated field for an extraction record or its losses, so this is a pending intent; adding such a field requires separate authorization and is outside this workflow (§10 note below). |
| Validation Report template | [`framework/templates/validation-report.md`](../templates/validation-report.md) | Consumer in `WF-007`. **Intended behaviour, not yet supported by the template:** the review basis should record which material was supplied as an extract, with its losses, and which material was unreadable. The current template has no dedicated field for an extraction record, so this is a pending intent; adding such a field requires separate authorization and is outside this workflow (§10 note below). |
| Validation Agent definition | [`.opencode/agents/validation-agent.md`](../../.opencode/agents/validation-agent.md) | Review dimensions, finding severity, and the prohibition on claiming review of inaccessible material. |
| Research Agent definition | [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md) | Read-only research boundary and required evidence fields. |
| Software Architect definition | [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) | Coordination role, tool authority, and the requirement to present decisions to the human user. |

**Template availability (observed 2026-11-10).** No template exists for an extraction record. Section 9.1 defines the fields, and this definition is authoritative until a template is authorized. The Documentation Agent **MUST NOT** create a template without separate authorization. Extraction records are session records unless the Software Architect authorizes persistence; where they are persisted, they are project-management records and not research reports.

**Template gap — extraction provenance (observed 2026-11-10).** The research report template and the validation report template do not currently provide a field for an extraction record, for its losses, or for the distinction between material read from an extract and material that was unreadable. The rows above therefore describe an intended behaviour that no template yet supports; a consumer that records this information today does so in whatever field the template happens to offer, and the limitation is stated in the record. Aligning either template is a separate change requiring Software Architect authorization and human approval under `AGENTS.md` §11, and it must not be performed as part of an extraction under this workflow.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Named consumer before extraction | Software Architect | No extraction proceeds without a named consumer and a stated purpose. |
| Originals untouched | Software Architect | The original remains under `input/existing-documentation/`, unmodified and unrenamed; the output is a separate derivative. |
| Original byte identity verified where a fingerprint is obtainable | Software Architect | Where a fingerprint of the original can be obtained — for example a hash of the file before extraction — it is recorded before extraction and recomputed after extraction completes; a difference is recorded and investigated before the extract is used, and the original is not itself corrected. Where no fingerprint can be obtained, the record states that identity was not verified by this means. |
| Actual format detection | Software Architect | Format is established from content, not from the extension; a mismatch is recorded. |
| Local processing | Software Architect | No network transmission, plugin, MCP server, or external conversion service is used. |
| Tool and version recorded | Software Architect | Every extraction records the tool, its version, and the environment; no version is inherited from an earlier extraction. |
| Encoding verification | Software Architect | Output encoding is checked and recorded; a non-UTF-8 result is converted or recorded as a limitation. |
| Losses recorded | Software Architect | The losses block is completed per category; `None detected` requires an actual check. |
| No fidelity overclaim | All agents | No agent states that tables, images, layout, or pagination were preserved unless the record says so. |
| Fragment traceability | Software Architect | Every fragment names its original and its page, section, slide, or sheet extent, and gaps are recorded. |
| Access verified, not assumed | Software Architect, confirmed by the consumer | A path shared is not access proven; the consumer reports having opened a named fragment. |
| Reading extents reported | Consumer agent | Each consumer states which fragments it read and which it did not. |
| No false reading claims | All agents | No agent claims to have read, or to have validated, content it did not access. |
| No blind retry | All agents | A failed read is diagnosed (path, encoding, truncation, size, format) and reported before any retry; the same read is not repeated unchanged. |
| OCR gated and labelled | Software Architect | OCR is used only under authorization, after a local alternative was verified, and its output is labelled `unverified derivative`. |
| No mechanism escalation | All agents | Models, permissions, agent definitions, plugins, and MCP servers are not changed to make a document readable. |
| Procedure verified on real material | Software Architect | DOCX and PDF are tested on real material, XLSX and PPTX on samples, with tables, encoding, content, and references checked and limitations documented. |

Extraction is not validation. A readable extract does not mean its content is correct, complete, or approved.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Enabling OCR | Human user, on the Software Architect's recommendation | Before any OCR is run | OCR text is `unverified derivative`; no decision may rest on it alone. |
| Using any mechanism that would transmit a document off the machine | Human user | Before use | The default is prohibition; without the authorization the extraction does not proceed and the limitation is recorded. |
| Installing, upgrading, or reconfiguring extraction tooling or its environment | Human user | Before the change | No silent environment change; the change invalidates earlier test evidence and requires re-verification. |
| Accepting an extraction whose recorded losses affect meaning | Human user, on the Software Architect's presentation | Before a consumer relies on the extract for a decision | The loss is recorded against the decision; the extract is not treated as sufficient. |
| Accepting that essential material remains unreadable | Human user | When no readable form can be produced | A readable version is requested; the gap remains visible and is not closed by assumption. |
| Approving this workflow as a framework asset | Human user, under the framework governance in `AGENTS.md` §11 | After review | v0.1.0 was approved by the Human user on 2026-11-10 and independently validated (PASS WITH CONDITIONS, with `VAL-005`, `VAL-007`, and `VAL-100` deferred); approval has therefore occurred, and the workflow is `Approved`. |

Agents **MUST NOT** infer any of these decisions from silence, from a general instruction to "read the documents", or from the existence of a tool on the machine. A recorded decision identifies the deciding role, the date, the scope, and any condition.

---

## 13. Completion Criteria

An extraction under this workflow is complete when all of the following hold:

- [ ] A named consumer agent and a stated purpose are recorded.
- [ ] The original is recorded by path and provenance, and was not modified, renamed, or moved.
- [ ] The format was detected from content and cross-checked against the extension and the supply statement.
- [ ] The extraction mechanism, tool, and version are recorded for this extraction.
- [ ] Processing was local, and no network transmission, plugin, MCP server, or external service was used.
- [ ] Output was written to a working location outside the repository in a recorded encoding.
- [ ] Long output was split into indexed fragments, each naming the original and its extent.
- [ ] The losses block is complete for every category, with actual checks behind any `None detected`.
- [ ] The result is recorded as `Extracted`, `Partially extracted`, or `Failed`, with the reason.
- [ ] The named consumer verified that it can actually open and read the extract.
- [ ] The consumer reported which fragments it read and which it did not.
- [ ] The provision for OCR, if used, is authorized, locally verified, and labelled unverified.
- [ ] No agent claimed to have read content it did not access.
- [ ] No original material, protected repository file, or file outside an authorized write scope was modified.
- [ ] The procedure's test evidence for DOCX, PDF, XLSX, and PPTX exists for the tool and version in use, or its absence is recorded as a limitation. The absence of that evidence prevents **relying on** the extraction tool's fidelity; it does not by itself prevent an individual extraction from being completed, provided the extraction proceeds with its losses recorded and the missing evidence is stated as a limitation. No claim of fidelity may rest on an extraction whose tool has no recorded test evidence.

Completion of an extraction does not validate its content, does not approve any decision based on it, and does not complete any lifecycle phase.

---

## 14. Exception Handling

### 14.1 Material that cannot be extracted

A PDF without a text layer, an encrypted or password-protected document, a corrupted file, a legacy binary format outside the selected mechanism, or a file whose content does not match any supported signature is recorded as `Failed` or `Partially extracted`, with the reason and the extent that could be obtained. The Software Architect requests a readable version from the human user. OCR is considered only under §4.7, and only after authorization. The material is never summarized from expectation.

### 14.2 Format mismatch

Where the extension and the content disagree, the detected format governs handling, and the mismatch is recorded in the extraction record and reported to the assignment that requested the extraction. An error caused by the mismatch is not attributed to the original's content.

### 14.3 Losses that affect meaning

Where a recorded loss changes what the material says — a table that no longer aligns, a page that did not extract, a figure that carried a requirement — the extract is marked insufficient for that purpose. The consumer reports the limitation with its findings, and a human checks the original where the point matters. The loss is not smoothed over by the consumer's prose.

### 14.4 The consumer cannot read the extract

Access failure is diagnosed before any retry: does the path exist and is it reachable from the consumer's context, is the file complete, is the encoding readable, is the fragment the intended one, is the extract too large for the read? The consumer reports the diagnosis to the Software Architect, who fixes the cause or supplies a different form. Repeating the same read without a diagnosis is prohibited because it produces the appearance of effort without information. The failure is recorded; the consumer does not proceed as if the material had been read.

### 14.5 Very long or very large material

Where the extract exceeds a practical reading size, the content is fragmented and indexed (§7 step 9), and the consumer works fragment by fragment, reporting its extents. A consumer that has read three of twelve fragments does not describe the document as read. Where the needed extent is unknown, the consumer states what it would need and the Software Architect extracts only that extent.

### 14.6 Pressure to use a faster route

Requests to use an online converter, a hosted model, a plugin, an MCP server, a different model, or a permission change to "just make the document readable" are refused and reported. The refusal is recorded with the alternative that remains available: a local extraction with recorded losses, an attributed textual description supplied by the human user, or a readable version requested from the human user.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner | Status |
| --- | --- | --- | --- | --- |
| `OQ-WF-011-01` | Which local extraction tool, version, and environment is approved as the durable reference, and who maintains it? | The workflow records the tool per extraction but does not decide the standard environment; without a decision, every extraction re-opens the choice. | Software Architect | `Open` |
| `OQ-WF-011-02` | Should extraction records be persisted as project-management records under `docs/`, and if so where, given that they are working evidence rather than deliverables? | Without persistence, provenance exists only in the session; with persistence, the repository accumulates derivative records that may be mistaken for sources. | Software Architect | `Open` |
| `OQ-WF-011-03` | Is OCR to be adopted at all, with which local tool and language data, and what accuracy threshold justifies its use? | OCR output can read fluently while being wrong; the acceptance criterion is undefined. | Software Architect | `Open` |
| `OQ-WF-011-04` | What is the maximum practical fragment size for a consumer agent, and should it be fixed as a convention? | Fragment size affects how much of a long document a consumer can reliably read and report on. | Software Architect | `Open` |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | Consumer: the documentation audit must establish readability of non-textual material, which this workflow provides. |
| [`WF-005` — Research](./research.md) | Consumer: research sources supplied in non-textual formats are consumed only through an extraction under this workflow. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Consumer: material under review must reach the reviewer in a readable form, with provenance; this workflow supplies it. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked when an extraction record or related report is persisted under authorization. |
| [`WF-010` — Technology Capability Assessment](./technology-capability-assessment.md) | Referred when the extraction need raises a question about a mechanism — tool, plugin, MCP server, or model — that this workflow neither selects nor installs. |
| [`WF-002` — Planning and Scope](./planning-and-scope.md), [`WF-003` — Requirements Analysis](./requirements-analysis.md), [`WF-004` — System Design and Architecture](./system-design.md) | Downstream consumers of material read from an extract, through the phase workflows' own evidence rules. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the document extraction workflow: format detection and per-format mechanism selection; local extraction performed by the Software Architect through shell; provenance, encoding, fragment, and losses recording; access verification before consumption; optional gated OCR; procedure verification against real DOCX and PDF material and XLSX and PPTX samples. Corrections applied within the same version after independent validation: the model-input constraint is classified `ASSUMPTION` with a stated verification route, and the Software Architect's shell permission is recorded as `ask` (§4.1, §4.8); original byte identity is verified where a fingerprint is obtainable (§11); the completion criterion distinguishes tool-fidelity evidence from the completion of an individual extraction (§13); the extraction-record expectations for the research and validation report templates are marked as intended behaviour that no template yet supports (§10). | Record the approved response to two distinct operating constraints: shell permission — verified from the agent definitions (`.opencode/agents/*.md`: Research, Validation, and Documentation have `shell: deny`; the Software Architect has `shell: ask`) — and model input modality (the models do not accept PDF or image input) — reported by the Software Architect from observation on 2026-11-10, not independently verified by a durable in-repository source. Together they mean that non-textual material must be converted to text locally, with provenance and recorded losses, before any agent relies on it. Findings VAL-005 and VAL-007 are deferred by the Software Architect and are not addressed by this correction. | Documentation Agent | Approved by Human user on 2026-11-10 — independent validation PASS WITH CONDITIONS; corrections for VAL-001, VAL-002, VAL-003, VAL-009, VAL-010, and VAL-011 verified as resolved. VAL-005 (duplicated metadata), VAL-007 ('Section structure' note), and VAL-100 ('Office document' terminology in the manifest template) are accepted as deferred/pending items, not as corrected or resolved. |
| 0.1.1 | 2026-11-11 | PATCH documentary correction: the §1 "Normative basis" was obsolete — it stated that this version is `In review`, not validated, and not approved, contradicting the metadata — and now records the actual state: v0.1.0 approved by the Human user on 2026-11-10 and independently validated PASS WITH CONDITIONS, with corrections verified as resolved and `VAL-005`, `VAL-007`, and `VAL-100` deferred as pending items, so that its procedural conventions are in effect as part of an approved workflow, **except** the section-structure convention, which remains a `RECOMMENDATION` until a durable workflow-governance document is established. The `Authority / approval` field now attributes the approval to v0.1.0. Status remains `Approved`; the `Validation` field already recorded the result and was left unchanged. No rule, procedural step, approval, or approved decision was changed. | Resolve the obsolete "Normative basis" statement and the systemic "Normative basis / Section structure" pattern recorded in WF-009 §16 (carve-out). Correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.0 approved by Human user on 2026-11-10; v0.1.1 PATCH documentary correction; the v0.1.0 validation result and its deferred items stand unchanged. |
| 0.1.2 | 2026-11-11 | PATCH documentary correction: the §12 "Human Approval Points" row *Approving this workflow as a framework asset* no longer states that the workflow remains unapproved (`In review`) until the decision; its `Effect on the agents` column now records that v0.1.0 was approved by the Human user on 2026-11-10 and independently validated (PASS WITH CONDITIONS, with `VAL-005`, `VAL-007`, and `VAL-100` deferred), so that approval has occurred and the workflow is `Approved` (VAL-P04). The decision, the deciding role, and the timing of the row are unchanged. No rule, procedural step, approval, or approved decision was changed. | Resolve validation finding VAL-P04, which recorded the approval-effect statement as obsolete after v0.1.0 had been approved. Residual correction applied under Human approval of 2026-11-11 and Software Architect authorization of 2026-11-11. | Documentation Agent | `Approved` — v0.1.0 approved by Human user on 2026-11-10; v0.1.2 PATCH documentary correction; the v0.1.0 validation result and its deferred items stand unchanged. |
