# skills

Jean Toledo's public collection of [Agent Skills](https://skills.sh) — reusable, opinionated capabilities for AI agents (Cursor, Claude Code, Codex, and any other agent that supports the Agent Skills spec).


## Skills

| Skill | Description |
|-------|-------------|
| [`html-artifact`](skills/html-artifact) | When asked, turn an agent or LLM chat response into a self-contained HTML artifact (report, dashboard, mockup, one-pager, summary) styled with the Birchline design system. Files open standalone in any browser, with optional interactivity (filters, tabs, toggles, charts). |

## Install

These skills are designed to be installed with [`skills.sh`](https://skills.sh):

```bash
npx skills add jeantoledo/skills
```

`skills.sh` auto-detects which agents you have installed and offers to install each skill to the appropriate location. Useful flags:

```bash
# List all available skills
npx skills add jeantoledo/skills --list

# Install one or more specific skill
npx skills add jeantoledo/skills --skill html-artifact

# Install to a specific agent only
npx skills add jeantoledo/skills -a claude-code -y

# Install globally (available in every project, not just the current workspace)
npx skills add jeantoledo/skills -g

# Install to every detected agent without prompting
npx skills add jeantoledo/skills --all
```

Restart your editor after installing — agents discover skills on startup.

## Repository layout

```
skills/
├── README.md
└── skills/
    └── <skill-name>/
        ├── SKILL.md       # Required. Skill entrypoint with frontmatter.
        ├── references/    # Optional. Heavy docs loaded on demand.
        ├── scripts/       # Optional. Executable helpers (bash/python/etc).
        └── assets/        # Optional. Static files referenced by the skill.
```

One directory per skill. The directory name must match the `name:` field in its `SKILL.md` frontmatter.

## Conventions

- **One skill, one job.** If two operating modes don't share context or rules, split them into separate skills.
- **The `description` field is a contract with the agent.** Write it so the agent can pattern-match user intent to the skill. List concrete triggers ("Use when: …").
- **Heavy references go in `references/`.** Keep `SKILL.md` under ~250 lines when possible; everything else gets loaded on demand from the body.
- **Mark freshness explicitly.** Any skill grounded in time-sensitive research declares a `guide-trust-window` in `metadata` and re-research triggers in the body.
- **No raw secrets.** Treat `SKILL.md` files as code even though the repo is private: no API keys, no PII beyond what's already public about Jean.

## License

MIT — see [`LICENSE`](LICENSE).
