# Configuration

For basic configuration instructions, see [this documentation](https://developers.openai.com/codex/config-basic).

For advanced configuration instructions, see [this documentation](https://developers.openai.com/codex/config-advanced).

For a full configuration reference, see [this documentation](https://developers.openai.com/codex/config-reference).

## Session titles

Interactive sessions generate a short default thread name after the first user prompt. The generated name uses the same thread metadata as `/rename`, and an existing thread name prevents a generated title from being written.

Disable default title generation with:

```toml
[session_title]
enabled = false
```

Select the auxiliary model used for generated titles with:

```toml
[session_title]
model = "gpt-5.4-mini"
```

Add style rules for generated titles with:

```toml
[session_title]
additional_instructions = """
- Prefer French titles.
- Keep proper nouns unchanged.
- Prefix debugging-related titles with "Debug:".
"""
```

Additional instructions may refine wording and style, but they do not replace the built-in title prompt or its JSON output contract.

## Lifecycle hooks

Admins can set top-level `allow_managed_hooks_only = true` in
`requirements.toml` to ignore user, project, and session hook configs while
still allowing managed hooks from requirements and managed config layers. This
setting is only supported in `requirements.toml`; putting it in `config.toml`
does not enable managed-hooks-only mode.
