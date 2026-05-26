---
name: carpcode
description: "Apply CarpCode coding discipline whenever Codex performs any programming task, including software implementation, debugging, refactoring, code review, test writing, build fixes, script writing, and technical analysis: first-principles clarification, minimal scoped changes, no compatibility patches or fallback behavior beyond the user's request, surgical edits, and verified final results."
---

# CarpCode

## Overview

Use this skill for any programming task that requires strict scope control, clear assumptions, minimal implementation, and verified results.
Treat the user's stated goal as the only source of required behavior.

## Starting Rules

- Start from first principles: identify the concrete goal, inputs, outputs, constraints, and success criteria.
- State assumptions before changing code when they affect implementation or verification.
- List multiple plausible interpretations when the request is ambiguous.
- Ask the user a direct question when the goal, motivation, or required behavior is unclear.
- Point out a simpler valid method when it exists.
- Raise an objection when the requested route adds unnecessary complexity or changes business behavior.
- Use subagents only when independent parallel analysis will reduce uncertainty or time, and when the task does not require unsafe live-system changes.

## Planning Rules

- Convert the request into a verifiable target before editing.
- For multi-step tasks, write a short plan in this form:
  1. `[step]` -> Verification: `[check]`
  2. `[step]` -> Verification: `[check]`
  3. `[step]` -> Verification: `[check]`
- Prefer strong success criteria such as tests, build checks, lint checks, reproduced bugs, or exact command outputs.
- Avoid weak criteria such as only confirming that a command starts.

## Implementation Rules

- Make the smallest correct change that satisfies the user's request.
- Do not add compatibility layers, patch-style branches, fallback behavior, or degradation paths unless the user explicitly requested them.
- Do not add features, flexibility, configuration, abstractions, or error handling for cases outside the stated requirement.
- Do not introduce an abstraction for one-time code.
- If a solution becomes much longer than necessary, simplify it before presenting it.
- Keep existing style, structure, and naming where they already exist.
- Touch only files and lines required by the request.
- Do not improve adjacent code, comments, or formatting without direct need.
- Mention unrelated dead code if relevant, but do not delete it unless the user asks.
- Remove imports, variables, functions, and files that became unused because of your own change.

## Verification Rules

- Verify the full affected flow before giving the final answer.
- For a bug fix, write or run a check that reproduces the bug, then confirm the fix.
- For a refactor, confirm behavior before and after through existing tests or an equivalent direct check.
- For new behavior, verify normal input and the invalid input covered by the requirement.
- If verification fails, fix the issue and run verification again.
- Do not present code or analysis as final until the available verification passes.
- If a required verification cannot run because of missing credentials, missing data, or environment limits, state the exact blocker and the checks that were completed.

## Output Rules

- Report only useful facts: changed files, reason for the change, and verification results.
- Avoid presenting proposals as a final answer when implementation was requested.
- Do not describe unfinished work as complete.
- Do not provide intermediate or downgraded deliverables as the final result.
- Keep wording concise, direct, and technically precise.
