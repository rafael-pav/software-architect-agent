# Software Engineering Agents

## 1. Overview

This repository contains a multi-agent system built with [OpenCode](https://opencode.ai/) to support the documentation and analysis stages of the Software Development Life Cycle (SDLC).

The system coordinates specialized AI agents that collaborate on:

1. Planning and Scope.
2. Requirements Analysis.
3. System Design and Architecture.

It is designed to support the activities that take place before application development. It does not implement application code.

## 2. Agent Architecture

The system defines four specialized agents.

### Software Architect

**Mode:** Primary agent  
**Model:** `deepseek/deepseek-v4-pro#high`

The Software Architect is the main entry point and coordinator.

Responsibilities:

- Understand project objectives.
- Coordinate specialized agents.
- Delegate research, documentation, and validation tasks.
- Review and consolidate agent outputs.
- Manage project phases and phase gates.
- Present important decisions for human approval.
- Authorize changes to reusable framework assets.

The Software Architect does not directly write project documentation or framework assets.

### Research Agent

**Mode:** Subagent  
**Model:** `deepseek/deepseek-flash#high`

The Research Agent gathers and analyzes evidence to support project decisions.

Responsibilities:

- Research technical documentation.
- Evaluate technologies and alternatives.
- Investigate API capabilities and integrations.
- Identify technical limitations and dependencies.
- Research licensing and pricing.
- Provide sources and evidence.

The Research Agent is read-only and does not modify repository files.

### Documentation Agent

**Mode:** Subagent  
**Model:** `deepseek/deepseek-flash#high`

The Documentation Agent is the only agent authorized to write generated project documentation and reusable framework assets.

Its permitted write locations are:

**Project documentation**
- `docs/00-project-management/`
- `docs/01-planning/`
- `docs/02-requirements/`
- `docs/03-architecture/`
- `docs/04-research/`
- `docs/05-validation/`

**Reusable framework**
- `framework/standards/`
- `framework/templates/`
- `framework/workflows/`

Framework changes require explicit authorization from the Software Architect.

The Documentation Agent cannot modify repository configuration, agent definitions, original project documentation, or application source code.

### Validation Agent

**Mode:** Subagent  
**Model:** `deepseek/deepseek-v4-pro#high`

The Validation Agent independently reviews project documentation and agent outputs.

Responsibilities:

- Identify inconsistencies and contradictions.
- Review completeness and clarity.
- Check requirements traceability.
- Identify missing information and unresolved questions.
- Evaluate technical feasibility.

The Validation Agent is read-only and does not modify repository files.

## 3. Repository Structure

The repository's main tracked files include:

```text
software-engineering-agents/
│
├── .gitignore
│
├── .opencode/
│   └── agents/
│       ├── documentation-agent.md
│       ├── research-agent.md
│       ├── software-architect.md
│       └── validation-agent.md
│
├── AGENTS.md
├── opencode.json
└── README.md
```

The following directories are designated for repository operation and future assets:

```text
docs/
├── 00-project-management/
├── 01-planning/
├── 02-requirements/
├── 03-architecture/
├── 04-research/
└── 05-validation/

framework/
├── standards/
├── templates/
└── workflows/

input/
└── existing-documentation/

project/
```

The presence of a designated directory does not imply that it already contains completed assets.

## 4. Permission Model

The global OpenCode configuration denies file editing by default and defines specific permitted locations.

The Documentation Agent has explicit write permissions for the six designated `docs/` directories and the three designated `framework/` directories.

The Software Architect, Research Agent, and Validation Agent retain their own edit-deny rules. Their agent-specific denials take precedence over the global directory allowances.

Other restrictions include:

- Shell execution requires approval globally.
- Web searches and web retrieval require approval globally.
- External directory access requires approval globally.
- Subagent invocation requires approval globally.
- Research and Validation cannot write files.
- Documentation cannot execute shell commands or launch other agents.

OpenCode evaluates ordered permission rules using the last matching rule. Agent-specific rules are evaluated after global rules.

The configured permissions should still be verified through controlled runtime tests before being considered fully validated.

## 5. Repository Governance

The repository separates three types of information:

### Original project information

`input/existing-documentation/` contains original materials supplied for analysis.

These files are read-only and must remain unchanged.

### Generated project documentation

`docs/` contains project-specific deliverables, research reports, validation reports, and approved documentation updates.

The Documentation Agent is the only agent authorized to write in the designated documentation directories.

### Reusable framework assets

`framework/` contains reusable standards, templates, and workflows used by the multi-agent system.

The Documentation Agent is the only authorized writer in the designated framework directories. Each framework change requires explicit authorization from the Software Architect.

## 6. Operating Principles

The system follows the instructions in `AGENTS.md` and the individual agent definitions.

Core principles include:

- Preserve original project documentation.
- Do not invent project facts or requirements.
- Distinguish confirmed information, assumptions, recommendations, and open questions.
- Maintain consistency between project deliverables.
- Identify decisions that require human approval.
- Validate deliverables before considering a project phase complete.
- Keep the system focused on documentation and analysis rather than application implementation.
- Keep reusable framework assets separate from project-specific documentation.
- Update relevant repository documentation alongside functional or configuration changes.

## 7. Intended SDLC Coverage

### Phase 1 — Planning and Scope

Potential deliverables:

- Project Charter.
- Scope Statement.
- Stakeholder Analysis.
- Feasibility Study.
- Budget Estimate.
- Project Roadmap.
- Risk Register.
- Assumptions Register.

The Software Architect coordinates this phase. There is currently no dedicated Planning Agent.

### Phase 2 — Requirements Analysis

Potential deliverables:

- Software Requirements Specification.
- Functional Requirements.
- Non-Functional Requirements.
- User Stories.
- Use Cases.
- Acceptance Criteria.
- Business Rules.
- Requirements Traceability Matrix.

### Phase 3 — System Design and Architecture

Potential deliverables:

- Architecture Overview.
- C4 Architecture Views.
- Technology Stack Specification.
- Data Model and Entity Relationships.
- API Contracts.
- Integration Specifications.
- Security Architecture.
- UX/UI Specifications.
- Architecture Decision Records.
- Deployment Architecture.

These are intended areas of responsibility. Their applicability depends on each project's scope.

## 8. Current Development Status

The repository contains:

- Four agent definitions.
- A global OpenCode configuration.
- General project instructions.
- A Git repository.
- An initial multi-agent coordination test.

The initial test demonstrated that the Software Architect could delegate inspection tasks to the Research, Documentation, and Validation Agents and consolidate their responses.

The test did not independently verify all effective runtime permissions or demonstrate that prohibited write operations are blocked.

The reusable framework directories are designated for future standards, templates, and workflows. Their designation does not mean that a complete framework library has already been implemented.

### Pending Development Areas

- Verify effective runtime write permissions.
- Develop and maintain framework standards, templates, and workflows.
- Standardize deliverable names across agent definitions.
- Establish a consistent process for report persistence.
- Continue testing multi-agent coordination and phase gates.

## 9. Getting Started

The repository uses OpenCode as its agent execution environment.

Open a terminal in the repository directory and execute:

```powershell
opencode
```

The default agent is `software-architect`.

### Providing initial project information

To begin a project, describe its objective in the conversation; this alone is sufficient to start. You may also provide documents, but you are not required to prepare technical documents that the agents can analyze themselves.

- **Document location:** `input/existing-documentation/` is the only location for original project documents. They are read-only and are never edited, renamed, moved, replaced, or deleted.
- **Accepted formats:** Markdown and plain text; PDF and Office documents whose text can be extracted; and images/diagrams (accompany them with a brief text description). If a document cannot be read, the Software Architect will request a readable version.
- **Original vs. generated:** original documents are analyzed and referenced, never modified; all generated deliverables are written under `docs/`, kept separate from the originals.
- **Verbal or pasted input:** you may describe the project or paste text in the conversation; the Software Architect captures it as an attributable source and asks clarifying questions one at a time.

The Software Architect coordinates the specialized agents according to their instructions and permissions.

## 10. Scope and Limitations

This repository focuses on the analysis and documentation activities that precede software implementation.

It does not provide:

- Application source-code generation.
- Application development workflows.
- Automated software deployment.
- A complete library of project templates.
- A complete framework of documentation standards.
- A fully verified permission-enforcement test suite.