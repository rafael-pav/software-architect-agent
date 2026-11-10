# Workflow WF-010 — Technology Capability Assessment

## 1. Identification

| Field | Value |
| --- | --- |
| Workflow ID | `WF-010` |
| Workflow name | Technology Capability Assessment |
| Version | `0.1.0` |
| Status | `Approved` |

| Field | Value |
| --- | --- |
| Asset type | Reusable framework workflow. Procedural description for agents; not a script, not executable automation, and not a project document. |
| Workflow ID | `WF-010` |
| Purpose | Decide, for a stated need, which OpenCode mechanism is the appropriate way to meet it — native configuration, a Skill, a Command, an Agent (subagent), an MCP server, or a Plugin — and produce a recommendation with its comparison criteria, security and cost consequences, and the authorization it requires. It researches, compares, and recommends; it installs and configures nothing. |
| Status | `Approved` |
| Version | `0.1.0` |
| Last updated | `2026-11-10` |
| Owner role | Documentation Agent (sole authorized writer of framework assets), under Software Architect coordination. |
| Authority / approval | Approved by Human user on 2026-11-10. |
| Validation | PASS — independent validation completed; findings MEDIUM, LOW, and INFORMATIONAL resolved. |
| Applies to | Any framework-level or engagement-level need where an OpenCode mechanism choice is possible, and any proposal to add, enable, or change a Skill, Command, Agent (subagent), MCP server, or Plugin in this repository. |
| Related workflows | `WF-001` (initiation), `WF-002` (planning and scope), `WF-004` (system design and architecture), `WF-005` (research), `WF-006` (documentation production), `WF-007` (independent validation), `WF-008` (approval and phase gate), `WF-009` (change control). |
| Related documents | [`AGENTS.md`](../../AGENTS.md) §§2, 3.4, 11, 12; [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) §§4, 7, 9; [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) §§3, 6; [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md) §7; [`research-report.md`](../templates/research-report.md). |

**Identifier scheme.** Workflow identifiers in this asset class use the pattern `WF-NNN`, assigned sequentially and never reused. The scheme is outside the six requirement prefixes of `documentation-standards.md` §5.1, is documented here for the asset class as required by §5.5, and does not conflict with them. Other identifiers cited in this workflow (`CAP`, `OPT`, `FND`, `SRC`, `REC`, `RISK`, `OQ`, `ASM`, `DEC`, `FR`, `NFR`, `INT`, `SEC`) keep the meanings given by the standard, template, or agent definition that establishes them; this workflow does not redefine them. `CAP-NNN` is introduced by this workflow as the identifier for a capability need assessed here and is documented in §9.

**Normative basis.** This workflow introduces no documentation rule of its own. Where it states a rule, the rule derives from `AGENTS.md`, the agent definitions, or `documentation-standards.md`, and those sources prevail if this file conflicts with them. The mechanism mapping in §4 records the outcome of research verified against the installed OpenCode version and supplied to the Software Architect; it is a research finding, not a product guarantee, and it does not override repository instructions. Because this asset is approved (Human user, 2026-11-10) and independently validated (PASS), its procedural conventions are in effect as part of an approved workflow. Where a convention is not fixed by `AGENTS.md`, the agent definitions, or `documentation-standards.md`, those sources prevail if this file conflicts with them.

**Section structure.** The sixteen sections of this workflow are a **proposed convention for this asset class** — a `RECOMMENDATION` until a durable workflow-governance document is established. The order deviates from the section order recommended in `documentation-standards.md` §3.3, which is a SHOULD-level recommendation and not a mandatory rule. The deviation is recorded here and justified: a workflow is read as a procedure, so its order follows the execution sequence — identification, inputs, steps, outputs, controls, approval points, completion criteria — rather than a document's reading order. The standard's content requirements are still met in section 10 (references), section 12 (decisions and approval status), section 14 (assumptions, open questions, and risks), and section 16 (change history).

---

## 2. Purpose

This workflow answers one question per need: *what is the smallest, safest OpenCode mechanism that meets this need?*

It exists because the available mechanisms differ in ways that are easy to ignore: a Skill and a Command both look like "a saved instruction", an Agent and a Skill both look like "a reusable role", and an MCP server and a Plugin both look like "more capability". They differ substantially in authority, isolation, permission model, maintenance burden, and cost. Selecting the most powerful mechanism first produces systems that are harder to review, harder to constrain, and more expensive to run than the need required.

The workflow is **capability-first, then mechanism**. The need is stated as a capability gap; mechanisms are then compared as candidate implementations of that capability. The output is a recommendation to the human user, never an installation.

**Hard boundary.** This workflow researches, compares, and recommends only. Installing, enabling, or configuring a Skill, Command, Agent (subagent), MCP server, Plugin, or any other tool is a separate action that requires **explicit human authorization**, recorded with the exact change and its scope. No step in this workflow writes configuration, adds a dependency, or changes `.opencode/`, `opencode.json`, or any agent definition.

---

## 3. Trigger / When to Use

Use this workflow when:

- A need cannot be met by the current configuration and a mechanism choice is possible.
- A proposal is made to add a Skill, Command, Agent (subagent), MCP server, or Plugin.
- A requirement or validation finding implies a capability the system does not currently have.
- An existing mechanism is suspected to be the wrong choice, duplicated, or more powerful than necessary.
- The installed OpenCode version changes, invalidating a prior capability claim.

Do not use this workflow to:

- Install, enable, configure, or troubleshoot an installed mechanism. Those require separate authorization and are outside every agent's write scope in this repository.
- Bypass a permission or policy decision. A recommendation that a restriction is inconvenient is not a change to the restriction.
- Justify a mechanism that has already been chosen. The need and the criteria are fixed before options are compared.

---

## 4. Scope and Boundaries

### 4.1 In scope

- Stating the capability need in mechanism-neutral terms.
- Establishing whether the need is real, recurring, and attributable to an authorized objective.
- Comparing candidate mechanisms on consistent criteria (§4.3, §6.3).
- Recording the OpenCode version each capability claim was verified against.
- Stating the security surface, permission implications, and cost of each viable option.
- Recommending an option, or recommending that no mechanism be added.
- Reporting the recommendation, its conditions, and the authorization it would require.

### 4.2 Deliberately excluded

- Installing, enabling, disabling, configuring, or removing any mechanism.
- Modifying `opencode.json`, `.opencode/`, agent definitions, `.gitignore`, `README.md`, or `AGENTS.md`. Those changes are human-controlled maintenance (`AGENTS.md` §§3.4, 12).
- Writing application code, scripts, automation, or tool implementations for a Plugin or MCP server.
- Conducting independent research. Research is assigned to the Research Agent under `WF-005`.
- Approving expenditure, approving a mechanism, or accepting a security trade-off.

### 4.3 Decision framework — capability first

The need is classified by capability before any mechanism is considered. The mapping below states which mechanism is the natural fit for each kind of need; it does not state that the mechanism is available, approved, or free of cost in this environment.

**Attribution and standing.** The capability-first mapping is derived from the Software Architect's technology-capability research commission, reported by the Research Agent in a report dated 2026-11-10 and verified against the official OpenCode **v2.2.6** documentation. The full source list is retained with the commissioning session and is not duplicated here, per the authorization for this asset. The mapping remains a **research finding**, not a product guarantee and not an approved standard: per-use research is still required (§7 step 7), and each assessment re-verifies the capability claims against the installed version (§4.5).

| Capability need | Natural mechanism | Why this mechanism | Constraints to record |
| --- | --- | --- | --- |
| Reusable task instructions or knowledge that should apply across sessions, without a separate prompt each time | **Skill** | Instructions are packaged as reusable guidance loaded when relevant, rather than restated in every prompt. | Verify how and when the skill is loaded; record its scope and whether it can be invoked implicitly or only explicitly. |
| A deterministic, user-triggered prompt with a known input shape | **Command** | The invocation is explicit and repeatable; the user decides when it runs. | Commands are not a place for hidden policy; the prompt's effects remain subject to permissions. |
| Context isolation, a different role, or a narrower or different authority than the calling agent | **Agent (subagent)** | The work runs under its own context and its own permissions, so it cannot inherit capabilities it should not have. | Record the subagent's tool and permission surface; an agent boundary is not a sandbox substitute. |
| Access to external data or external tooling that does not exist in the repository | **MCP server** | The capability is provided by an external service through a defined protocol. | **Requires an explicit cost and context statement** (§4.4). An MCP server is an external dependency with its own access, trust, and availability model. |
| Behavior that cannot be expressed through configuration at all | **Plugin** | Only a Plugin can extend behavior beyond what configuration exposes. | **Last resort.** A Plugin executes code in the application's process and is **not sandboxed**; it is the largest security surface of the mechanisms listed here. |

**Enforcement versus convenience.**

- A requirement that **must not be overridable** — "the Documentation Agent may never write outside `docs/`", "no agent may modify `AGENTS.md`" — is an **enforcement** concern. It belongs in a **policy** mechanism that holds regardless of who asks, and in the repository instructions that agents must follow.
- A requirement that exists for **convenience or accident prevention** — "ask before running shell commands", "ask before web access" — is a **permission** concern. Permissions reduce mistakes; they are not a substitute for a rule that must be non-overridable.

Recording the wrong one of these is a substantive defect: a convenience permission presented as an enforcement boundary overstates the guarantee, and an enforcement rule implemented as a permission understates the risk.

### 4.4 Cost statements

Every candidate carries a cost statement, even when the cost is zero. At minimum:

| Cost dimension | What must be stated |
| --- | --- |
| Monetary | Any subscription, per-call, per-token, or licensing cost, with its basis, currency, and source. |
| Context | How much context the mechanism consumes or injects, and when. An MCP server's tool definitions and responses consume context even when unused. |
| Operational | Installation, upgrade, monitoring, credential management, availability dependency, and failure modes introduced. |
| Maintenance | Who must keep it working, and what breaks when the upstream service or the OpenCode version changes. |

An MCP server proposal without a cost and context statement is incomplete and **MUST NOT** be presented as a recommendation.

### 4.5 Version verification

Every capability claim **MUST** be stamped with the OpenCode version it was verified against.

- The version against which the mapping in §4.3 was verified is **v2.2.6**: the installed version recorded when this workflow was drafted, and the version named in the Research Agent's technology-capability report dated 2026-11-10.
- Official documentation **SHOULD** be read at the release tag corresponding to the installed version, not only at the "latest" documentation, because behavior documented for a later release may not exist in the installed one, and behavior present in the installed release may be undocumented at "latest".
- Where the installed version differs from the version a claim was verified against, the claim is `ASSUMPTION` until re-verified, and the affected recommendation is re-opened.
- Where documentation is silent, the gap is recorded. Silence is not evidence of absence, and an inference is not a documented capability.

---

## 5. Responsible Agent and Participants

| Role | Responsibility in this workflow |
| --- | --- |
| **Software Architect** | Owns the workflow. Defines the capability need, decides whether it warrants assessment, fixes the comparison criteria, evaluates the research, and forms the recommendation to the human user. Writes no files and installs nothing. |
| **Research Agent** | Read-only. Investigates mechanism capabilities and limitations under `WF-005`: official documentation at the applicable release tag, version applicability, security surface, permission model, licensing, and cost. Supplies findings, sources, and limitations; makes no decision and writes no file. |
| **Documentation Agent** | Records an assessment or recommendation only when the Software Architect authorizes persistence, with an explicit path and scope. Applies `research-report.md` for research findings and the project or framework document convention for the assessment record. Does not decide, research, or configure. |
| **Human user / stakeholder** | Decides the need is worth meeting, accepts the recommendation or rejects it, and **authorizes any installation or configuration** with its exact scope. |
| **Validation Agent** | Read-only, when assigned. May review the completeness and internal consistency of the comparison and whether its claims are properly version-stamped. Cannot approve a mechanism or authorize an installation. |

No agent in this workflow installs, enables, or configures a mechanism. The participants do not delegate to one another; all interaction is mediated by the Software Architect.

---

## 6. Preconditions and Inputs

### 6.1 Preconditions

- The need is stated in mechanism-neutral terms: what must be possible, for whom, and why.
- The installed OpenCode version is known and recorded.
- The repository instructions and agent definitions that constrain the answer have been read.
- The Software Architect has accepted that an assessment is warranted, rather than a configuration change or a documentation change.
- Participants understand that this workflow cannot install anything.

### 6.2 Inputs

| Input | Source | Requirement | Notes |
| --- | --- | --- | --- |
| Capability need statement | Software Architect | **MUST** | Mechanism-neutral; names the actor, the task, and the frequency. |
| Objective or requirement the capability serves | Project or framework record | **MUST** | A need with no authorized objective is recorded as a `RECOMMENDATION` at most. |
| Installed OpenCode version | Human user or environment | **MUST** | Version stamp for every capability claim. |
| Repository instructions and agent definitions | `AGENTS.md`, `.opencode/agents/` | **MUST** | Constraints that eliminate options before comparison. |
| Comparison criteria | Software Architect | **MUST** | Fixed before any option is assessed. |
| Research findings | Research Agent, via `WF-005` | **MUST** for any capability claim | Official sources at the applicable release tag, with version and limitations. |
| Current configuration | `.opencode/`, `opencode.json` | **SHOULD** | Read-only inspection; determines whether the need is already met. |
| Prior assessments | Framework or project records | **MAY** | Reused with their version stamp; a stale stamp triggers re-verification. |

### 6.3 Comparison criteria

Every viable option is assessed against the same criteria, defined before assessment:

| Criterion | What is compared |
| --- | --- |
| Utility | Whether the mechanism actually meets the need, including edge cases and failure behavior. |
| Security surface | What the mechanism can reach, what it can execute, and what it can exfiltrate. A Plugin is not sandboxed; an MCP server is an external trust boundary. |
| Permission model | Whether the mechanism's effects can be constrained per action, per tool, or per resource, and whether constraints can be overridden. |
| Maintenance burden | Who keeps it working, how it is upgraded, and what breaks on an OpenCode version change. |
| Cost | Monetary, context, operational, and maintenance cost under §4.4. |
| Reversibility | How easily the mechanism can be removed, and what residue it leaves in configuration or data. |

Where an option cannot be assessed against a criterion, record `Not assessed` with the reason. Do not score it arbitrarily.

---

## 7. Workflow Steps

1. **Receive and restate the need.** The Software Architect restates the capability need in mechanism-neutral terms and names the objective, requirement, or finding it serves. If the need is expressed as a preferred mechanism ("add an MCP server for X"), restate the underlying capability and set the mechanism aside until step 6.
2. **Confirm that assessment is the right activity.** Verify that the need is not already met by existing configuration, that it is not a documentation or process gap, and that no permission or policy decision is being circumvented. A need that is really a rule change is routed to `WF-009` and human-controlled maintenance.
3. **Record the environment baseline.** Record the installed OpenCode version, the relevant configuration in force, and the date. This baseline stamps every subsequent capability claim.
4. **Fix the comparison criteria.** Confirm the criteria in §6.3, adding project-specific criteria where justified, before any option is examined in detail.
5. **Enumerate candidate mechanisms.** Include native configuration, Skill, Command, Agent (subagent), MCP server, and Plugin where plausible, plus "no mechanism: change the process or accept the limitation". Record why an option was excluded before assessment only when the exclusion is structural, such as an instruction in `AGENTS.md`.
6. **Apply the capability-first mapping.** Use §4.3 to identify the natural mechanism for the need, and record where the need spans more than one mechanism, since that is a signal the need should be split.
7. **Commission research where a claim is not already evidenced.** The Software Architect assigns the Research Agent under `WF-005`, with the specific questions: does the mechanism exist in the installed version, how is it invoked, what authority does it run with, what does it cost, and what does the official documentation say at the release tag. Do not accept recollection, community posts, or "latest" documentation as proof of behavior in the installed version.
8. **Classify enforcement versus convenience.** For each requirement the mechanism must satisfy, record whether it must be non-overridable (**policy**) or is an accident-prevention measure (**permission**). Record the consequence of misclassifying it.
9. **Assess each option on the fixed criteria.** Utility, security surface, permission model, maintenance burden, cost, reversibility. State confidence and its basis for each assessment.
10. **Produce the cost and context statement.** For every option, complete §4.4. For an MCP server, state what it injects into context, what it depends on, and what fails when it is unavailable.
11. **State the security consequences.** Identify what the mechanism can reach beyond the repository, what runs with the agent's authority, and which mechanism carries the largest surface. A Plugin recommendation **MUST** state that Plugins are not sandboxed and are the last resort.
12. **Recommend one option, or recommend none.** The recommendation names the mechanism, the configuration shape at the level of intent, the conditions under which it remains appropriate, and what would make it wrong. Recommendations remain `RECOMMENDATION` until accepted.
13. **State the authorization required.** Name precisely what a human decision would authorize: which mechanism, which configuration file or directory would change, what would be installed or enabled, and what access it would receive. "Approve the improvement" is not an authorization.
14. **Report to the Software Architect.** Deliver the assessment with its version stamp, findings, criteria, costs, security consequences, recommendation, and open questions. Research findings are attributed to the Research Agent and are not restated as the Documentation Agent's conclusions.
15. **Present the decision to the human user.** The Software Architect presents the need, the options, the criteria, the comparison, the recommendation, the residual risks, and the exact authorization requested, in the language required by `documentation-standards.md` §3.7.
16. **Record the outcome, not the installation.** When authorized, the Documentation Agent persists the assessment or recommendation under an explicit write assignment. Acceptance, rejection, deferral, and the scope of any installation authorization are recorded with approver and date.
17. **Stop at the installation boundary.** If the human user authorizes an installation or configuration change, that change is executed through human-controlled repository maintenance, not by an agent under this workflow. Agents **MUST NOT** perform it on the strength of an accepted recommendation.
18. **Re-verify when the baseline changes.** When the installed OpenCode version, the configuration, or the upstream service changes, re-verify the affected claims, keep the earlier assessment visible, and re-open the recommendation under `WF-009` where it supported an approved decision.

---

## 8. Delegation and Agent Interactions

| From | To | Assignment | Constraints |
| --- | --- | --- | --- |
| Software Architect | Research Agent | Capability questions for a named need and a named version. | Read-only; official sources at the release tag; version applicability stated; no recommendation of an option as a decision. |
| Software Architect | Documentation Agent | Persist an assessment or recommendation record. | Explicit path and file list; no configuration changes; preserve attribution and version stamps. |
| Documentation Agent | Software Architect | Report of what was recorded, what remains unverified, and what authorization the recommendation requires. | Does not assess, decide, or configure. |
| Software Architect | Validation Agent | Review of the comparison's completeness and consistency. | Read-only; cannot approve a mechanism or authorize installation. |
| Software Architect | Human user | The capability decision and any installation authorization. | Presented with alternatives, costs, security consequences, and residual risk. |

No agent delegates installation or configuration work, and no agent delegates to another mechanism choice. The Documentation Agent does not launch agents.

---

## 9. Expected Outputs

| Output | Owner | Description |
| --- | --- | --- |
| Capability need statement | Software Architect | The need in mechanism-neutral terms, with the objective it serves. `CAP-NNN`. |
| Environment baseline | Software Architect | Installed OpenCode version, relevant configuration, date. |
| Option comparison | Software Architect, on Research Agent evidence | Options assessed on the fixed criteria, including excluded and unassessed options. |
| Cost and context statement | Software Architect | Monetary, context, operational, and maintenance cost per option. |
| Security and permission assessment | Software Architect | Security surface, permission model, and enforcement-versus-convenience classification. |
| Recommendation | Software Architect | One option, or none, with conditions and the authorization it requires. `REC-NNN` where recorded as a register entry. |
| Decision and authorization record | Human user, recorded by the Software Architect | Accepted, rejected, deferred; and the exact installation authorization, if any. |
| Persisted assessment (conditional) | Documentation Agent | Written only on explicit authorization, at the authorized path. |

`CAP-NNN` is introduced by this workflow as a register identifier for a capability need and is not a requirement prefix. `FND-NNN`, `OPT-NNN`, `SRC-NNN`, `OQ-NNN`, and `REC-NNN` keep the meanings given in [`research-report.md`](../templates/research-report.md) §§3, 5, 6, 8, and 9 respectively. Where a project or framework register already uses these prefixes, a single sequence is allocated per type (`documentation-standards.md` §5.4).

---

## 10. Related Templates and Documents

| Asset | Path | Use in this workflow |
| --- | --- | --- |
| Research Report template | [`framework/templates/research-report.md`](../templates/research-report.md) | Structure for the mechanism research this workflow relies on, including sources, version applicability, alternatives, and limitations. |
| Architecture Decision Record template | [`framework/templates/architecture-decision-record.md`](../templates/architecture-decision-record.md) | Structure when an accepted mechanism choice becomes an architecture-level decision with alternatives and consequences. |
| Project Brief template | [`framework/templates/project-brief.md`](../templates/project-brief.md) | Carries a capability need that originates at intake, where it affects scope or constraints. |
| Documentation Standards | [`framework/standards/documentation-standards.md`](../standards/documentation-standards.md) | Classification, evidence fields, version applicability, and approval-status honesty. |
| Repository instructions | [`AGENTS.md`](../../AGENTS.md) | Write boundaries, framework authorization, and the rule that configuration changes are human-controlled maintenance. |
| Software Architect definition | [`.opencode/agents/software-architect.md`](../../.opencode/agents/software-architect.md) | Decision presentation, delegation, and the prohibition on making significant technical decisions without approval. |
| Research Agent definition | [`.opencode/agents/research-agent.md`](../../.opencode/agents/research-agent.md) | Research method, evidence fields, and report structure for the mechanism findings. |

**Template availability (observed 2026-11-10).** No template exists for a capability assessment record or an options register as such. The assessment is recorded either as a research report through `research-report.md`, as an architecture decision through `architecture-decision-record.md`, or as a framework document following `documentation-standards.md` §3, as the Software Architect directs. No new template may be created without separate authorization.

---

## 11. Validation and Quality Controls

| Control | Applied by | Requirement |
| --- | --- | --- |
| Need stated before mechanism | Software Architect | The need is mechanism-neutral and attributable to an objective; a mechanism-first request is restated before assessment. |
| Criteria fixed before assessment | Software Architect | No option is scored before the criteria are recorded. |
| Version stamp | Software Architect, Research Agent | Every capability claim names the OpenCode version verified against; unstamped claims are `ASSUMPTION`. |
| Release-tag documentation | Research Agent | Official documentation is read at the applicable release tag, not only at "latest"; the access date is recorded. |
| Cost disclosure | Software Architect | Every option carries a cost and context statement; an MCP option without one is not recommendation-ready. |
| Security disclosure | Software Architect | The security surface and the non-sandboxed nature of Plugins are stated, not implied. |
| Enforcement versus convenience | Software Architect, Validation Agent | Each requirement is classified as policy or permission, and a misclassification is treated as a defect. |
| No unauthorized change | All agents | Nothing is installed, enabled, or configured; the only write is an authorized record. |
| Independent review (optional) | Validation Agent | Reviews completeness, consistency, and version discipline; does not approve the mechanism. |
| Recommendation honesty | Documentation Agent | A recommendation is never recorded as an accepted decision or an installation. |

An assessment is not validated because it was recorded. Independent validation applies only when the Software Architect assigns it and the Validation Agent performs it.

---

## 12. Human Approval Points

| Decision | Deciding role | When | Effect on the agents |
| --- | --- | --- | --- |
| Whether the need warrants a mechanism at all | Human user, on the Software Architect's recommendation | After the need is stated and before options are compared in detail | No assessment proceeds toward a recommendation without a stated objective. |
| Acceptance of the recommended mechanism | Human user | After the comparison, costs, and security consequences are presented | A recommendation remains `RECOMMENDATION` until accepted; acceptance is recorded with approver and date. |
| Authorization to install, enable, or configure a mechanism | Human user, explicitly and with exact scope | After acceptance, as a distinct decision | No agent installs or configures anything. Any change to `opencode.json`, `.opencode/`, or an agent definition is human-controlled repository maintenance. |
| Acceptance of a residual security or cost risk | Human user | Before an option with an unmitigated risk is accepted | The risk is recorded against the decision, not absorbed into the prose. |
| Authorization to persist an assessment record | Software Architect | Before the Documentation Agent writes any file | Persistence is not approval and does not authorize installation. |

Agents **MUST NOT** infer any of these decisions from enthusiasm, from an accepted recommendation, or from the existence of a configuration that already permits the change.

---

## 13. Completion Criteria

An assessment under this workflow is complete when all of the following hold:

- [ ] The capability need is stated in mechanism-neutral terms and linked to an objective, requirement, or finding.
- [ ] The installed OpenCode version and relevant configuration are recorded as a baseline.
- [ ] Comparison criteria were fixed before options were assessed.
- [ ] All plausible mechanisms were enumerated, and any excluded option has a recorded reason.
- [ ] Each viable option is assessed on the fixed criteria, or marked `Not assessed` with a reason.
- [ ] Every option carries a cost and context statement.
- [ ] The security surface, permission model, and enforcement-versus-convenience classification are recorded.
- [ ] Every capability claim carries the OpenCode version it was verified against.
- [ ] One option, or none, is recommended, with its conditions and the conditions under which it would be wrong.
- [ ] The exact authorization a human decision would grant is stated.
- [ ] The outcome is recorded, and no installation or configuration was performed by an agent.
- [ ] No repository configuration, agent definition, or protected file was modified.

Completion of this workflow does not approve a mechanism and does not authorize an installation.

---

## 14. Exception Handling

### 14.1 Insufficient information

Where the mechanism's behavior in the installed version cannot be established, record the gap as `OPEN QUESTION`, classify the affected claim `ASSUMPTION`, and state what evidence would settle it. Do not fill the gap with recollection or with behavior documented for a different version. The Software Architect decides whether the assessment can proceed with the gap open.

### 14.2 Conflicting documentation

Where official documentation at the release tag contradicts other official material, or contradicts observed behavior, record both with their versions and locations and escalate. Do not prefer the more convenient account. Observed behavior that contradicts documentation is recorded as an observation with its version and reproduction context, not as proof of intended capability.

### 14.3 Version drift

Where the installed version changes during or after an assessment, the earlier version stamp is retained and the affected claims are marked for re-verification. A recommendation supported by a stale stamp is not silently carried forward; it is re-opened under `WF-009` where it supported an approved decision.

### 14.4 Requests to install or configure

A request to install, enable, disable, or configure a mechanism is outside this workflow and outside agent write scope. The agent explains the boundary, records the request, and asks the human user to authorize the change as human-controlled maintenance. An accepted recommendation is not such an authorization.

### 14.5 Requests that would weaken an enforcement boundary

Where a need can only be met by weakening a rule stated in `AGENTS.md` or in an agent definition, the assessment records the conflict and escalates it. Agents do not propose a permission change as though it satisfied a policy requirement, and they do not implement the weakening.

### 14.6 Cost or dependency changes

Where a price, quota, license, or upstream service changes after an assessment, the earlier finding remains visible and the change is recorded against it. A withdrawn or unavailable option is marked as such rather than deleted.

### 14.7 Findings and blockers

A Validation Agent finding is handled under `WF-007`; it is not closed because a correction was drafted. A blocker is recorded only when the Software Architect designates it. Where a blocker depends on a human decision, the assessment pauses at that decision.

### 14.8 Open questions about this workflow

| ID | Question | Why it matters | Owner |
| --- | --- | --- | --- |
| `OQ-WF-010-01` | Where should a persisted capability assessment be recorded: as framework documentation, as a project record under `docs/04-research/`, or as an architecture decision? | The record is reused across engagements but is not project-specific, and its home determines how later changes are traced. | Software Architect |
| `OQ-WF-010-02` | Is a capability assessment required for every proposal to add a mechanism, or only where the mechanism choice is genuinely open? | A mandatory assessment for a clearly necessary configuration change would add procedure without adding information. | Software Architect |
| `OQ-WF-010-03` | What evidence standard should apply to Plugin trust, given that a Plugin is not sandboxed? | The comparison currently records the security surface but no minimum evidence threshold for accepting it. | Software Architect |

These identifiers are framework-level register identifiers for this workflow; they are not requirement identifiers and do not use the six standard prefixes.

None of the open questions listed above blocks the procedural steps of this workflow. Where an item is claimed to be blocking, that status is the Software Architect's decision and not the author's (`documentation-standards.md` §8.2).

---

## 15. Related Workflows

| Workflow | Relationship |
| --- | --- |
| [`WF-001` — Project Initiation](./project-initiation.md) | A capability need may surface during intake and be recorded in the Project Brief or the audit. |
| [`WF-002` — Planning and Scope](./planning-and-scope.md) | Feasibility and technology questions that concern mechanism choice are referred here. |
| [`WF-004` — System Design and Architecture](./system-design.md) | Architecture decisions that select a technology or integration surface may depend on this assessment. |
| [`WF-005` — Research](./research.md) | Supplies the mechanism evidence, version applicability, and source records this workflow requires. |
| [`WF-006` — Documentation Production](./documentation-production.md) | Invoked to persist an authorized assessment or recommendation record. |
| [`WF-007` — Independent Validation](./independent-validation.md) | Invoked when the Software Architect assigns review of an assessment or any deliverable that depends on it. |
| [`WF-008` — Approval and Phase Gate](./approval-and-phase-gate.md) | Governs how the decision and the installation authorization are presented and recorded. |
| [`WF-009` — Change Control](./change-control.md) | Invoked when a version change or new evidence affects an accepted mechanism choice. |

---

## 16. Change History

| Version | Date | Summary | Reason | Author | Status |
| --- | --- | --- | --- | --- | --- |
| 0.1.0 | 2026-11-10 | Initial creation of the technology capability assessment workflow, under explicit Software Architect authorization for the consolidated framework-expansion pass. | Establish a capability-first procedure for choosing among OpenCode mechanisms without installing or configuring anything. | Documentation Agent | Approved by Human user on 2026-11-10. |
