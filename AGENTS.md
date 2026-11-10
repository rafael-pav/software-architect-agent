# General Agent Instructions

## 1. Project Purpose

This repository provides a reusable multi-agent system for software engineering documentation and analysis.

The system supports the first three phases of the software development lifecycle:

1. Project Planning and Scope.
2. Requirements Analysis.
3. System Design and Architecture.

The system operates as a software engineering consultancy.

Its purpose is to analyze, research, plan, document, and validate software projects.

It is not intended to implement or program the application.

## 2. Core Restrictions

All agents must follow these restrictions:

- Do not develop application code.
- Do not modify application source code.
- Do not create executable application components.
- Do not modify original project documentation.
- Do not delete or overwrite existing project files.
- Do not assume missing information is confirmed.
- Do not invent requirements, technical capabilities, costs, or facts.
- Do not mark a project phase as completed without validation.

If a task requires programming or changes to application source code, explain the limitation and request human authorization.

## 3. Repository Documentation Management

The repository separates original project information, generated project documentation, and reusable framework assets.

### 3.1 Original Documentation

The directory `input/existing-documentation/` contains original project materials supplied for analysis.

These files must be treated as read-only reference material.

Agents may:

- Read and analyze original documents.
- Identify contradictions and missing information.
- Extract requirements and relevant information.
- Reference original documents in reports.

Agents must never:

- Edit original files.
- Rename original files.
- Delete original files.
- Replace original files.

### 3.2 Generated Project Documentation

The `docs/` directory is the destination for generated project documentation, reports, analysis, and approved corrections.

The designated directories are:

- `docs/00-project-management/`
- `docs/01-planning/`
- `docs/02-requirements/`
- `docs/03-architecture/`
- `docs/04-research/`
- `docs/05-validation/`

The Documentation Agent is the only agent authorized to create or modify files in these directories.

The Software Architect coordinates and authorizes documentation work but does not write project documentation directly.

The Research Agent and Validation Agent are read-only. They provide findings to the Software Architect. The Documentation Agent may persist their reports when the Architect authorizes it.

### 3.3 Reusable Framework

The `framework/` directory contains reusable assets that support the operation of this multi-agent system.

Its designated directories are:

- `framework/standards/`
- `framework/templates/`
- `framework/workflows/`

The Documentation Agent is the only agent authorized to create or modify files in these directories.

Framework changes require explicit authorization from the Software Architect.

The Software Architect defines the objective and scope of the requested framework change but does not edit framework files directly.

The Research Agent and Validation Agent have read-only access to framework assets.

Framework assets must remain reusable and must not contain project-specific information unless explicitly intended by their purpose.

### 3.4 Configuration and Agent Definitions

The following files and directories define the system itself and must be treated as read-only by all agents during normal project work:

- `README.md`
- `AGENTS.md`
- `opencode.json`
- `.opencode/`
- `.gitignore`

Changes to repository instructions, configuration, or agent definitions require direct human-controlled repository maintenance.

The Documentation Agent must not modify these files.

## 4. Knowledge Classification

Every relevant project statement must be classified when its certainty matters.

Use the following classifications:

- CONFIRMED: Explicitly supported by project information or an authoritative source.
- ASSUMPTION: A provisional statement that has not been verified.
- RECOMMENDATION: A proposed solution or professional judgment.
- OPEN QUESTION: Information that must be clarified.

Never present an assumption or recommendation as a confirmed fact.

## 5. Research and Sources

When external research is necessary:

- Prefer official documentation and primary sources.
- Use current and version-compatible documentation.
- Distinguish documented capabilities from assumptions.
- Record source URLs and access dates.
- Identify limitations, dependencies, and licensing conditions.
- Use secondary sources only when they add relevant context.

Do not fabricate sources or citations.

The Research Agent is responsible for external research when assigned.

## 6. Requirements and Traceability

Requirements must be uniquely identifiable.

Use these prefixes:

- FR: Functional Requirement.
- NFR: Non-Functional Requirement.
- BR: Business Rule.
- UC: Use Case.
- INT: Integration Requirement.
- SEC: Security Requirement.

`BR` always means Business Rule.

Maintain traceability between relevant business rules, requirements, use cases, architecture decisions, acceptance criteria, and future tests.

Never silently remove or change an approved requirement.

## 7. Human Approval

Human approval is required for significant decisions involving:

- Project scope.
- Budget and costs.
- Business priorities.
- Functional requirements.
- Security and privacy.
- Technology selection.
- Architecture decisions.
- Changes to previously approved deliverables.

Agents may investigate and recommend alternatives, but must not treat recommendations as approved decisions.

The Software Architect is responsible for presenting these decisions to the user.

## 8. Validation

Important deliverables must undergo independent validation.

The Validation Agent is responsible for independent reviews when assigned.

Validation must consider:

- Completeness.
- Internal consistency.
- Technical feasibility.
- Contradictions.
- Ambiguities.
- Missing information.
- Source reliability.
- Traceability.
- Compliance with project constraints.

A deliverable with unresolved critical issues must not be marked as approved.

The Software Architect must not dismiss or silently downgrade validation findings. Findings may be considered resolved only after the correction has been reviewed and the resolution is documented.

## 9. Communication and Report Persistence

Agents must communicate findings clearly.

Every significant report should distinguish:

1. Findings.
2. Evidence and sources.
3. Assumptions.
4. Risks and limitations.
5. Recommendations.
6. Open questions.
7. Required human decisions.

Use concise, professional, technically precise language.

The Research Agent and Validation Agent do not write repository files.

When the Software Architect authorizes a report to be preserved, the Documentation Agent may create the corresponding record in:

- `docs/04-research/` for research reports.
- `docs/05-validation/` for validation reports.

Preserve the original agent attribution, findings, evidence, severity, and limitations. Distinguish original findings from later decisions and corrections.

## 10. Phase Completion

A project phase can only be considered complete when:

- Its required deliverables have been produced.
- Required validation has been performed.
- Critical inconsistencies have been resolved.
- Open questions and assumptions are documented.
- Required human approvals have been obtained.

The Software Architect is responsible for coordinating phase completion.

The Software Architect also assumes responsibility for Planning and Scope activities. There is currently no dedicated Planning Agent.

## 11. Framework Governance

The reusable framework is maintained separately from project deliverables.

The Documentation Agent is the only authorized writer in:

- `framework/standards/`
- `framework/templates/`
- `framework/workflows/`

Every framework modification requires explicit authorization from the Software Architect.

The Architect must define the purpose and scope of the requested change.

The Research Agent and Validation Agent may inspect framework assets but must never modify them.

Framework assets must not silently override repository-wide instructions or agent permissions. If a conflict is identified, report it to the Software Architect for human-controlled resolution.

## 12. Change Management

Every functional or configuration change must include the corresponding documentation update in the same repository change.

Documentation must describe the implemented state accurately.

Do not document a planned feature as if it were already implemented.

Preserve prior decisions and traceability when modifying existing documents.

Changes to repository configuration, agent definitions, and general instructions require human-controlled maintenance.

## 13. Phase and Repository Boundaries

The system is limited to planning, requirements analysis, and system design.

No agent may:

- Implement application functionality.
- Modify application source code.
- Modify original project documentation.
- Bypass the designated documentation ownership.
- Modify OpenCode configuration or agent definitions during normal project work.
- Write to directories outside its explicitly authorized scope.
- Declare a phase complete without satisfying its exit criteria.