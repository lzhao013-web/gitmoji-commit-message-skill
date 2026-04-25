---
name: gitmoji-commit-message
description: Generate strict carloscuesta/gitmoji-style Git commit messages from git diff, staged changes, file lists, or change summaries. Use when the user asks for a commit message, Gitmoji commit subject, or wants changes summarized into one or more Git commit descriptions.
---

# Gitmoji Commit Message

## Workflow

Generate commit message options from the provided change context. If no diff or summary is provided, offer exactly two choices and wait for the user's selection:

1. `待提交的所有修改`: inspect all pending changes, including staged, unstaged, and untracked files where practical.
2. `已暂存的修改`: inspect staged changes only.

After the user selects one option, inspect only that source and clearly say which source was used. If the selected source has no changes, say so and do not invent a message.

Use this format:

```text
<emoji shortcode> <message>
```

Example:

```text
:bug: fix uv
```

Prefer an English commit subject unless the user explicitly asks for Chinese. Keep the subject concise, ideally under 60 characters.

## Output

Return:

```text
推荐：
<emoji shortcode> <message>

原因：
- <一句话解释>

备选：
1. <emoji shortcode> <message>
2. <emoji shortcode> <message>
```

Only include `如果应该拆分：` when the diff clearly mixes independent topics.

## Rules

- Use exactly one Gitmoji shortcode per commit message.
- Always use the shortcode form, such as `:bug:` or `:sparkles:`, never the emoji glyph.
- Do not include a parenthesized scope or colon separator after the shortcode.
- Choose the Gitmoji shortcode that best represents the dominant intent.
- Do not invent changes absent from the diff.
- Avoid vague subjects such as `update stuff` or `fix bug`.
- Use an imperative phrase or concise verb phrase.
- Mention the affected area in the message when it clarifies the change, such as `api`, `auth`, `ui`, `db`, `config`, `deps`, `tests`, `docs`, `ci`, `llm`, or `tool-call`.
- If the change introduces an incompatible API, protocol, config, schema, or behavior change, prefer `:boom:`.
- If the diff clearly contains multiple independent themes, recommend splitting into separate commits.

## Gitmoji Selection

Use these common shortcodes:

- `:sparkles:` for new features, capabilities, interfaces, pages, commands, or parameters.
- `:bug:` for clear bug fixes, wrong behavior, exceptions, or logic errors.
- `:ambulance:` for urgent production hotfixes.
- `:boom:` for breaking changes.
- `:recycle:` for refactors without external behavior change.
- `:zap:` for performance improvements.
- `:memo:` for documentation.
- `:bulb:` for source comments.
- `:white_check_mark:` for tests.
- `:wrench:` for configuration.
- `:hammer:` for development or build scripts.
- `:construction_worker:` for CI/CD and automation.
- `:green_heart:` for fixing CI builds.
- `:arrow_up:` for dependency upgrades.
- `:arrow_down:` for dependency downgrades.
- `:heavy_plus_sign:` for adding dependencies.
- `:heavy_minus_sign:` for removing dependencies.
- `:lock:` for security or privacy fixes.
- `:closed_lock_with_key:` for secrets, keys, or credentials.
- `:art:` for structure, formatting, or readability improvements.
- `:rotating_light:` for lint, warning, or static-check fixes.
- `:fire:` for deleting code or files.
- `:coffin:` for removing dead code.
- `:truck:` for moving or renaming files, paths, resources, or routes.
- `:twisted_rightwards_arrows:` for merges.
- `:rewind:` for reverts.
- `:package:` for generated packages or compiled artifacts.
- `:label:` for type definitions.
- `:card_file_box:` for database changes.
- `:seedling:` for seed files.
- `:triangular_flag_on_post:` for feature flags.
- `:goal_net:` for error handling, fallbacks, or error boundaries.
- `:adhesive_bandage:` for small non-critical fixes.
- `:passport_control:` for authorization, roles, or access control.
- `:thread:` for concurrency, threading, async races, or locks.
- `:safety_vest:` for validation, input checks, or schema validation.
- `:necktie:` for business logic.
- `:stethoscope:` for health checks.
- `:bricks:` for infrastructure.
- `:technologist:` for developer experience.
- `:speech_balloon:` for copy, strings, prompts, or localization text.
- `:globe_with_meridians:` for internationalization or localization.
- `:wheelchair:` for accessibility.
- `:lipstick:` for UI or visual styling.
- `:iphone:` for responsive or mobile adaptation.
- `:camera_flash:` for snapshots.
- `:test_tube:` for adding a currently failing test.
- `:monocle_face:` for data exploration or analysis code.
- `:alembic:` for experiments.
- `:clown_face:` for mocks, stubs, or fakes.
- `:see_no_evil:` for `.gitignore`.
- `:page_facing_up:` for licenses.
- `:bookmark:` for release versions.
- `:rocket:` for deployment.
- `:wheel_of_dharma:` for Kubernetes.
- `:whale:` for Docker.

## Splitting Guidance

Recommend splitting when the diff includes unrelated domains, such as feature code plus dependency upgrades, docs-only changes plus behavior changes, or unrelated bug fixes. For each suggested split, provide one Gitmoji commit subject.
