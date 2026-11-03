# Project context

Building websites for product- or service-based e-commerce, plus portfolio sites. It is not yet decided whether the sites are for the owner's own businesses or for clients, and the stack is not final. Ask before assuming either.

## Working defaults (change these once decided)

- Stack: Next.js, Tailwind with shadcn/ui, Postgres, Stripe.
- Payments: use Stripe Checkout. Do not build custom card handling.
- Data: put a `site_id` column on every table from the start, even with one site, so a second business can be added later without a rewrite. Do not build full multi-tenancy (per-plan feature switches, tenant admin) until a second customer exists.
- Build one real shop with a portfolio section before generalizing into a reusable platform.

## Using the skills in .claude/skills

- `ui-ux-pro-max`: run `python3 .claude/skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system`. Check that the top result fits the product before using it. Its marketplace and multi-tenant results are weak; do not rely on them.
- `taste-skill` sets the visual direction (look, type, palette, layout, motion). `ui-ux-pro-max` supplies UX and accessibility rules and stack guidance. When they disagree: taste-skill decides the visual style, `ui-ux-pro-max` decides usability and accessibility (contrast, touch targets, keyboard, focus, reduced motion). Do not run both design searches for the same decision; pick one source per question.
- `ui-styling` for components, `design-system` for tokens, `brand` for voice and identity.
- `caveman`, `ultracave` and `megacave` only run when the user asks. Do not apply them to code, commits or docs.
