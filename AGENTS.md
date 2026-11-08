# General Agent Instructions

## 1. Project Purpose

This repository provides a reusable multi-agent system for software
engineering documentation and analysis.

The system supports the first three phases of the software development
lifecycle:

1. Project Planning and Scope
2. Requirements Analysis
3. System Design and Architecture

The system operates as a software engineering consultancy.

Its purpose is to analyze, research, plan, document, and validate
software projects.

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

If a task requires programming or changes to application source code,
explain the limitation and request human authorization.

## 3. Documentation Management

### Original Documentation

The directory `input/existing-documentation/` contains original
project materials supplied for analysis.

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

### Generated Documentation

The `docs/` directory is the destination for all generated
documentation, reports, analysis, and approved corrections.

Use the existing directory structure.

Do not create unnecessary duplicate documents.

Preserve previous versions when a change has significant impact.

## 4. Knowledge Classification

Every relevant project statement must be classified when its
certainty matters.

Use the following classifications:

- CONFIRMED: Explicitly supported by project information or an
  authoritative source.
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

## 6. Requirements and Traceability

Requirements must be uniquely identifiable.

Use these prefixes:

- FR: Functional Requirement
- NFR: Non-Functional Requirement
- BR: Business Rule
- UC: Use Case
- INT: Integration Requirement
- SEC: Security Requirement

Maintain traceability between relevant business rules,
requirements, use cases, architecture decisions, and future tests.

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

Agents may investigate and recommend alternatives,
but must not treat recommendations as approved decisions.

## 8. Validation

Important deliverables must undergo independent validation.

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

A deliverable with unresolved critical issues must not be
marked as approved.

## 9. Communication

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

## 10. Phase Completion

A project phase can only be considered complete when:

- Its required deliverables have been produced.
- Required validation has been performed.
- Critical inconsistencies have been resolved.
- Open questions and assumptions are documented.
- Required human approvals have been obtained.

The Architect is responsible for coordinating phase completion.