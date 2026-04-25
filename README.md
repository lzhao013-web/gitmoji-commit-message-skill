# Gitmoji Commit Message Skill

A Codex skill that generates strict `carloscuesta/gitmoji`-style commit subjects from pending changes, staged diffs, file lists, or change summaries.

This repository references and follows conventions from [carloscuesta/gitmoji](https://github.com/carloscuesta/gitmoji).

## What it does

- Produces concise commit subjects in this format: `<emoji shortcode> <message>` (for example: `:bug: fix auth token parsing`).
- Enforces a single Gitmoji shortcode and avoids vague messages.
- Chooses the best shortcode based on dominant intent (feature, bugfix, docs, refactor, etc.).
- Can suggest splitting commits when one diff mixes unrelated topics.

## How to use

### 1) Add the skill to Codex

Place this repository (or the `gitmoji-commit-message` folder) in your Codex skills directory so Codex can load `SKILL.md`.

### 2) Invoke the skill in chat

Ask Codex to use the skill by name, for example:
- `Use $gitmoji-commit-message for my current diff.`
- `Generate a gitmoji commit message from staged changes.`

### 3) Follow the selection workflow

If no diff or summary is provided, the skill offers two choices:
1. all pending changes
2. staged changes only

Then it generates recommended and alternative commit subjects.

## Compatibility

This skill is written in a generic `SKILL.md` format and can often be used by other code agents that support compatible skill directories (for example, Claude Code/OpenCode style skill loading).

## Output format

The skill returns:

```text
Recommended:
<emoji shortcode> <message>

Reason:
- <one-line explanation>

Alternatives:
1. <emoji shortcode> <message>
2. <emoji shortcode> <message>
```

## Repository structure

- `gitmoji-commit-message/SKILL.md`: core behavior, workflow, and Gitmoji mapping.
- `gitmoji-commit-message/agents/openai.yaml`: OpenAI/Codex interface metadata.
- `LICENSE`: project license.

## Notes

- Default style prefers English commit subjects unless the user explicitly requests Chinese.
- The skill uses Gitmoji shortcodes like `:sparkles:` and `:memo:` (not emoji glyphs).
