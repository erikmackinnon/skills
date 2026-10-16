# Skills

Agent skills by [Erik MacKinnon](https://erikmackinnon.com). They follow the [Agent Skills](https://agentskills.io) standard, so they work with Claude Code, Codex, Cursor, OpenCode, bb and other agents that support skills.

| Skill | What it does |
|---|---|
| [**Ambition**](skills/ambition/) | Before your agent starts building, it pushes you both to aim for the pinnacle. It sets the aim with a few quick calls, boldest version first, then finds the real outcome, expert methods, an outside judge, proof it's possible and a target that sounds unreasonable. Then it rewrites your task as a prompt and waits for your go-ahead. Run it with `/ambition <task>`. |

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
