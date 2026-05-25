# Using this repo with Cursor

This repository includes Cursor project rules for the Karpathy-inspired 12-rule behavior contract.

## In this repository

1. Open the folder in Cursor.
2. The English rule [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc) is committed with `alwaysApply: true`.
3. Cursor should apply the English 12-rule contract automatically.
4. The Chinese reference rule [`.cursor/rules/karpathy-guidelines.zh.mdc`](.cursor/rules/karpathy-guidelines.zh.mdc) is committed with `alwaysApply: false` to avoid duplicate instruction pressure.

## Use the same guidelines in another project

**Cursor, English primary:** copy `.cursor/rules/karpathy-guidelines.mdc` into that project's `.cursor/rules/` directory.

**Cursor, Chinese reference:** copy `.cursor/rules/karpathy-guidelines.zh.mdc` if you want a Chinese version for reading or manual activation.

**Other tools:** if a stack only supports a root instruction file, copy [`CLAUDE.md`](CLAUDE.md). For Chinese documentation, copy [`CLAUDE.zh.md`](CLAUDE.zh.md).

## Optional: personal Agent Skills

English skill: [`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md)

Chinese skill: [`skills/karpathy-guidelines-zh/SKILL.md`](skills/karpathy-guidelines-zh/SKILL.md)

You can copy either skill into your personal skills directory.

## Claude Code vs Cursor

- **Claude Code:** install via the plugin marketplace, or copy `CLAUDE.md` into a project.
- **Cursor:** use the committed `.cursor/rules/` files. Cursor does not read `.claude-plugin/` or `CLAUDE.md` by default.

## For contributors

When changing the 12 rules, keep these files aligned:

- [`CLAUDE.md`](CLAUDE.md)
- [`CLAUDE.zh.md`](CLAUDE.zh.md)
- [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc)
- [`.cursor/rules/karpathy-guidelines.zh.mdc`](.cursor/rules/karpathy-guidelines.zh.mdc)
- [`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md)
- [`skills/karpathy-guidelines-zh/SKILL.md`](skills/karpathy-guidelines-zh/SKILL.md)
