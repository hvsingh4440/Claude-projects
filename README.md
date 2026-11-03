# claude-projects

Claude Code skills tuned for building and developing projects. Everything here loads
automatically in any Claude Code session opened on this repo.

## Skill set

| Skill | Trigger | Job |
|---|---|---|
| `ui-ux-pro-max` | auto on UI work | Design decisions: style, palette, fonts, UX/accessibility rules, per-stack guidance (22 stacks). Local search, no network. |
| `ui-styling` | auto on UI work | Implementation: shadcn/ui + Tailwind components, theming, dark mode. |
| `build-business-website` | auto when given a business model | Turns a business model into a spec (public site, customer side, backend, admin panel with full controls), builds in a safe order, tests in a browser. |
| `taste-skill` | auto on any page or screen build | Art direction: researched visual directions, strict no-generic-AI style, lint and real-browser inspection. Needs Node 22+ and Chrome for its scripts. |
| `brand` | auto on brand work | Brand voice, messaging, visual identity, consistency checks. Restored for shop and portfolio sites. |
| `design-system` | auto on token work | Token architecture (primitive → semantic → component), component specs, CSS variables. |
| `caveman` | `/caveman` | Short replies, every technical fact kept. Off: "stop caveman". |
| `ultracave` | `/ultracave` | Maximum compression. Manual only. |
| `megacave` | `/megacave` | Classical Chinese register. Manual only; kept because `/caveman wenyan` points to it. |
| `caveman-compress` | `/caveman-compress <file>` | Shrinks CLAUDE.md and other memory files to cut input tokens every session. Sends the file to a model provider. |
| `cavecrew` + 3 agents | auto on delegation | Investigator / builder / reviewer subagents that return compressed results (Haiku model). |

## Deliberately excluded

- `design`, `banner-design`, `slides`: asset generation and decks, not development. `design` also needs a paid image API key. Restore from the source repo if needed.
- `caveman-stats`, Caveman hooks and status line: need the full plugin:
  `claude plugin marketplace add JuliusBrussee/caveman && claude plugin install caveman@caveman`

## Sources and local changes

- Taste Skill: https://github.com/Leonxlnx/taste-skill @ `12af471f627f866411b4bd785b19646d3672784c` (MIT, `third_party/taste-skill/`). Unchanged except `evals/` removed.
- Caveman: https://github.com/JuliusBrussee/caveman @ `2e068f735253cce28256744804785f01887d9646` (Apache-2.0, `third_party/caveman/`). Unchanged.
- UI/UX Pro Max: https://github.com/nextlevelbuilder/ui-ux-pro-max-skill @ `713eef51b04efc98d6fa565323b495f7c9c89fd4` (MIT, `third_party/ui-ux-pro-max/`). Changes:
  - `ui-ux-pro-max/SKILL.md`: script path falls back to the repo root when `CLAUDE_PLUGIN_ROOT` is unset (project install).
  - `ui-ux-pro-max/scripts/tests/` removed (upstream test suite, not needed to use the skill).

Search command: `python3 .claude/skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system`
