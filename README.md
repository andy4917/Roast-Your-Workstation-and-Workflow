# Workstation Workflow Review

## Overview
This skill is used to inspect developer workstations, Codex operating workflows, toolchains, and recurring manual processes. It identifies repetitive manual tasks and converts evidence-backed findings into small, verifiable improvement slices wrapped in explicit risk gates and validation mechanisms.

## When to Use
Use this skill when auditing, designing, hardening, or improving:
- Developer environments, toolchains, or agent control planes
- MCP setups, shell hooks, automations, or custom runbooks
- Broad-scope workstation architectures and operational rhythms

## Core Workflow Steps
1. **Bind the Request**: Define target boundaries, permitted write surfaces, success thresholds, and final output shapes.
2. **Collect Evidence**: Review required source files, configs, and logs in a read-only manner while leaving sensitive credential boundaries closed.
3. **Classify Surfaces**: Group targets into distinct review/change surfaces and map them to risk levels (`observe`, `draft`, `controlled-change`, `high-risk-change`).
4. **Review from Evidence**: Separate facts from hypotheses, score audit axes based on hard evidence, and assign an overall verdict asset score.
5. **Normalize Findings**: Rank issues from P0 (secret leaks, data loss, false success) down to P3 (naming, convenience) with a defined confidence rating.
6. **Identify Workflow Assets**: Select recurring, stable procedures to transform into an appropriate form (`Skill`, `Custom subagent`, `Automation`, or `Extend existing`).
7. **Harden into a Bounded Goal**: Establish a `GOAL_SPEC` detailing scope boundaries, acceptance criteria, and explicit safe-stop/rollback paths.
8. **Execute and Verify**: Mutate the smallest live surface required, verify through the consuming interface, and log residual risks.

## High-Risk Gates
Do not mutate the following surfaces without explicit current user intent:
- Shell profiles, global PATHs, version managers, wrappers, or shims
- Active MCP server registrations, hook enablements, or automation schedules
- Raw secrets, tokens, credential rotation settings, or publishing permissions
- Destructive filesystem mutations, log migrations, or SQLite WAL/SHM deletions
- Host or native browser state modifications

## Required Output Contract
For design or audit tasks, the execution output must structurally adhere to the following blocks: `EVIDENCE_LEDGER`, `SURFACE_MAP`, `FINDING_MAP`, `WORKFLOW_SHORTLIST`, `GOAL_SPEC`, and `SLICE_REPORT`.
