# CLAUDE.md — Digital All Stars

This file is project memory for Claude Code. Read it before doing work.

## What this is
Digital All Stars is a digital business card platform for automotive dealerships
(and later, other businesses). Each salesperson gets a card at a URL like:

    digitalallstars.com/{Dealership}/{First-Last}
    e.g. digitalallstars.com/ToyotaPlaza/Mike-Hochwald

A card lets a customer: save the rep to their phone (vCard), call/text/email,
and jump to the rep's inventory + review/social links. Cards are reached via a
QR code printed on desk placards and showroom posters.

## Who's building it
Mike Hochwald — automotive sales at Toyota Plaza. Non-engineer / vibe-coding via
Claude Code. Owns GitHub, Vercel, and Supabase accounts. Stripe to be added later.
Explain reasoning in plain language; don't assume deep coding knowledge.

## Business model (future, not Phase 1)
- Per-seat or tiered MONTHLY subscription billed to the dealership.
- Add-on: physical print products (desk placards, showroom posters) with QR codes.
- Roles: Dealership ADMIN (manages the team + billing) and USER (edits own card only).

## IMPORTANT constraints / sensitivities
- Trademark caution: Toyota / dealership names + logos are NOT ours. On the
  dealership-branded path we use them only with dealer permission. On Mike's
  personal fallback path (mike-hochwald-toyota-plaza.com) we avoid their logos
  and trademarked styling — just Mike's name + a neutral "I sell at Toyota Plaza".
- Customer leads route TO the dealership's inventory, never away from it. This is
  a retention/rapport tool that feeds the dealer, framed as a benefit to them.
- Don't build features that capture/resell dealer customer data.

## BUILD IN PHASES — do not skip ahead
### Phase 1 — Single static card (NO database)
- One self-contained card per folder. Data lives in a config block, template is
  reusable. Deploy to Vercel as a static site. Goal: prove value + get manager buy-in.
- This already exists as a working HTML file (see /reference/card-prototype.html).

### Phase 2 — Multi-card + auth + admin (ADD Supabase)
- Supabase auth. Tables: dealerships, users (FK dealership, role admin|user), cards.
- Dashboard: admin adds/removes team members; each user edits only their own card.
- Cards render from DB instead of the hand-edited config block. NO billing yet.

### Phase 3 — Monetize (ADD Stripe)
- Stripe subscriptions (per-seat / tiered) billed to dealership admin.
- Print product line: Stripe one-time checkout + orders table + a print-fulfillment
  partner (don't handle physical logistics in-house).

## Stack
- Front-end + hosting: Next.js on Vercel (auto-deploy from GitHub main).
- DB/auth (Phase 2+): Supabase.
- Payments (Phase 3): Stripe.
- Keep Supabase/Stripe MCP connectors OFF until the phase that needs them, to
  avoid bloating the context window. GitHub + Vercel are enough for Phase 1.

## Conventions
- URL/folder structure mirrors the card path: /{Dealership}/{First-Last}.
- Separate CONTENT from TEMPLATE everywhere — adding a person should never mean
  editing layout code.
- Commit in small, described steps. Mike should be able to roll back easily.
