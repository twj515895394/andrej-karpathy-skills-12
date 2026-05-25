![Karpathy Skills 12 overview](./assets/karpathy-skills-12-overview.svg)

# Karpathy-Inspired Claude Code Guidelines — 12 Rules

English | [简体中文](./README.zh.md)

A compact, English-first behavior contract for Claude Code, Cursor, and reusable agent skills. It starts from Andrej Karpathy's observations about LLM coding failures and extends the original 4-rule template into a 12-rule version for modern multi-step agent workflows.

The goal is not to make the model "careful" in a vague way. The goal is to turn recurring failure modes into short, executable rules that can live in `CLAUDE.md`, Cursor rules, and reusable skills.

## What this project solves

The original template focused on four common coding failures:

1. silent wrong assumptions,
2. overcomplicated code and APIs,
3. unnecessary side-effect edits,
4. weak or missing success criteria.

This project keeps those four rules and adds eight rules for newer agent-style workflows: deterministic logic boundaries, token budgets, conflicting codebase patterns, read-before-write discipline, meaningful tests, checkpoints, convention matching, and loud failure.

## What is included

| File | Purpose |
| --- | --- |
| [`CLAUDE.md`](./CLAUDE.md) | English primary 12-rule behavior contract for Claude Code |
| [`CLAUDE.zh.md`](./CLAUDE.zh.md) | Simplified Chinese version of the same 12 rules |
| [`.cursor/rules/karpathy-guidelines.mdc`](./.cursor/rules/karpathy-guidelines.mdc) | English Cursor project rule, enabled by default |
| [`.cursor/rules/karpathy-guidelines.zh.mdc`](./.cursor/rules/karpathy-guidelines.zh.mdc) | Chinese Cursor reference rule, not enabled by default |
| [`skills/karpathy-guidelines/SKILL.md`](./skills/karpathy-guidelines/SKILL.md) | English reusable skill |
| [`skills/karpathy-guidelines-zh/SKILL.md`](./skills/karpathy-guidelines-zh/SKILL.md) | Chinese reusable skill |

## The 12 rules

| # | Rule | Prevents |
| --- | --- | --- |
| 1 | Think Before Coding | silent assumptions, hidden confusion |
| 2 | Simplicity First | overengineering, speculative features |
| 3 | Surgical Changes | unrelated edits, accidental refactors |
| 4 | Goal-Driven Execution | vague work, unverifiable completion |
| 5 | Use the Model Only for Judgment Calls | unstable model-driven routing/retry logic |
| 6 | Token Budgets Are Not Advisory | runaway sessions and context drift |
| 7 | Surface Conflicts, Do Not Average Them | blended inconsistent patterns |
| 8 | Read Before You Write | duplicate code and local-context mistakes |
| 9 | Tests Verify Intent, Not Just Behavior | shallow tests that prove little |
| 10 | Checkpoint After Every Significant Step | multi-step drift and lost state |
| 11 | Match Codebase Conventions | style forks and framework inconsistency |
| 12 | Fail Loud | false success and hidden uncertainty |

## Install

### Option A: Claude Code plugin

From within Claude Code, add the marketplace and install the plugin:

```bash
/plugin marketplace add twj515895394/andrej-karpathy-skills-12
/plugin install andrej-karpathy-skills-12@karpathy-skills-12
```

This exposes the guideline skill across projects.

### Option B: Per-project `CLAUDE.md`

New project:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/twj515895394/andrej-karpathy-skills-12/main/CLAUDE.md
```

Existing project:

```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/twj515895394/andrej-karpathy-skills-12/main/CLAUDE.md >> CLAUDE.md
```

Chinese version:

```bash
curl -o CLAUDE.zh.md https://raw.githubusercontent.com/twj515895394/andrej-karpathy-skills-12/main/CLAUDE.zh.md
```

## Using with Cursor

This repository includes a committed Cursor project rule at [`.cursor/rules/karpathy-guidelines.mdc`](./.cursor/rules/karpathy-guidelines.mdc). It has `alwaysApply: true`, so Cursor can apply the English 12-rule contract automatically when the project is opened.

A Chinese reference rule is also available at [`.cursor/rules/karpathy-guidelines.zh.mdc`](./.cursor/rules/karpathy-guidelines.zh.mdc). It is intentionally not enabled by default to avoid duplicate instruction pressure.

See [`CURSOR.md`](./CURSOR.md) for more details.

## Customization guidance

Keep the base rules short. Add project-specific instructions after the 12 rules, such as:

```markdown
## Project-Specific Guidelines

- Use TypeScript strict mode.
- All API endpoints must have tests.
- Follow the existing error handling pattern in `src/utils/errors.ts`.
```

A tuned 6-rule file that matches your real failure modes is better than a long instruction file full of unused preferences.

## Key idea

`CLAUDE.md` should not be a preference dump. Treat it as a behavior contract: each rule should close a failure mode you have actually seen.

## License

MIT
