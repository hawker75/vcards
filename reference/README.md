# Digital All Stars

Digital business cards for dealership sales teams. A QR code on a desk placard or
showroom poster takes a customer to a salesperson's card, where they can save the
rep to their phone, call/text/email, and view inventory.

## Quick start (Phase 1)
1. Put `reference/card-prototype.html` content into `app/` as your first card.
2. `git init`, commit, push to a new GitHub repo.
3. Import the repo into Vercel → it deploys automatically on every push to `main`.
4. Point your domain at the Vercel project (custom domain in Vercel settings).
5. Generate a QR code to the live card URL; print it on your placard.

## Roadmap
| Phase | Goal | Adds | Needs a DB? |
|-------|------|------|-------------|
| 1 | Your own card live, prove value, get buy-in | Static card + Vercel deploy | No |
| 2 | Team cards + admin dashboard | Supabase auth, roles, dashboard | Yes |
| 3 | Make it a business | Stripe subscriptions + print products | Yes |

## Repo structure (target)
```
/app
  /[dealership]/[person]/   # dynamic card route (Phase 2) — static folders in Phase 1
  /dashboard/               # admin + user management (Phase 2)
/lib                        # supabase client, helpers (Phase 2)
/reference                  # prototypes + planning docs
CLAUDE.md                   # project memory for Claude Code
```

## Data model sketch (Phase 2)
- **dealerships**: id, name, slug, logo_url, brand_color, created_at
- **users**: id, dealership_id (FK), role ('admin' | 'user'), name, title, phone,
  email, photo_url, inventory_url, links (json), slug, active
- **cards**: optional — fold into users unless cards need to outlive a user
- (Phase 3) **subscriptions**: dealership_id, plan, seat_count, stripe_customer_id
- (Phase 3) **orders**: dealership_id, product, qty, status, stripe_payment_id

## Branding paths
- **Dealer-approved:** digitalallstars.com/ToyotaPlaza/Mike-Hochwald (uses dealer brand, with permission)
- **Personal fallback:** mike-hochwald-toyota-plaza.com (Mike's name only, no dealer logos/trademarks)
