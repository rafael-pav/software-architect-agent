# Workflow WF-001 — Project Initiation

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-001` |
| Workflow name | Project Initiation |
| Version | `0.1.2` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-001` |
| Purpose | Establish an accurate, evidence-based picture of a project's current state before any lifecycle phase begins: inventory the available documentation and repository structure, identify gaps, contradictions, risks, and open questions, and produce a work plan for human authorization. |
| Status | `Approved` |
| Version | `0.1.2` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | The start of a project engagement, and any re-baselining of an engagement whose available project material has changed materially. |
| Related workflows | `WF-002` (next phase), `WF-005` (research), `WF-006` (documentation production), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§2–4, 10; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§2–4, 7, 9; [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) §4; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §§2–3. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `VAL`) keep the meanings given by the standard, template, or agent definition that establishes them; this workflow does not redefine them.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. Procedural conventions introduced by this workflow and not fixed by those sources are in effect as part of an approved workflow: this workflow was approved by the Human user on 2026-11-10 and independently validated (PASS), so those conventions are no longer pending `RECOMMENDATION` items. Approval does not change their normative rank — those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines how a project engagement is opened. It produces a defensible starting position: what documentation and repository material exists, which of it is authoritative, what is missing, what is contradictory, and what the agents propose to do next.

Its objective is to prevent two failure modes: beginning phase work on an assumed understanding of the project, and replacing or recreating existing documentation before it has been read.

This workflow does not produce project deliverables. It produces an audit, a work plan, and an authorization basis for the first authorized activity.

---

## 3. Trigger / When to Use

Use this workflow when:

- A new project engagement is opened by the human user.
- New original project material is supplied after an engagement has started, materially changing what is known.
- An engagement is resumed after a suspension long enough that the repository state can no longer be assumed.
- The Software Architect has reason to believe that existing documentation no longer reflects the project.

Do not use this workflow to re-open an approved decision. Changes to approved content follow `WF-009`.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Reading and inventorying repository structure and project material.
- Establishing which material is authoritative, provisional, superseded, or unreadable.
- Identifying missing information, contradictions, risks, and open questions.
- Proposing which lifecycle phases and deliverables apply, and which do not, with reasons.
- Preparing a work plan and the decision points it requires.
- Obtaining human authorization for the first authorized activity.

### 4.2 Deliberately excluded

- Drafting Phase 1, 2, or 3 deliverables. That work requires authorization through `WF-002`, `WF-003`, or `WF-004` and execution through `WF-006`.
- Resolving contradictions between sources. The workflow records them; the human user or the Software Architect decides.
- Modifying original project material under `input/existing-documentation/`, in any way and for any stated convenience.
- Application implementation, code, prototypes, infrastructure, or automation of any kind.
- Creating new framework assets. Missing templates or workflows observed during initiation are reported, not created.
- Declaring a phase complete. Phase completion is a gate decision governed by `WF-008`.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns the workflow. Inspects the repository, performs or directs the audit analysis, decides priorities, judges blocking status, reviews the work plan, and presents decisions to the human user. Writes no files. |
| **Documentation Agent** | Reads repository material and reports inventory findings to the Software Architect. Persists the audit or work plan only when the Software Architect authorizes it, with an explicit file list, under `docs/00-project-management/`. |
| **Research Agent** | Read-only. Investigates externally verifiable questions raised by the audit when assigned. Provides findings and sources; does not decide and does not write. |
| **Validation Agent** | Read-only. May review the completeness of the audit when the Software Architect assigns that review. Cannot authorize work, approve scope, or complete a phase. |
| **Human user / stakeholder** | Decides whether the work plan is accepted, which original material is authoritative where sources conflict, and which phase work is authorized to begin. |

No other agents exist in this system. No Planning Agent is defined; the Software Architect assumes Planning and Scope responsibility as stated in `AGENTS.md` §10.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- A human user has expressed an engagement request to the Software Architect.
- The Software Architect has read `AGENTS.md` and the agent definitions that govern the engagement.
- Read access to `input/existing-documentation/`, `project/`, `docs/`, and `framework/` is available.
- No phase work has been authorized yet, or — on re-baselining — prior decisions remain visible and unmodified.
- The Documentation Agent has read the documentation standard and the relevant templates before reporting anything as inventory evidence.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Repository instructions | `AGENTS.md`, `README.md` | **MUST** | Normative basis for permissions and boundaries. |
| Original project material | `input/existing-documentation/` | **SHOULD** | Read-only. May be absent for a project starting from zero. |
| Additional project context | `project/` | **MAY** | Read-only. |
| Existing generated documentation | `docs/00-project-management/` … `docs/05-validation/` | **MAY** | May be empty on first engagement. |
| Framework standards, templates, workflows | `framework/` | **MUST** for the Documentation Agent | Determines structure and reusable conventions. |
| Project objective and constraints as stated by the human user | Software Architect | **MUST** | Must be attributable to the human user, not inferred by an agent. |
| Prior authorization records | Software Architect | **MAY** | Required on re-baselining. |

---

## 7. Workflow Steps

1. **Confirm the initiation boundary.** The Software Architect restates, in its own working record, what the human user asked for: which project, which objective, which constraints, and which activities were *not* requested. An initiation request is not authorization for phase work.
2. **Confirm read-only treatment of original material.** The Software Architect and Documentation Agent acknowledge that `input/existing-documentation/` will be read and referenced, never edited, renamed, moved, replaced, or deleted (`AGENTS.md` §3.1).
3. **Inventory the repository structure.** The Software Architect, assisted by the Documentation Agent where useful, records the directory structure and the files present, including files that appear empty, duplicated by name, or in non-Markdown formats.
4. **Build the documentation inventory.** For each item, record: path, apparent title and purpose, format, apparent status, version or date if stated, language, stated owner if any, and readability. A row **MUST NOT** be completed from memory or expectation.
5. **Read the available material and classify what it is.** Distinguish authoritative sources, drafts, superseded material, material of unknown standing, and material that could not be read. Record the basis for each judgement.
6. **Identify gaps.** For each relevant area (objectives, scope, stakeholders, budget, constraints, dependencies, requirements, integrations, security and privacy, architecture, deployment), record what is expected but missing. Absence is a gap only where a phase deliverable or decision depends on it; state the dependency.
7. **Record contradictions with both locations.** Each contradiction **MUST** identify the conflicting statements, their documents and sections, and the decision it would affect. Contradictions **MUST NOT** be reconciled by an agent (`documentation-standards.md` §2.3).
8. **Record risks and open questions.** Give each a stable identifier from the project's register schemes, an owner or resolver, and a classification of `ASSUMPTION` or `OPEN QUESTION`. The Software Architect, not the author, decides which items are blocking for a phase gate (`documentation-standards.md` §8.2).
9. **Propose deliverable applicability.** Identify which Phase 1, 2, and 3 deliverables appear applicable to the project and which appear not applicable, with a reason for each exclusion. A proposed exclusion remains `RECOMMENDATION` until decided.
10. **Draft the work plan.** Sequence the proposed activities, name their dependencies, the research support they need, the validation points, and the human decisions they require. Mark the plan `RECOMMENDATION`; it is not an approved plan while it remains an agent proposal.
11. **Report to the Software Architect.** The Documentation Agent and Research Agent report findings with exact paths and identifiers. The Software Architect reviews, resolves what is within its authority (priorities, sequencing, whether to request clarification), and returns anything that requires clarification.
12. **Present the audit summary and work plan to the human user.** The Software Architect presents: current state, findings, risks and limitations, proposed work plan, pending decisions, and next actions, in the language required by `documentation-standards.md` §3.7.
13. **Obtain explicit authorization for the first authorized activity.** Record which activity is authorized, its scope, and any condition attached. Silence, a non-committal reply, or an inferred intent **MUST NOT** be treated as authorization (`WF-008`).
14. **Persist the audit or work plan only if authorized.** Hand the assignment to `WF-006` with an explicit list of permitted files under `docs/00-project-management/`. No audit template currently exists in `framework/templates/`; the Documentation Agent **MUST** apply the structure and metadata rules of `documentation-standards.md` §3 and **MUST NOT** invent or create a template.
15. **Hand over to the authorized activity.** Normally `WF-002` for Planning and Scope. Any other starting point is recorded with its authorization.
16. **Re-baseline when material changes.** If new material arrives later, repeat the affected steps, preserve prior findings, and route changes to already approved documents through `WF-009`.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Documentation Agent | Read repository material; report inventory, gaps, contradictions, and structural observations. | Read-only until a persistence assignment is issued. Findings go to the Software Architect, not into files. |
| Software Architect | Documentation Agent | Persist the audit summary or work plan. | Explicit authorization identifying each permitted file; `docs/00-project-management/` only; no template invention. |
| Software Architect | Research Agent | Verify externally observable facts named in the original material, or investigate feasibility questions raised by the audit. | Read-only; findings and sources only; no decisions; no file writes. |
| Software Architect | Validation Agent | Optional completeness review of the audit before the work plan is presented. | Read-only; findings to the Software Architect; cannot authorize work or complete a phase. |
| Software Architect | Human user | Decide on the work plan, the authoritative source set, and the first authorized activity. | Decisions are presented with alternatives, consequences, and a recommendation. |

Agent interactions are sequential and mediated by the Software Architect. No agent delegates to another agent, and the Documentation Agent does not launch other agents.

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Initiation boundary statement | Software Architect | What was requested and what was not. |
| Documentation inventory | Software Architect, with Documentation Agent support | Per-file record of material present, standing, and readability. |
| Gap register | Software Architect | Missing information, the decision or deliverable that depends on it, and its owner. |
| Contradiction register | Software Architect | Conflicting statements with both locations and affected decisions. |
| Risk and open-question list | Software Architect | Identified risks and unresolved questions, with owners and status. |
| Deliverable applicability proposal | Software Architect | Which deliverables apply, with reasons; explicitly a `RECOMMENDATION`. |
| Work plan | Software Architect | Sequenced activities, dependencies, research and validation points, required decisions. |
| Authorization record | Human user, recorded by the Software Architect | Which activity is authorized, its scope, date, and conditions. |
| Persisted audit or work plan (optional) | Documentation Agent | Project record under `docs/00-project-management/`, only when authorized. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Project Charter template | [`framework/templates/project-charter.md`](../templates/project-charter.md) | Not used for drafting here. Consulted to determine which information the audit must be able to supply for `WF-002`. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Same purpose: identifies scope information the audit must locate or flag as missing. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | Same purpose: identifies cost, alternative, and evidence inputs that may be absent. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Defines the structure a research finding must satisfy if the audit requires external evidence. |
| Documentation Standards | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Normative rules for classification, identifiers, sources, and metadata. |
| Documentation Agent definition | [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) | Write boundaries and required reporting. |

**Template availability (observed 2026-11-10).** No template exists for a documentation audit, an inventory, a gap register, a risk register, or an assumptions register. This workflow therefore records those artifacts as reports and registers that follow `documentation-standards.md` §3 when persisted. Creating a template requires separate Software Architect authorization and is outside this workflow.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Path evidence | Software Architect | Every inventory entry names a repository path that was actually opened. |
| No reconstruction | All agents | No document, date, version, or capability is described from memory, assumption, or expectation. |
| Readability limits | Software Architect | Material that could not be read is recorded as a limitation, never summarized as though it had been read. |
| Contradiction preservation | Software Architect | Contradictions appear with both locations and are not resolved by an agent. |
| Classification discipline | Software Architect, Documentation Agent | Inferences are `RECOMMENDATION`; unverified beliefs are `ASSUMPTION`; unknowns are `OPEN QUESTION`; `CONFIRMED` requires a citable source. |
| Write verification | Documentation Agent, Software Architect | The Documentation Agent reports every file it created or modified; the Software Architect checks that no other path changed. |
| Independent review (optional) | Validation Agent | If assigned, reviews the audit's completeness and the accuracy of its path references. Independent review of the audit is not approval of the work plan. |

The audit is not validated merely because the Documentation Agent reports it. Independent validation applies only when the Software Architect assigns it and the Validation Agent actually performs it.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Designation of authoritative original material where sources conflict | Human user, on the Software Architect's presentation | After contradictions are recorded, before phase drafting depends on them | Agents may not treat either conflicting source as authoritative until the designation is recorded. |
| Acceptance of the work plan | Human user | After the audit summary and work plan are presented | Agents may not begin the planned drafting work before acceptance. |
| Authorization to begin the first lifecycle phase | Human user | At the same decision point or later, explicitly | The phase workflow may start only for the authorized activity and scope. |
| Acceptance of documented gaps as tolerable for planning | Human user, with the Software Architect's recommendation | Before a plan is accepted | Gaps remain `OPEN QUESTION` items; they are not closed by acceptance of the plan. |

Agents **MUST NOT** infer any of these decisions from silence, from a general expression of interest, or from the existence of a repository. A recorded decision identifies the deciding role, the date, the scope, and any condition.

---

## 13. Completion Criteria

This workflow is complete when all of the following hold:

- [ ] The initiation boundary is recorded: what was requested and what was not.
- [ ] The repository structure and documentation inventory are recorded with paths that were actually read.
- [ ] Every item that could not be read is recorded as a limitation.
- [ ] Gaps are recorded with the deliverable or decision that depends on them.
- [ ] Contradictions are recorded with both locations and reported to the Software Architect.
- [ ] Risks and open questions are recorded with owners and status.
- [ ] Deliverable applicability is proposed with reasons and classified as a recommendation.
- [ ] The work plan is reported to the Software Architect and presented to the human user.
- [ ] Explicit human authorization for the first activity is recorded, with its scope and conditions.
- [ ] No original material, protected repository file, or file outside an authorized write scope was modified.
- [ ] No lifecycle phase has been described as complete.

Completion of this workflow does not complete any lifecycle phase and does not approve any decision.

---

## 14. Exception Handling

### 14.1 Insufficient information

Record the gap as `OPEN QUESTION` with an owner, the decision or deliverable it blocks, and the expected resolution point. Do not substitute an assumption for missing information without labeling it `ASSUMPTION` and stating its basis and verification path. The Software Architect decides whether the gap blocks planning.

### 14.2 Contradictions between sources

Record each contradiction with both locations, the affected decision, and the effect if it remains unresolved. Escalate to the Software Architect. Where the conflict concerns which original document governs, request the human designation described in §12. Do not merge, average, or silently prefer one source.

### 14.3 Material that cannot be read

Where a file is in a binary or unsupported format, is empty, is truncated, or cannot be decoded, record the format and the limitation. A rendered summary, an external preview, or an agent's recollection is not a substitute for the source. If the material is essential, the Software Architect requests a readable version from the human user.

### 14.4 Requests that fall outside the system's boundaries

Requests to modify original documents, edit protected repository files, write application code, create scripts, or add new framework assets are refused, explained, and reported to the Software Architect. The agent does not proceed on the assumption that the request implicitly authorizes the work.

### 14.5 Findings, blockers, and pending decisions

- A finding from the Validation Agent is handled under `WF-007`; it is never closed because a correction was drafted.
- A blocker is recorded as such only when the Software Architect designates it. If a blocker depends on a human decision, the workflow pauses at that decision rather than proceeding on a provisional basis.
- Pending decisions are listed for the human user; they are not resolved by agent preference.

### 14.6 Re-baselining an existing engagement

If material changes after this workflow completed, repeat steps 3 to 11 for the affected scope, keep earlier findings for traceability, and route any change to an already approved document through `WF-009`. Do not overwrite earlier audit conclusions.

### 14.7 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-001-01` | Should a documentation-audit artifact be a recognized project deliverable with its own template? | The audit is currently persisted, when at all, as an untemplated record under `docs/00-project-management/`. | Software Architect |
| `OQ-WF-001-02` | Which lifecycle phase receives the audit record by default: project management or planning? | Affects where the persisted record belongs and how later phases reference it. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Primary successor: the phase this workflow normally authorizes first. |
| [`WF-005` — Research](./research.md) | Invoked when the audit raises questions that require external evidence. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked to persist the audit or work plan when authorized. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked when the Software Architect assigns review of the audit or a later deliverable. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs how the work plan and phase authorizations are presented and recorded. |
| [`WF-009` — Change Control](./change-control.md) | Invoked when new material or a re-baselining affects previously approved content. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the project initiation workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable, evidence-based opening procedure for project engagements. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
