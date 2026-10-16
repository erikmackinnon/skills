# Skills

Agent skills by [Erik MacKinnon](https://erikmackinnon.com). They follow the [Agent Skills](https://agentskills.io) standard, so they work with Claude Code, Codex, Cursor, OpenCode, bb and other agents that support skills.

| Skill | What it does |
|---|---|
| [**Ambition**](skills/ambition/) | Before your agent starts building, it helps you aim higher. It sets the aim with a few quick calls, finds the real outcome, expert methods, an outside judge and a harder target, then rewrites your task as a prompt and waits for your go-ahead. Run it with `/ambition <task>`. |

## Install

With the [skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add erikmackinnon/skills --list                  # see what's available
npx skills add erikmackinnon/skills --skill ambition -g     # install one skill globally
```

Or copy a folder from `skills/` into your agent's skills directory, such as `~/.claude/skills/` or `~/.agents/skills/`.

## Layout

```
skills/<name>/      the installable skill: SKILL.md plus references
research/<name>/    how the skill was made (not installed)
```

## License

[MIT](LICENSE)
