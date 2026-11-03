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

### UI/UX Pro Max

`.claude/skills/ui-ux-pro-max/` is copied unchanged from
https://github.com/nextlevelbuilder/ui-ux-pro-max-skill (commit `713eef51b04efc98d6fa565323b495f7c9c89fd4`). MIT; see `third_party/ui-ux-pro-max/`.
It searches local design data (styles, palettes, fonts, UX rules, 22 stacks) with a Python 3 script; no network, no extra packages.
Installed as a project skill, run the script from the repo root:
`python3 .claude/skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system`
(the skill's own instructions use `${CLAUDE_PLUGIN_ROOT}`, which is only set in a plugin install).

#### Companion design skills (same source, same commit)

| Skill | Use | Needs |
|---|---|---|
| `design-system` | Tokens (primitive→semantic→component), component specs, token-driven slides | Python 3 / Node for scripts |
| `brand` | Brand voice, visual identity, messaging, consistency checks | Node for scripts |
| `design` | Logos, corporate identity, icons, banners, social images, slides | `GEMINI_API_KEY`, `ATLASCLOUD_API_KEY` or `MUAPI_API_KEY` for AI image generation (sends prompts to that provider) |
| `banner-design` | Social, ad, hero and print banners | Optional image generation via `design` |
| `slides` | HTML presentations with Chart.js | Browser |
| `ui-styling` | shadcn/ui + Tailwind components, theming, dark mode, canvas posters (bundles 5.5 MB of fonts, see its `LICENSE.txt`) | Node for `shadcn_add.py` |
