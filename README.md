# claude-projects

## Claude Code skills

`.claude/skills/` and `.claude/agents/` hold the Caveman skill set by Julius Brussee,
copied unchanged from https://github.com/JuliusBrussee/caveman (commit `2e068f735253cce28256744804785f01887d9646`).
Licensed Apache-2.0; see `third_party/caveman/`.

| Skill / agent | Use |
|---|---|
| `caveman` | `/caveman`: terse replies, all technical facts kept. Off with "stop caveman". |
| `ultracave` | `/ultracave` or `/caveman ultra`: maximum compression. |
| `megacave` | `/megacave`: Classical Chinese register. |
| `caveman-compress` | `/caveman-compress <file>`: compress CLAUDE.md or other memory files. Sends the file's text to a model provider. |
| `cavecrew` + agents | Delegates search, small edits and reviews to subagents that answer compressed. |

Not included: `caveman-stats`, the hooks and the status line. Those need the full plugin:
`claude plugin marketplace add JuliusBrussee/caveman && claude plugin install caveman@caveman`
