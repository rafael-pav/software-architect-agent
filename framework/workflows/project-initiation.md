# Workflow WF-001 — Project Initiation

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-001` |
| Workflow name | Project Initiation |
| Version | `0.2.0` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-001` |
| Purpose | Establish an accurate, evidence-based picture of a project's current state before any lifecycle phase begins: classify the intake state, interview the human user adaptively, inventory the available documentation with its provenance, identify gaps, contradictions, risks, and open questions, produce an approved Project Brief, and produce a work plan for human authorization. |
| Status | `Approved` |
| Version | `0.2.0` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | v0.1.2: independent validation PASS. v0.2.0: independent validation PASS (findings MEDIUM, LOW, and INFORMATIONAL resolved). |
| Applies to | The start of a project engagement — from an idea, partial documentation, complete documentation, or a modification to an existing system — and any re-baselining of an engagement whose available project material has changed materially. |
| Related workflows | `WF-002` (next phase), `WF-005` (research), `WF-006` (documentation production), `WF-008` (approval and phase gate), `WF-009` (change control), `WF-010` (technology capability assessment). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§2–4, 10; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§2–4, 7, 9; [`project-brief.md`](../templates/project-brief.md); [`project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md); [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) §4; [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) §§2–3. |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`BR`, `FR`, `NFR`, `UC`, `INT`, `SEC`, `AC`, `TST`, `ASM`, `OQ`, `RISK`, `DEC`, `ADR`, `VAL`, `OBJ`, `CON`, `SRC`, `DOC`, `GAP`, `CONFLICT`) keep the meanings given by the standard, template, or agent definition that establishes them; this workflow does not redefine them. `DOC`, `GAP`, and `CONFLICT` are the audit-manifest identifiers defined in [`project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md) §3, §4, and §5; `OBJ`, `CON`, `SRC`, `ASM`, `OQ`, `RISK`, and `DEC` are defined in the planning templates.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. The conventions introduced in v0.1.2 are in effect as part of an approved workflow: v0.1.2 was approved by the Human user on 2026-11-10 and independently validated (PASS). The intake, questioning, provenance, and Project Brief conventions introduced in v0.2.0 are in effect as part of the approved workflow: v0.2.0 was approved by the Human user on 2026-11-10 and independently validated (PASS). Approval does not change their normative rank — `AGENTS.md`, the agent definitions, and `documentation-standards.md` prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow defines how a project engagement is opened. It produces a defensible starting position: what documentation and repository material exists, which of it is authoritative, what is missing, what is contradictory, and what the agents propose to do next.

The engagement begins with **Discovery and Intake**. The Software Architect classifies the engagement into one of four intake states — `Idea (greenfield)`, `Partial documentation`, `Complete documentation`, or `Existing system modification` — and then interviews the human user conversationally, one question at a time, using the available material to avoid asking what is already answered. The result is consolidated into a **Project Brief** that the human user approves before Planning and Scope (`WF-002`) begins.

Its objective is to prevent two failure modes: beginning phase work on an assumed understanding of the project, and replacing or recreating existing documentation before it has been read.

This workflow does not produce Phase 1, 2, or 3 deliverables. It produces an intake classification, an audit and manifest, a Project Brief, a work plan, and an authorization basis for the first authorized activity.

---

## 3. Trigger / When to Use

Use this workflow when:

- A new project engagement is opened by the human user, whether from an idea, an existing set of documents, or a modification to a running system.
- New original project material is supplied after an engagement has started, materially changing what is known.
- An engagement is resumed after a suspension long enough that the repository state can no longer be assumed.
- The Software Architect has reason to believe that existing documentation no longer reflects the project.
- The human user supplies project information verbally, by pasted text, or by reference to documents that have not yet been delivered (§4.3, §7.1).

Do not use this workflow to re-open an approved decision. Changes to approved content follow `WF-009`.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Classifying the engagement into an intake state and confirming that classification with the human user (§4.3).
- Conducting the adaptive intake interview with the human user (§7.1).
- Reading and inventorying repository structure and project material.
- Recording the provenance of every original, and detecting duplicates and stale versions by content.
- Establishing which material is authoritative, provisional, superseded, or unreadable.
- Identifying missing information, contradictions, risks, and open questions.
- Producing a Project Brief through `project-brief.md`, for human approval.
- Proposing which lifecycle phases and deliverables apply, and which do not, with reasons.
- Preparing a work plan and the decision points it requires.
- Obtaining human authorization for the first authorized activity.
- Persisting the audit, the Project Brief, the work plan, and the authorization record under `docs/00-project-management/`.

### 4.2 Deliberately excluded

- Drafting Phase 1, 2, or 3 deliverables. That work requires authorization through `WF-002`, `WF-003`, or `WF-004` and execution through `WF-006`. The Project Brief records the intake understanding; it is not a charter, a scope statement, or a feasibility study.
- Resolving contradictions between sources. The workflow records them; the human user or the Software Architect decides.
- Modifying original project material under `input/existing-documentation/`, in any way and for any stated convenience.
- Reviewing, refactoring, or documenting application source code. For an `Existing system modification` engagement, only the system's documented behaviour, interfaces, and constraints are in scope.
- Choosing, installing, enabling, or configuring OpenCode mechanisms (Skills, Commands, Agents, MCP servers, Plugins). Mechanism choices follow `WF-010`, and any installation requires separate explicit human authorization.
- Application implementation, code, prototypes, infrastructure, or automation of any kind.
- Creating new framework assets. Missing templates or workflows observed during initiation are reported, not created.
- Declaring a phase complete. Phase completion is a gate decision governed by `WF-008`.

### 4.3 Discovery and Intake

Every engagement is classified before it is audited. The intake state determines the questioning path and the audit depth, so the classification is recorded explicitly and confirmed by the human user; an unconfirmed selection is an `ASSUMPTION`.

| Intake state | What it means | Questioning focus | Audit depth |
| --- | --- | --- | --- |
| `Idea (greenfield)` | No project material exists beyond the request itself. | Problem, outcomes, users, constraints, success measures. | Minimal. Confirm the repository state and record an empty or near-empty manifest as a finding. |
| `Partial documentation` | Some material exists; coverage, currency, and authority are uncertain. | What exists, what it covers, what it omits, which version governs, who owns it. | Focused. Manifest the supplied material and record gaps against what the lifecycle phases require. |
| `Complete documentation` | Material appears to cover the project's planning, requirements, and design scope. | Which documents are authoritative, approved, and current. | Full. Classify every document, analyse versions and duplicates, and review contradictions. |
| `Existing system modification` | A system already operates and the engagement concerns a change to it. | What the system does today, its documented interfaces, operational constraints, and what must change or remain. | Targeted. Inventory documented behaviour and interface records. **Application source code is out of scope:** only the system's documented behaviour, interfaces, and constraints are captured. |

The [`project-brief.md`](../templates/project-brief.md) template restates these four states and their effect for the reader; this section is the authoritative definition and prevails if the two differ.

**Adaptive interview.** The Software Architect interviews the human user conversationally, **one question at a time**. Each question is informed by the answers already given, the documentation already supplied, and the open questions already recorded. A question that is already answered by the material or by a prior answer **MUST NOT** be asked again. Each answer is classified as `CONFIRMED`, `ASSUMPTION`, or `OPEN QUESTION`; an assumption **MUST NOT** be converted into a confirmed fact without evidence or an explicit human confirmation. Where the engagement's state is ambiguous, the Software Architect states the ambiguity and asks the human user to choose.

**Project Brief.** The intake result is consolidated into a Project Brief using [`project-brief.md`](../templates/project-brief.md). The Project Brief **MUST** be approved by the human user before Planning and Scope (`WF-002`) begins. Approval of the brief confirms the intake understanding; it does not approve the project, its scope, its budget, or its priorities. `WF-002` §6.1 applies the same unconditional gate from the receiving side: it provides no exception, and where this workflow was not run, an equivalent approved brief is still required before Phase 1 drafting begins.

### 4.4 Delivery channels, provenance, and material locations

Two locations hold different classes of material, and the audit keeps them distinct:

| Location | Class | Treatment |
| --- | --- | --- |
| `input/existing-documentation/` | Original project material supplied by the human user. | Accepted delivery location for files. Read-only: never edited, renamed, moved, replaced, or deleted. |
| `docs/` | Generated project documentation, including this workflow's persisted records. | Written only by the Documentation Agent under an explicit authorization. Never treated as an original. |

- **Delivery channels.** Information may arrive as files, pasted text, verbal statements, or references to material that has not been supplied. Each is recorded as an attributable, dated source record (`SRC-NNN`) that names who provided it and through which channel. Information supplied verbally is not less valid than a file, but it is weaker evidence about an existing system's behaviour, and is classified accordingly.
- **Documents referenced but not provided.** The Software Architect requests them, and the absence is recorded as a gap until they arrive. Their contents must not be described from expectation.
- **Provenance.** Every original in the manifest records its delivery source, delivery date, and channel. Material without provenance cannot be assessed for authority.
- **Versions and duplicates.** Duplicate and stale material is identified by comparing content, not only file names. Every `superseded` designation records its basis.
- **Formats.** A PDF or Office document whose text can be extracted is readable evidence, and the extraction basis is recorded. Images, scans, and diagrams require a textual description supplied with the material; the description is attributed, not invented. Material that is genuinely unreadable is recorded as a limitation and a readable version is requested (§14.3).

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns the workflow. Classifies the intake state, conducts the adaptive intake interview with the human user one question at a time, inspects the repository, performs or directs the audit analysis, decides priorities, judges blocking status, reviews the Project Brief and the work plan, and presents decisions to the human user. Writes no files. |
| **Documentation Agent** | Drafts the audit and the Project Brief when authorized, applies the audit and Project Brief templates, records provenance and classification, and reports inventory findings to the Software Architect. Drafts nothing without an explicit file list. |
| **Research Agent** | Read-only. Investigates externally verifiable questions raised by the audit when assigned. Provides findings and sources; does not decide and does not write. |
| **Validation Agent** | Read-only. May review the completeness of the audit when the Software Architect assigns that review. Cannot authorize work, approve scope, or complete a phase. |
| **Human user / stakeholder** | Decides whether the work plan is accepted, which original material is authoritative where sources conflict, and which phase work is authorized to begin. |

No other agents exist in this system. No Planning Agent is defined; the Software Architect assumes Planning and Scope responsibility as stated in `AGENTS.md` §10. Questions about which OpenCode mechanism to use — a Skill, Command, agent, MCP server, or Plugin — are not resolved in this workflow; they follow `WF-010`.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- A human user has expressed an engagement request to the Software Architect.
- The Software Architect has read `AGENTS.md` and the agent definitions that govern the engagement.
- A respondent is available for the intake interview: either the human user or someone the human user has designated.
- The engagement can be classified into one of the four intake states, or the ambiguity can be stated as a question for the human user.
- Read access to `input/existing-documentation/`, `docs/`, and `framework/` is available.
- No phase work has been authorized yet, or — on re-baselining — prior decisions remain visible and unmodified.
- The Documentation Agent has read the documentation standard, `project-brief.md`, and `project-documentation-audit-and-manifest.md` before reporting anything as inventory evidence.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Repository instructions | `AGENTS.md`, `README.md` | **MUST** | Normative basis for permissions and boundaries. |
| Original project material | `input/existing-documentation/` | **SHOULD** | Read-only. May be absent for a project starting from zero. |
| Verbal or pasted project information | Human user | **MAY** | Captured as an attributable, dated source record; not left in conversation only. |
| Documents referenced but not provided | Human user | **SHOULD** be requested | Requested from the human user and recorded as a gap until delivered. |
| Existing generated documentation | `docs/00-project-management/` … `docs/05-validation/` | **MAY** | May be empty on first engagement. |
| Framework standards, templates, workflows | `framework/` | **MUST** for the Documentation Agent | Determines structure and reusable conventions. |
| Project objective and constraints as stated by the human user | Software Architect | **MUST** | Must be attributable to the human user, not inferred by an agent. |
| Prior authorization records | Software Architect | **MAY** | Required on re-baselining. |

---

## 7. Workflow Steps

The steps are grouped into three stages: Discovery and Intake, Documentation Audit, and Brief, Plan, and Authorization.

### 7.1 Stage A — Discovery and Intake

1. **Confirm the initiation boundary.** The Software Architect restates, in its own working record, what the human user asked for: which project, which objective, which constraints, and which activities were *not* requested. An initiation request is not authorization for phase work.
2. **Classify the intake state.** Using §4.3 and the material already available, the Software Architect proposes one of the four intake states, records the basis for the proposal, and asks the human user to confirm it. The state is recorded before the audit begins, so that the audit depth and the questioning path follow the engagement rather than an assumption about it. An unconfirmed selection is an `ASSUMPTION`.
3. **Conduct the adaptive intake interview.** The Software Architect interviews the human user conversationally, **one question at a time**, following this procedure:
   - Each question is informed by the answers already given, the documentation already supplied, and the open questions already recorded.
   - A question already answered by the material or by a prior answer **MUST NOT** be asked again. Where the same fact appears in more than one place, the Software Architect records the confirmation rather than repeating the question.
   - Each answer is recorded with its source and classified `CONFIRMED`, `ASSUMPTION`, or `OPEN QUESTION`. An answer the user gives about their own intent or constraints is attributable evidence; an answer about an existing system's behaviour is evidence of what the user believes, and is confirmed only by a documented source.
   - An `ASSUMPTION` **MUST NOT** be promoted to `CONFIRMED` by repetition, by the passage of time, or by an agent's inference. Promotion requires recorded evidence or an explicit human confirmation.
   - The interview ends when the Project Brief can be completed, or when every remaining gap is recorded as an `OPEN QUESTION` with an owner.
4. **Capture information delivered outside files.** When the human user speaks, pastes text, or refers to documents that have not been supplied, the Software Architect records an attributable source entry: what was provided, by whom, on which date, and through which channel (`SRC-NNN`), preserving the wording where feasible. Documents that are referenced but not provided are requested from the human user and recorded as a gap; their contents are never described from expectation.
5. **Confirm the accepted delivery location and read-only treatment.** The Software Architect and Documentation Agent confirm that original files are delivered to `input/existing-documentation/`, which is the **only** location for original documents, and are read and referenced only — never edited, renamed, moved, replaced, or deleted (`AGENTS.md` §3.1). `docs/` holds generated documentation only. The two are not interchangeable (§4.4).
6. **State the approval that will be required.** The Software Architect states that a Project Brief will be produced and that Planning and Scope (`WF-002`) may not begin until the human user approves it. This prevents the brief from being treated as a formality completed after planning has started.

### 7.2 Stage B — Documentation Audit

7. **Inventory the repository structure.** The Software Architect, assisted by the Documentation Agent where useful, records the directory structure and the files present, including files that appear empty, duplicated, or in non-Markdown formats, and including the absence of an expected directory.
8. **Build the documentation manifest with provenance.** Using [`project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md), record for each item: path, apparent title and purpose, format, apparent status, version or date if stated, language, stated owner if any, delivery source, delivery date, channel, and readability. A row **MUST NOT** be completed from memory, from a file name, or from expectation. Material whose delivery source, date, or channel cannot be established is recorded as such, and its authority is correspondingly limited.
9. **Analyse versions and duplicates by content.** Compare the supplied material for duplicates, earlier drafts, later revisions, and same-titled but different documents. Comparison is based on content — sections, identifiers, dates, change history, or extracted text — not on file name, timestamp alone, or directory position. Every `superseded` designation records its basis; where the basis is an agent's judgement, the designation remains a `RECOMMENDATION` until the Software Architect or the human user decides. Duplicate and superseded files are neither deleted nor renamed.
10. **Read the available material and classify what it is.** Distinguish authoritative sources, drafts, superseded material, material of unknown standing, and material that could not be read. Record the basis for each judgement.
11. **Identify gaps.** For each relevant area (objectives, scope, stakeholders, budget, constraints, dependencies, requirements, integrations, security and privacy, architecture, deployment), record what is expected but missing. Absence is a gap only where a phase deliverable or decision depends on it; state the dependency.
12. **Record contradictions with both locations.** Each contradiction **MUST** identify the conflicting statements, their documents and sections, and the decision it would affect. Contradictions **MUST NOT** be reconciled by an agent (`documentation-standards.md` §2.3).
13. **Record risks and open questions.** Give each a stable identifier from the project's register schemes, an owner or resolver, and a classification of `ASSUMPTION` or `OPEN QUESTION`. The Software Architect, not the author, decides which items are blocking for a phase gate (`documentation-standards.md` §8.2).

### 7.3 Stage C — Brief, Plan, and Authorization

14. **Propose deliverable applicability.** Identify which Phase 1, 2, and 3 deliverables appear applicable to the project and which appear not applicable, with a reason for each exclusion. A proposed exclusion remains `RECOMMENDATION` until decided.
15. **Draft the work plan.** Sequence the proposed activities, name their dependencies, the research support they need, the validation points, and the human decisions they require. Mark the plan `RECOMMENDATION`; it is not an approved plan while it remains an agent proposal.
16. **Draft the Project Brief.** Using [`project-brief.md`](../templates/project-brief.md), consolidate the intake result: intake state and its basis, problem statement, measurable objectives, users and stakeholders, preliminary scope, constraints, integrations, risks, assumptions, open questions, and approval status. Every statement carries its classification and source. The brief records the intake understanding; it does not decide scope, budget, or priorities.
17. **Report to the Software Architect.** The Documentation Agent and Research Agent report findings with exact paths and identifiers. The Software Architect reviews, resolves what is within its authority (priorities, sequencing, whether to request clarification), and returns anything that requires clarification.
18. **Present the audit summary, the Project Brief, and the work plan to the human user.** The Software Architect presents: current state, findings, risks and limitations, the proposed Project Brief, the proposed work plan, pending decisions, and next actions, in the language required by `documentation-standards.md` §3.7.
19. **Obtain the Project Brief approval and the authorization for the first authorized activity.** These are two recorded decisions:
    - Approval of the Project Brief by the human user, with approver and date, recorded in the brief's approval section.
    - Explicit authorization of the first authorized activity, with its scope and any condition attached. Silence, a non-committal reply, or an inferred intent **MUST NOT** be treated as authorization (`WF-008`).

    Approval of the brief is a precondition for `WF-002`; it is not a substitute for the scope, budget, and priority decisions that Phase 1 will present.
20. **Persist the records.** Persistence is mandatory, not conditional. The Software Architect issues the write assignment with an explicit file list, and the Documentation Agent writes the following under `docs/00-project-management/` using `WF-006`: the documentation audit and manifest, the approved Project Brief, the work plan, and the authorization record. Declining to persist the audit, the brief, or the authorization record is not a permitted outcome of this workflow. Where a project-specific reason prevents persistence, it is recorded as an `OPEN QUESTION` for the Software Architect and the gap is reported to the human user; the omission is never silent.
21. **Hand over to the authorized activity.** Normally `WF-002` for Planning and Scope, which requires the approved Project Brief. Any other starting point is recorded with its authorization.
22. **Re-baseline when material changes.** If new material arrives later, repeat the affected steps from 7 to 16, preserve prior findings, and route changes to already approved documents through `WF-009`. A change to an approved Project Brief follows `WF-009`; the brief is not edited in place.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Documentation Agent | Read repository material; report inventory, provenance, gaps, contradictions, and structural observations. | Read-only until a drafting or persistence assignment is issued. Findings go to the Software Architect, not into files. |
| Software Architect | Documentation Agent | Draft the documentation audit and manifest, and the Project Brief. | Explicit authorization naming each file; the audit template and the Project Brief template are applied; nothing is filled from expectation. |
| Software Architect | Documentation Agent | Persist the audit and manifest, the approved Project Brief, the work plan, and the authorization record. | Explicit file list; `docs/00-project-management/` only. Persistence itself is mandatory under §7.3 step 20; the authorization only fixes the files. |
| Software Architect | Research Agent | Verify externally observable facts named in the original material, or investigate feasibility questions raised by the audit. | Read-only; findings and sources only; no decisions; no file writes. |
| Software Architect | Validation Agent | Optional completeness review of the audit before the work plan is presented. | Read-only; findings to the Software Architect; cannot authorize work or complete a phase. |
| Software Architect | Human user | Decide on the work plan, the authoritative source set, and the first authorized activity. | Decisions are presented with alternatives, consequences, and a recommendation. |

Agent interactions are sequential and mediated by the Software Architect. No agent delegates to another agent, and the Documentation Agent does not launch other agents.

Mechanism questions raised during intake — whether a need calls for a Skill, a Command, an agent, an MCP server, or a Plugin — are referred to `WF-010`. This workflow neither chooses nor installs a mechanism.

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Initiation boundary statement | Software Architect | What was requested and what was not. |
| Intake state classification | Software Architect, confirmed by the human user | Which of the four states applies, the basis for it, and its effect on questioning and audit depth. |
| Documentation audit and manifest | Software Architect, drafted by the Documentation Agent when authorized | Per-file record of material present, provenance, standing, and readability; produced through `project-documentation-audit-and-manifest.md`. |
| Gap register | Software Architect | Missing information, the decision or deliverable that depends on it, and its owner. |
| Contradiction register | Software Architect | Conflicting statements with both locations and affected decisions. |
| Version and duplicate analysis | Software Architect | Content-based duplicate and stale-material findings, with the basis for each designation. |
| Risk and open-question list | Software Architect | Identified risks and unresolved questions, with owners and status. |
| Deliverable applicability proposal | Software Architect | Which deliverables apply, with reasons; explicitly a `RECOMMENDATION`. |
| Project Brief | Software Architect, drafted by the Documentation Agent when authorized | Consolidated intake record produced through `project-brief.md`, classified, and submitted for human approval. |
| Project Brief approval | Human user, recorded by the Software Architect | Approver, date, and any condition. Required before `WF-002`. |
| Work plan | Software Architect | Sequenced activities, dependencies, research and validation points, required decisions. |
| Authorization record | Human user, recorded by the Software Architect | Which activity is authorized, its scope, date, and conditions. |
| Persisted records (mandatory) | Documentation Agent | The audit and manifest, the approved Project Brief, the work plan, and the authorization record, under `docs/00-project-management/`, written under an explicit file list. |

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Project Brief template | [`framework/templates/project-brief.md`](../templates/project-brief.md) | Structure for the intake result and the approval that must precede `WF-002`. |
| Documentation Audit and Manifest template | [`framework/templates/project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md) | Structure for the manifest, provenance, gap, contradiction, duplicate, and readability analysis produced by the audit. |
| Project Charter template | [`framework/templates/project-charter.md`](../templates/project-charter.md) | Not used for drafting here. Consulted to determine which information the audit must be able to supply for `WF-002`. |
| Scope Statement template | [`framework/templates/scope-statement.md`](../templates/scope-statement.md) | Same purpose: identifies scope information the audit must locate or flag as missing. |
| Feasibility Study template | [`framework/templates/feasibility-study.md`](../templates/feasibility-study.md) | Same purpose: identifies cost, alternative, and evidence inputs that may be absent. |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Defines the structure a research finding must satisfy if the audit requires external evidence. |
| Documentation Standards | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Normative rules for classification, identifiers, sources, provenance, and metadata. |
| Documentation Agent definition | [`.opencode/agents/documentation-agent.md`](../../.opencode/agents/documentation-agent.md) | Write boundaries and required reporting. |

**Template availability (observed 2026-11-10).** Templates now exist for the documentation audit and manifest and for the Project Brief. Both were created as `Draft` v0.1.0 under Software Architect authorization, and neither has been independently validated or approved at the time of writing. Gap, contradiction, version/duplicate, and classification registers are sections of those templates rather than standalone templates; no template exists for a standalone risk register or assumptions register. Creating any further template requires separate Software Architect authorization and is outside this workflow.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Path evidence | Software Architect | Every inventory entry names a repository path that was actually opened. |
| No reconstruction | All agents | No document, date, version, or capability is described from memory, assumption, or expectation. |
| Intake-state basis | Software Architect | The intake state is recorded with the evidence that supports it, and an unconfirmed selection is an `ASSUMPTION`. |
| Provenance completeness | Software Architect, Documentation Agent | Every original records its delivery source, delivery date, and channel; material without provenance is not treated as authoritative. |
| Content-based duplicate analysis | Software Architect | Duplicate and stale determinations compare content; every `superseded` designation records its basis. |
| Format and readability | Software Architect | Extractable PDF or Office text is recorded as readable evidence; images and diagrams require an attributed textual description; unreadable material is recorded as a limitation, never summarized as though it had been read, and a readable version is requested. |
| Contradiction preservation | Software Architect | Contradictions appear with both locations and are not resolved by an agent. |
| Classification discipline | Software Architect, Documentation Agent | Inferences are `RECOMMENDATION`; unverified beliefs are `ASSUMPTION`; unknowns are `OPEN QUESTION`; `CONFIRMED` requires a citable source. No assumption is promoted by repetition. |
| Brief approval honesty | Software Architect, Documentation Agent | The Project Brief is never described as approved without a recorded approver and date, and approval of the brief is never presented as approval of scope, budget, or priorities. |
| Persistence verification | Software Architect, Documentation Agent | The mandatory records under `docs/00-project-management/` exist, or the omission is recorded as an `OPEN QUESTION` and reported to the human user. |
| Write verification | Documentation Agent, Software Architect | The Documentation Agent reports every file it created or modified; the Software Architect checks that no other path changed. |
| Independent review (optional) | Validation Agent | If assigned, reviews the audit's completeness and the accuracy of its path references. Independent review of the audit is not approval of the work plan. |

The audit is not validated merely because the Documentation Agent reports it. Independent validation applies only when the Software Architect assigns it and the Validation Agent actually performs it.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Confirmation of the intake state | Human user, on the Software Architect's proposal | After the state is proposed from the audit evidence, before the audit proceeds to conclusions | The state determines questioning and audit depth; an unconfirmed state remains an `ASSUMPTION`. |
| Designation of authoritative original material where sources conflict | Human user, on the Software Architect's presentation | After contradictions are recorded, before phase drafting depends on them | Agents may not treat either conflicting source as authoritative until the designation is recorded. |
| Approval of the Project Brief | Human user | After the audit and the brief are presented | Planning and Scope (`WF-002`) may not begin until the approval is recorded with approver and date. Approval does not approve the project, its scope, its budget, or its priorities. |
| Acceptance of the work plan | Human user | After the audit summary and work plan are presented | Agents may not begin the planned drafting work before acceptance. |
| Authorization to begin the first lifecycle phase | Human user | At the same decision point or later, explicitly | The phase workflow may start only for the authorized activity and scope. |
| Acceptance of documented gaps as tolerable for planning | Human user, with the Software Architect's recommendation | Before a plan is accepted | Gaps remain `OPEN QUESTION` items; they are not closed by acceptance of the plan. |

Agents **MUST NOT** infer any of these decisions from silence, from a general expression of interest, or from the existence of a repository. A recorded decision identifies the deciding role, the date, the scope, and any condition.

---

## 13. Completion Criteria

This workflow is complete when all of the following hold:

- [ ] The initiation boundary is recorded: what was requested and what was not.
- [ ] The intake state is recorded with its basis, and the human user has confirmed it or the selection is recorded as an `ASSUMPTION`.
- [ ] The intake interview used one question at a time, and no question already answered by the material was repeated.
- [ ] Repository structure and the documentation manifest are recorded with paths that were actually read, including delivery source, delivery date, and channel for every original.
- [ ] Duplicate and stale material has been analysed by content, and every `superseded` designation records its basis.
- [ ] Every item that could not be read is recorded as a limitation, and a readable version has been requested where the material is needed.
- [ ] Gaps are recorded with the deliverable or decision that depends on them, including documents referenced but not delivered.
- [ ] Contradictions are recorded with both locations and reported to the Software Architect.
- [ ] Risks and open questions are recorded with owners and status.
- [ ] Deliverable applicability is proposed with reasons and classified as a recommendation.
- [ ] The Project Brief is drafted from `project-brief.md`, classified, and submitted for human approval.
- [ ] The human user's approval of the Project Brief is recorded with approver and date.
- [ ] The work plan is reported to the Software Architect and presented to the human user.
- [ ] Explicit human authorization for the first activity is recorded, with its scope and conditions.
- [ ] The audit and manifest, the approved Project Brief, the work plan, and the authorization record are persisted under `docs/00-project-management/`, or a persistence omission is recorded as an `OPEN QUESTION` and reported to the human user.
- [ ] No original material, protected repository file, or file outside an authorized write scope was modified.
- [ ] No lifecycle phase has been described as complete.

Completion of this workflow does not complete any lifecycle phase and does not approve any decision.

---

## 14. Exception Handling

### 14.1 Insufficient information

Record the gap as `OPEN QUESTION` with an owner, the decision or deliverable it blocks, and the expected resolution point. Do not substitute an assumption for missing information without labeling it `ASSUMPTION` and stating its basis and verification path. The Software Architect decides whether the gap blocks planning.

### 14.2 Contradictions between sources

Record each contradiction with both locations, the affected decision, and the effect if it remains unresolved. Escalate to the Software Architect. Where the conflict concerns which original document governs, request the human designation described in §12. Do not merge, average, or silently prefer one source.

### 14.3 Material that cannot be read, and format handling

Format determines treatment:

- **PDF and Office documents with extractable text** are readable evidence. The extraction basis (for example, extracted text or a text layer) and the page or section reference are recorded, so that the statement can be traced back to the source.
- **Images, scans, and diagrams without extractable text** require a textual description. The description is attributed to the person who supplied or authored it; an agent does not invent one by looking at the image. Where a diagram and its description conflict, the conflict is recorded rather than resolved (`documentation-standards.md` §3.4).
- **Material that is genuinely unreadable** — corrupted, encrypted, empty, truncated, or in an unsupported encoding — is recorded as a limitation with its format and effect on the audit. A rendered summary, an external preview, or an agent's recollection is not a substitute for the source. If the material is essential, the Software Architect requests a readable version from the human user.

In every case, unreadable material is not summarized as though it had been read, and the audit states what could not be established because of it.

### 14.4 Requests that fall outside the system's boundaries

Requests to modify original documents, edit protected repository files, write application code, create scripts, or add new framework assets are refused, explained, and reported to the Software Architect. The agent does not proceed on the assumption that the request implicitly authorizes the work.

### 14.5 Findings, blockers, and pending decisions

- A finding from the Validation Agent is handled under `WF-007`; it is never closed because a correction was drafted.
- A blocker is recorded as such only when the Software Architect designates it. If a blocker depends on a human decision, the workflow pauses at that decision rather than proceeding on a provisional basis.
- Pending decisions are listed for the human user; they are not resolved by agent preference.

### 14.6 Re-baselining an existing engagement

If material changes after this workflow completed, repeat steps 7 to 16 for the affected scope, keep earlier findings for traceability, and route any change to an already approved document through `WF-009`. A change to an approved Project Brief also follows `WF-009`; the earlier version remains visible with its approval record. Do not overwrite earlier audit conclusions.

### 14.7 Information that arrives without a file

Where the human user provides information verbally, by pasted text, or by pointing to a document that cannot be supplied, the Software Architect:

- records it as an attributable source entry with speaker, date, and channel, preserving the wording where feasible;
- classifies the resulting statement for what it is — a record of what the user said — rather than promoting it to a confirmed fact about an existing system;
- requests any referenced document, and records its absence as a gap until it arrives;
- does not treat a conversation as an approved document, and does not reconstruct a referenced document's content from memory or expectation.

Where the volume of verbal material is large enough that its accuracy matters to a later decision, the Software Architect confirms the recorded summary with the human user before it is used as a basis.

### 14.8 Open questions about this workflow

| ID | Question | Why it matters | Owner | Status |
| --- | --- | --- | --- | --- |
| `OQ-WF-001-01` | Should a documentation-audit artifact be a recognized project deliverable with its own template? | The audit is persisted under `docs/00-project-management/`. | Software Architect | `Resolved` in v0.2.0 (approved by Human user on 2026-11-10) — the audit is recognized as a project-management record with its own template, [`project-documentation-audit-and-manifest.md`](../templates/project-documentation-audit-and-manifest.md). |
| `OQ-WF-001-02` | Which lifecycle phase receives the audit record by default: project management or planning? | Affects where the persisted record belongs and how later phases reference it. | Software Architect | `Resolved` in v0.2.0 (approved by Human user on 2026-11-10) — the default location is `docs/00-project-management/`, as recorded in §7.3 step 20 and in the template's `Applies to` field. |

Both resolutions were recorded under Software Architect authorization for the v0.2.0 consolidated change; like the rest of v0.2.0, they were approved by the Human user on 2026-11-10 and independently validated (PASS). A later change to either resolution follows `WF-009`.

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Primary successor: the phase this workflow normally authorizes first, and the consumer of the approved Project Brief. |
| [`WF-005` — Research](./research.md) | Invoked when the audit raises questions that require external evidence. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked to draft and persist the audit, the Project Brief, the work plan, and the authorization record. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked when the Software Architect assigns review of the audit, the Project Brief, or a later deliverable. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs how the Project Brief, the work plan, and phase authorizations are presented and recorded. |
| [`WF-009` — Change Control](./change-control.md) | Invoked when new material or a re-baselining affects previously approved content, including an approved Project Brief. |
| [`WF-010` — Technology Capability Assessment](./technology-capability-assessment.md) | Referred when the engagement raises a question about which OpenCode mechanism to use; this workflow neither chooses nor installs one. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the project initiation workflow, under explicit Software Architect authorization for the framework workflow stage. | Establish a repeatable, evidence-based opening procedure for project engagements. | Documentation Agent | `Draft` — not independently validated and not approved. |
| 0.1.1 | 2026-11-10 | Corrections after the first independent review: the section-structure note is reworded as a proposed convention for this asset class (VAL-001), and the open-questions block now states that none of its items blocks the procedural steps (VAL-004). | Apply authorized review corrections; no procedural step changed. | Documentation Agent | `Draft` — not re-validated and not approved |
| 0.1.2 | 2026-11-10 | Updated metadata to reflect independent validation PASS, status `In review`, and pending human approval. | Record the completed independent validation result without approving the workflow. | Documentation Agent | Approved by Human user on 2026-11-10. |
| 0.2.0 | 2026-11-10 | Consolidated expansion under Software Architect authorization: added the Discovery and Intake stage with four intake states and an adaptive one-question-at-a-time interview; added the Project Brief as a human-approved output preceding `WF-002`; added delivery-channel, provenance, content-based duplicate, and format handling (§4.4, §14.3, §14.7); made persistence of the audit, brief, work plan, and authorization record mandatory under `docs/00-project-management/`; defined the two material locations; updated the output, control, approval, and completion-criteria sections; referenced `project-brief.md`, `project-documentation-audit-and-manifest.md`, and `WF-010`; resolved `OQ-WF-001-01` and `OQ-WF-001-02`. | Address the initiation and intake gaps identified in the framework review (DIAG-001 to DIAG-006) and align the workflow with the new templates and capability-assessment workflow. Versioning: MINOR (additive new stages, procedures, and requirements; no previously approved decision, boundary, or baseline is altered or superseded). | Documentation Agent | Approved by Human user on 2026-11-10. |
