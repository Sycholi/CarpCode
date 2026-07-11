---
name: carpcode
description: "Apply scope control, surgical edits, and task-proportionate verification to general software-engineering work, including implementation, debugging, refactoring, code review, test writing, and build repair. Use biocarp for one-off biomedical R or Python analysis workflows; add carpcode in that domain only for package, library, pipeline-software, or repository engineering."
---

# CarpCode

## Define The Change

- Inspect the repository, applicable instructions, existing behavior, tests, and current worktree before editing.
- Translate the user goal and confirmed project constraints into concrete inputs, outputs, behavior, scope, and verification.
- Infer safe details from local context. State an assumption when it affects implementation or verification. Ask only when unresolved ambiguity would materially change behavior, risk, or scope.
- Point out a simpler valid route or a conflict with existing behavior before implementing it.

## Implement

- Make the smallest correct change that satisfies the requested behavior and established project contracts.
- Preserve existing structure, style, naming, and public interfaces unless changing them is part of the task.
- Avoid unrelated cleanup, speculative features, premature abstractions, compatibility branches, fallback behavior, and configuration outside the requirement.
- Add error handling only when required by the request, an existing contract, tests, or a concrete safety condition.
- Keep a one-use operation local. Introduce an abstraction only when repetition or the existing architecture justifies it.
- Remove imports, variables, or functions made unused by the current change. Delete files only when the task clearly authorizes it.
- Preserve unrelated user changes and original or key files.

## Verify

- Start with the narrowest check that reproduces or exercises the affected behavior, then expand verification according to change risk.
- For a bug fix, demonstrate the failure and then the corrected behavior. For a refactor, compare behavior before and after. For new behavior, test the normal case and required error cases.
- Run relevant tests, builds, linters, type checks, or direct commands. Fix failures caused by the change and rerun the affected checks.
- Distinguish failures caused by the change from pre-existing failures, flaky checks, missing credentials or data, external-service faults, and environment limits.
- Do not claim completion when available task-relevant verification has not passed. Report the exact blocker when a required check cannot run.

## Report

State the changed files, reason for each change, verification commands and results, and any unresolved blocker. Keep the report concise and factual.
