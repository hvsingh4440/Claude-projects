---
name: build-business-website
description: Use when the user describes a business or business model and asks to create, build, plan or scope its website or platform (shop, service business, subscription product, portfolio, marketplace, booking, sales site). Turns the business model into a complete spec covering the public site, the customer side, the backend and an admin panel with every control needed to run the business, then builds it in a safe order and tests it in a real browser. Do not use for small edits to an existing site.
---

# Build a business website end to end

The user gives a business model. Your job is to think through everything needed to run that business online, not only the pages. A site that takes orders but cannot refund, pause a subscription, hide a product or show yesterday's revenue is not finished.

## 1. Intake (short)

From the business model, work out and write down:

- What is sold (products, services, subscriptions, listings, bookings, digital goods) and to whom.
- How money moves: one-time, recurring, deposits, commission, payouts to third parties, tax, currencies.
- Who operates the business: owner only, staff with limited roles, sellers or vendors, clients.
- How it is fulfilled: shipping, delivery, appointments, digital access, manual work.
- Legal and regional constraints: tax or VAT, consumer-rights rules, data-protection rules, age limits, licences.

Ask the user only questions whose answer changes the architecture (at most five, asked together). For everything else, choose a sensible default and list it as an assumption. Never ask about something you can default.

## 2. Write the spec before any code

Create `docs/spec.md` with these sections, in this order. Skip a section only if the business model makes it irrelevant, and say why.

1. Business summary and assumptions.
2. Roles and permissions: a table of every role against every action. Start from: visitor, customer, staff, admin, owner. Add seller or client roles only if the model needs them.
3. Public site: every page, its purpose, its main action, and SEO basics (titles, descriptions, structured data, sitemap).
4. Customer side: sign-up and login, account area, every flow a customer can start (browse, buy, subscribe, book, cancel, refund request, download invoice), and every email or message they receive.
5. Admin panel: every control needed to run the business. Use `admin-controls-checklist.md` in this folder and include each item that applies. For each control state who can use it and whether it is logged.
6. Data model: tables, key fields, relationships. Every table carries `site_id`. Money is stored as integer minor units with a currency code.
7. Payments and money flows: what Stripe handles, which webhooks are consumed, how failures, retries, refunds and disputes are handled.
8. Notifications: transactional emails, admin alerts, templates.
9. Security and compliance: auth method, 2FA for staff, rate limits, input validation, audit log, backups, privacy and legal pages.
10. Non-functional: performance budget, accessibility target (WCAG 2.2 AA), supported devices, analytics.
11. Build phases and what each delivers.
12. Open decisions for the user.

Present a short summary of the assumptions and open decisions in chat and stop for approval. Changing the spec is cheap; changing a built system is not. If the user has already said to proceed without checking, continue.

## 3. Build order

1. Foundation: project setup, database, authentication, roles and permission checks, admin shell, audit log, environment and secrets handling.
2. Core money flow: the one path that earns revenue (checkout, subscription, booking). Use Stripe Checkout and signed webhooks. Make webhook handling idempotent.
3. Admin controls for that flow first (orders or subscriptions, refunds, customers), then the rest of the admin checklist.
4. Customer account area.
5. Public marketing and portfolio pages.
6. Polish, SEO, performance, accessibility.
7. Test, then launch checklist.

Never build a customer action without its admin counterpart. Every state change that affects money, access or data writes an audit log entry.

## 4. Which skill to use when

- Visual direction for public pages and app screens: `taste-skill`.
- Usability, accessibility and stack guidance: `ui-ux-pro-max` (run its search for the actual product, and check the top result fits before using it).
- Components and theming: `ui-styling`. Tokens: `design-system`. Voice and identity: `brand`.
- Payments and subscriptions: the Stripe plugin, if the user has installed it.
- Browser testing: the Playwright plugin, if installed.
- Accessibility review and interface copy: the Design plugin, if installed.

If a plugin is not installed, say so once and continue with the skills that are.

## 5. Verification before calling anything done

- Run the real critical paths in a browser, not only unit tests: sign up, log in, buy or subscribe, receive the confirmation, then in the admin panel find that order, refund it, and see the customer's state change.
- Use Stripe test mode and test cards. Replay a webhook twice and confirm nothing is duplicated.
- Check each role: a customer must not reach admin routes or another customer's data; staff must not exceed their permissions.
- Check mobile width, keyboard-only use, and colour contrast on the main pages.
- Report what was tested and what was not. Do not claim it works because it compiles.

## 6. Launch checklist

Production environment variables and secrets set; Stripe live mode keys and webhook endpoint configured; domain, HTTPS and email sending (SPF, DKIM) set up; backups on and a restore tested; error monitoring on; admin accounts have 2FA; default and test accounts removed; privacy policy, terms and refund policy published; sitemap and robots in place; analytics consent handled.
