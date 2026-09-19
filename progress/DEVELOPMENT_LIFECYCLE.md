# Application Development Progress Lifecycle

This guide defines how the `progress/` folder explains Toolboxed development to people and AI. It separates what the project intends to do, how the work is described, what has actually happened, what has been reviewed, and what has been accepted.

The progress folder is the authoritative project narrative. It must allow a reader to answer:

1. What are we building?
2. Why are we building it?
3. How will we build it?
4. What has actually been done?
5. What evidence exists?
6. What remains unreviewed, unvalidated, or unaccepted?
7. What should happen next?

## Lifecycle

```text
Planned → Documented → Executed → Reviewed → Accepted
              ↑            ↓          ↓
              └──── corrected, blocked, deferred, or continued
```

The stages are related but are not interchangeable. A later stage requires evidence from the earlier stage; producing a document does not prove that implementation or validation occurred.

| Stage | Meaning | Required record | What it does not prove |
|---|---|---|---|
| **Planned** | Intended scope and outcome are authorised or proposed | Plan item, objective, scope, dependencies, risks, outputs, acceptance criteria, and next action in `PLAN_LOG.md` | That work started or produced repository changes |
| **Documented** | The intended approach, design, contracts, assumptions, or evaluation method has been written down | Design document, ADR, fixture brief, contract, checklist, or other linked planning evidence | That the design works, was implemented, or was approved |
| **Executed** | The approved increment was carried out within its bounded scope | Worklog entry, affected paths, implementation details, validation performed, limitations, and commit/PR evidence in `CODING_WORKLOG.md` | That the result is correct, sufficient, or accepted |
| **Reviewed** | Required people or defined review roles inspected the result and recorded decisions | Reviewers, date, evidence inspected, comments, amendments, decisions, owners, and unresolved items | That all technical or product acceptance criteria passed |
| **Accepted** | Scope-specific acceptance criteria are met, evidence is linked, and remaining limitations are resolved or explicitly accepted | Acceptance decision, validation evidence, review record, status change, and next authorised scope | That the entire product or every future use case is complete |

## How to apply the lifecycle

### 1. Planned

Before consequential work begins, record the intended work in `PLAN_LOG.md`. Include:

- Plan ID and status.
- Objective and reason.
- Scope and explicit exclusions.
- Owner and required roles.
- Dependencies and prerequisites.
- Data, fixtures, tools, or evidence needed.
- Expected outputs.
- Risks, assumptions, open questions, and blockers.
- Increment exit condition and final acceptance criteria.
- Next responsible action.

A plan is the authorisation and explanation of intended work. It is not an execution record.

### 2. Documented

Document the design or evaluation method before building when the work changes architecture, data, public contracts, domain boundaries, security, or operational behaviour. Record:

- Options and alternatives.
- Decisions and rationale.
- Interfaces and contracts.
- Assumptions and unresolved questions.
- Evaluation fixture and workload definitions.
- Expected evidence and pass/fail or observation criteria.
- Review responsibilities.

For example, a fixture brief documents what must be evaluated. It does not mean that the fixture dataset exists or that measurements have been run.

### 3. Executed

Execute only the approved scope. Record actual work in `CODING_WORKLOG.md`, including:

- Exact increment and authorising plan ID.
- Files created, updated, deleted, or unchanged.
- Decisions made during execution.
- Validation actually performed.
- Failed or unperformed checks.
- Limitations, blockers, and deviations.
- Commit, pull request, test, or other exact evidence.

A created document is evidence that documentation was executed. It is not evidence that the documented design was implemented or validated.

### 4. Reviewed

Review is a distinct activity. Record:

- Required and actual reviewers.
- Date and scope of review.
- Documents, code, tests, fixtures, or measurements inspected.
- Approval, amendment, rejection, or request for correction.
- Open questions and named owners.
- Unblock conditions and next review point.

If reviewers have not recorded a decision, the work remains unreviewed even when the documentation is detailed.

### 5. Accepted

Move an increment or plan item to accepted/completed only when:

- Its scope was executed or formally changed.
- Its stated outputs exist.
- Required validation was performed and recorded.
- Required review occurred.
- Failures and limitations are resolved or explicitly accepted.
- Evidence is linked from the plan and worklog.
- No known blocker prevents the stated outcome.

Acceptance is always scoped. Accepting a fixture definition accepts the definition, not the architecture choices that the fixture will later evaluate.

## Evidence examples

| Work state | Evidence that is sufficient | Evidence that is insufficient by itself |
|---|---|---|
| Architecture planned | PL item with alternatives, dependencies, risks, and acceptance criteria | A sentence saying a framework is preferred |
| Architecture documented | ADR or decision matrix with rationale and evaluation method | A provisional recommendation with no assumptions or criteria |
| Fixture defined | Versioned fixture brief with workloads and reproducibility requirements | A list of desired model elements without workload definitions |
| Dataset created | Versioned model/file, provenance, counts, license, and integrity record | A fixture brief or filename with no inspectable dataset |
| Evaluation executed | Reproducible environment, commands/tools, results, failures, and limitations | Claiming that a benchmark was run without results |
| Review completed | Named reviewers, date, inspected evidence, decisions, and amendments | “Reviewed” with no review record |
| Architecture accepted | Evidence-backed ADR updates, review approval, and linked validation | A successful documentation commit alone |

## Rules for readers and AI

- Treat `PLAN_LOG.md` as intended scope and authorisation, not proof of implementation.
- Treat `CODING_WORKLOG.md` as the record of actual repository work, not proof of product acceptance.
- Treat documents labelled provisional, proposed, assumption, open, or pending as unresolved.
- Do not infer dataset creation, measurements, tests, approvals, or acceptance from a plan or design document.
- Do not infer implementation from a commit that only changes documentation.
- Report missing evidence explicitly.
- Preserve partial, failed, blocked, deferred, corrected, and rejected outcomes.
- Link every accepted increment to its plan, worklog, exact evidence, and review record.
- Keep parent plans active until their own acceptance criteria are met, even when individual increments are accepted.

## PL-0003 example

For the architecture evaluation fixture:

1. **Planned:** PL-0003 defines the fixture increment and its exit criteria.
2. **Documented:** `docs/architecture/ARCHITECTURE_EVALUATION_FIXTURE.md` defines the model, workloads, evidence, and review checklist.
3. **Executed:** WL-0013 records creation of that fixture brief and its commit.
4. **Pending execution:** The actual dataset and measured evaluations do not yet exist.
5. **Pending review:** Product, technical, BIM/domain, security, and QA decisions are not recorded.
6. **Not accepted:** PL-0003 remains Active / Partial execution because architecture acceptance requires review and evidence from the dataset and evaluations.

This is correct progress, not a contradiction. The fixture-definition increment can be complete while the parent architecture plan remains incomplete.

## Record relationship

```text
PLAN_LOG.md
  → defines intended scope and acceptance
CODING_WORKLOG.md
  → records actual bounded work
Repository evidence
  → commits, files, tests, fixtures, measurements, and review records
Status
  → communicates the current lifecycle state honestly
```

When records disagree, preserve the more cautious status and record the missing evidence or correction rather than silently upgrading the work.
