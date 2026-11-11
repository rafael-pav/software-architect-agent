# Reusable Documentation Standards — Index and Governance

| Field | Value |
| --- | --- |
| Purpose | Index and governance entry point for the reusable documentation standards of this repository. |
| Status | In review |
| Version | 0.4.0 |
| Last updated | 2026-11-10 |
| Owner role | Documentation Agent (sole authorized writer). |
| Authority / approval | v0.3.1 approved by Human user on 2026-11-09. The change incorporated in v0.4.0 was approved by the Human user on 2026-11-10, under Software Architect authorization of 2026-11-10 naming `framework/standards/README.md`, `framework/standards/documentation-standards.md`, and `framework/workflows/change-control.md`. v0.4.0 is not approved. The Software Architect coordinates, authorizes, and reviews standards work but does not write files. |
| Validation | v0.2.0: independent validation PASS (second review, 2026-11-09). v0.3.1: independent validation PASS (re-review, 2026-11-09). v0.4.0: pending independent validation. |
| Directory | `framework/standards/` |
| Related documents | [`documentation-standards.md`](./documentation-standards.md) — the standard indexed and governed by this README. |

---

## 1. Purpose

The `framework/standards/` directory contains the reusable documentation standards of this multi-agent software engineering system.

Standards define the conventions and quality criteria that documentation must follow consistently across projects. They are project-agnostic reference assets. They do not describe any specific project, stakeholder, budget, requirement, or architecture.

This README is the entry point for the directory and the governance reference for standards as a class of framework asset. It explains:

1. What the standards cover and do not cover.
2. Which standards currently exist.
3. Who may write, authorize, and review standards.
4. How standards are proposed, reviewed, approved, updated, and superseded.
5. How reusable standards relate to project-specific documentation under `docs/`.

---

## 2. Scope of the standards

### 2.1 In scope

Reusable standards in this directory may define:

- Documentation structure, formatting, and metadata conventions.
- Writing principles and terminology consistency.
- Classification of information according to certainty.
- Requirement and artifact identifiers, and rules governing their stability.
- Traceability conventions between requirements artifacts.
- Source attribution, references, and evidence quality expectations.
- How assumptions, open questions, risks, and decisions are recorded.
- Versioning, status, and change control for documents.
- Minimum quality criteria for a document to be considered complete.
- Documentation conventions specific to each of the three supported lifecycle phases.
- The documentation impact review that follows a change to project material, decisions, or documentation (see `documentation-standards.md` §9.6).

### 2.2 Out of scope

Standards in this directory deliberately do **not** cover:

- **Application implementation, programming, or source code.** The system is limited to Project Planning and Scope, Requirements Analysis, and System Design and Architecture. Standards do not define coding standards, build processes, deployment procedures, or executable components.
- **Executable automation.** Standards are descriptive documents, not scripts, pipelines, or tooling.
- **Project-specific content.** Budgets, stakeholders, requirements, schedules, technologies, and architecture decisions belong to project documentation, not to reusable standards.
- **Templates and workflows as deliverables.** Reusable document structures live in `framework/templates/`. Repeatable agent procedures live in `framework/workflows/`. These are separate asset classes and are **not** listed as standards in this README.
- **Repository configuration and agent definitions.** `README.md`, `AGENTS.md`, `opencode.json`, `.opencode/`, and `.gitignore` are governed by human-controlled repository maintenance, not by standards in this directory.
- **Original project material.** Files under `input/existing-documentation/` are read-only reference material and are never modified by standards or by documents that follow them.

### 2.3 Normative language

Standards in this directory distinguish mandatory rules from recommendations. The following keywords carry the stated meaning:

| Keyword | Meaning |
| --- | --- |
| **MUST / MUST NOT** | Mandatory rule. Deviation requires explicit authorization from the Software Architect and must be recorded. |
| **SHOULD / SHOULD NOT** | Recommended practice. Deviation is permitted when justified and recorded. |
| **MAY** | Optional practice, permitted without justification. |

A standard that does not distinguish these levels is non-compliant with this governance README.

---

## 3. Available standards

Only standards whose files actually exist in this directory are listed. The index reflects the current state of the directory; it is not a roadmap of intended assets.

| Standard | File | Purpose | Status |
| --- | --- | --- | --- |
| Documentation Standards | [`documentation-standards.md`](./documentation-standards.md) | Foundational standard for documentation produced during Planning and Scope, Requirements Analysis, and System Design and Architecture. Defines writing principles, the language policy, structure and metadata conventions, the four information classifications, the six requirement/artifact identifier prefixes, traceability, source and evidence handling, recording of assumptions/questions/risks/decisions, versioning and change control, the documentation impact review required after any change (§9.6), and minimum completion criteria. | In review |

No other standards currently exist. Templates (`framework/templates/`) and workflows (`framework/workflows/`) are separate asset classes and are intentionally not listed here.

---

## 4. Ownership and authorization

### 4.1 Roles

| Role | Responsibility for standards |
| --- | --- |
| **Documentation Agent** | Sole authorized writer. Creates and modifies standards files, but only when explicitly authorized by the Software Architect for a specific objective or asset. Reports conflicts rather than resolving them unilaterally. |
| **Software Architect** | Coordinates and authorizes standards work, defines the intended outcome and scope, reviews drafts, and requests human approval for significant changes. Does not write or edit standards files. |
| **Research Agent** | Read-only. May inspect standards and supply evidence relevant to them. Never modifies standards files. |
| **Validation Agent** | Read-only. Performs independent review of proposed or changed standards and reports findings to the Software Architect. Never modifies standards files and never writes validation reports into the repository. |
| **Human user / stakeholder** | Provides the approvals required for significant changes. |

### 4.2 Authorization rules

- The Documentation Agent **MUST NOT** create or modify a standard without explicit authorization from the Software Architect that identifies the intended objective or asset.
- General permission to work on project documentation does **not** authorize framework changes.
- Authorization to change one standard does **not** extend to other standards, templates, or workflows.
- The Documentation Agent **MUST NOT** expand the scope of the framework by introducing unrelated assets.
- Standards **MUST NOT** override or contradict `AGENTS.md`, `README.md`, `opencode.json`, or agent definitions. Where a conflict is identified, it must be reported to the Software Architect for human-controlled resolution.
- No agent may approve a standard on behalf of the human user.

### 4.3 Required checks before modifying an existing standard

1. Read the current version and related framework assets.
2. Identify the reason for the change and the requested objective.
3. Check whether templates, workflows, or other standards depend on the affected content.
4. Preserve existing valid conventions unless the Architect authorizes a change.
5. Report the expected impact of the modification.

---

## 5. Governance lifecycle for standards

Standards follow a controlled lifecycle. The stages below describe responsibilities and expected outputs; they do not imply that every stage has already occurred for any given asset.

### 5.1 Proposal

- Anyone may identify a documentation problem or a missing convention and raise it with the Software Architect.
- The Software Architect evaluates the proposal, defines the objective and scope, and decides whether to authorize drafting.
- A proposal **SHOULD** state: the problem, the affected documents or agents, the proposed scope, and the expected benefit.

### 5.2 Drafting

- The Software Architect assigns the task, with explicit authorization, to the Documentation Agent.
- The Documentation Agent checks for an existing asset that already covers the purpose, avoids duplicating rules across standards, templates, and workflows, and keeps terminology consistent with repository instructions.
- The draft is written as a reusable, project-agnostic asset with mandatory rules and recommendations clearly distinguished.
- A draft is not an approved standard. Its status field **MUST** reflect this.

### 5.3 Review

- The Software Architect reviews the draft for alignment with repository instructions, scope, and intended outcome.
- Important standards **MUST** undergo independent review by the Validation Agent when that agent is assigned.
- The Validation Agent reports findings with severity and precise references. It does not modify the standard and does not approve phase gates or business decisions.
- Findings **MUST NOT** be dismissed or silently downgraded. A finding is resolved only after the correction has been reviewed and the resolution is documented.

### 5.4 Approval

- The Software Architect consolidates review findings and presents the standard, with unresolved issues, to the human user.
- Human approval is required where a standard affects significant matters, including scope, business priorities, functional requirements, security and privacy, technology selection, or architecture decisions, and for any change to a previously approved standard.
- Approval is recorded explicitly in the standard's status and change history, including the approving role and date. Presence of a file in this directory **MUST NOT** be interpreted as approval.
- The Documentation Agent **MUST NOT** claim that a standard is approved, validated, or complete unless that approval or review actually occurred.

### 5.5 Publication and index maintenance

- When a standard is created, its entry is added to Section 3 of this README. The index **MUST** list only files that exist.
- When a standard is superseded, its entry is updated to identify the replacement. The original file is retained and marked as superseded; standards **MUST NOT** be deleted to hide prior decisions.
- The status recorded for a standard in Section 3 **MUST** reflect the status of that standard's current version and **MUST NOT** imply an approval that the version does not hold. When a standard's status changes, this index is updated in the same change.

### 5.6 Maintenance and change control

- Changes to an existing standard require the same authorization and review discipline as the original creation.
- Material changes are recorded in the standard's change history with version, date, summary, and reason.
- This README is subject to the same discipline and maintains its own change history in Section 9.
- Changes to a standard are subject to the documentation impact review defined in `documentation-standards.md` §9.6: the index in Section 3, the changed standard, and the templates or workflows that cite the affected section are reviewed together, not only the file being edited.
- Prior conventions and decisions are preserved unless a change is explicitly authorized.

---

## 6. Relationship to project-specific documentation

| Aspect | Reusable standards (`framework/standards/`) | Project documentation (`docs/`) |
| --- | --- | --- |
| Nature | Project-agnostic conventions and quality criteria. | Project-specific deliverables, analyses, and reports. |
| Content | Rules about *how* documentation is written, structured, classified, traced, and maintained. | Statements about *what* a particular project requires, assumes, decides, and plans. |
| Project facts | Must contain none. | Expected and required, with classification and sources. |
| Lifetime | Reusable across projects; revised through framework governance. | Scoped to a project and its lifecycle phases. |
| Writer | Documentation Agent, only when authorized by the Software Architect. | Documentation Agent, when assigned by the Software Architect. |
| Approval | Framework governance, including human approval of significant changes. | Project approvals by the human user, coordinated by the Software Architect. |
| Location | `framework/standards/` | `docs/00-project-management/`, `docs/01-planning/`, `docs/02-requirements/`, `docs/03-architecture/`, `docs/04-research/`, `docs/05-validation/` |

Standards define conventions; project documents follow them. Where a project document cannot comply, the deviation **MUST** be justified in that document and reported to the Software Architect. A project document **MUST NOT** silently redefine a standard, and a standard **MUST NOT** embed a project decision as if it were a rule.

Research reports persisted under `docs/04-research/` and validation reports persisted under `docs/05-validation/` remain project records. They follow the documentation standards for structure, classification, and evidence, while preserving original agent attribution, findings, severity, and limitations.

---

## 7. Compliance and escalation

- Standards apply to all generated documentation produced by this system.
- Conflicts between a standard and `AGENTS.md`, `README.md`, `opencode.json`, or an agent definition are resolved in favor of the repository instructions until the human user authorizes a controlled change.
- The Documentation Agent reports such conflicts to the Software Architect and does not modify protected repository files.
- Where repository instructions are silent, an approved standard may establish a convention. Until approval, a standard's convention is a proposal and must be described as such.

---

## 8. Related assets

- `framework/templates/` — reusable document structures (separate asset class; not indexed here).
- `framework/workflows/` — repeatable agent procedures (separate asset class; not indexed here).
- `AGENTS.md` — repository-wide agent instructions.
- `.opencode/agents/` — agent definitions and permissions.

---

## 9. Change history

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-09 | Initial creation of the standards index and governance README, under Software Architect authorization for `framework/standards/README.md` and `framework/standards/documentation-standards.md`. | Establish the directory entry point, the ownership and authorization model, and the governance lifecycle for standards. | Documentation Agent | Draft — not independently validated and not approved. |
| 0.2.0 | 2026-11-09 | Metadata block harmonized with `documentation-standards.md` §3.2: shared field names aligned, an explicit `Not approved` approval status recorded, and a related-documents field added. This change-history section added in response to review finding VAL-005. | Align this README with its own metadata and change-history requirements, and record corrections made under Software Architect authorization following review findings VAL-001 to VAL-005. | Documentation Agent | Draft — corrections applied; not re-validated and not approved at time of authoring; subsequently passed independent validation (second review, 2026-11-09); not approved. |
| 0.3.0 | 2026-11-09 | Version bump and state update: the indexed standard now incorporates resolved decisions `OQ-STD-001`, `OQ-STD-002`, and `OQ-STD-003`, the mandatory language policy, and the VAL-006 wording fix. Metadata, the Section 3 index entry, and validation state updated to match. | Keep this index accurate after the standards update applied under Software Architect authorization. | Documentation Agent | In review — changes applied; pending independent validation; not approved. |
| 0.3.1 | 2026-11-09 | Corrections applied following the independent review of v0.3.0: the indexed standard's §14 column is relabeled to `Status` (VAL-001); the v0.2.0 change-history note is reconciled with the v0.2.0 validation PASS (VAL-002); the language-policy precedence over the general deviation path is clarified (VAL-003); versioning terminology is standardized to "semantic-style version numbering" (VAL-004). The Section 3 status entry is now version-agnostic. | Keep this index consistent with the corrected standard and with the recorded validation state. | Documentation Agent | Approved by Human user on 2026-11-09 (following independent validation PASS). |
| 0.4.0 | 2026-11-10 | Index state synchronized with the indexed standard: the Section 3 entry records `In review` instead of `Approved`, and its purpose description now names the documentation impact review of §9.6 (VAL-001). §2.1 lists the documentation impact review within the scope of the standards, §5.5 adds the rule that the indexed status must reflect the current version's status, and §5.6 states that changes to a standard are subject to the §9.6 documentation impact review. Metadata status, version, last-updated date, approval status, and validation state updated accordingly. | Correct the index inconsistency reported as VAL-001, so that the index does not represent the indexed standard as approved while its current version is `In review`, and make the new §9.6 review visible in the governance README. | Documentation Agent | In review — additive change applied under Human approval of 2026-11-10 and Software Architect authorization of 2026-11-10; pending independent validation; not approved. |
