# SOP 8: Buyer & Money Management

## Safety rules (non-negotiable)
- **Honey never messages a buyer or meets one alone.** Every handoff has Marie present.
- Meet in a public place or a police station "safe exchange zone." For furniture, porch pickup only, with Marie home, buyer never comes inside.
- **Get paid before the item leaves** — cash or Venmo/Zelle confirmed received, not "sent." Never accept checks, overpayment, or "send extra and give the rest to my mover" (classic scam pattern).
- Don't share a phone number or home address until a pickup time is actually confirmed.
- Tell someone (each other, minimum) the pickup time and buyer's name/profile before it happens.

## Message scripts
**First reply to an inquiry:**
> "Hi! Yes, it's still available. It's [condition note]. Would [day/time] work for pickup? It's $[price], cash or Venmo at pickup."

**Lowball offer:**
> "Thanks for the offer! I can do $[counter], firm — it's priced fairly against what similar ones are selling for."

**No-show:**
> "Hi, just checking — are we still on for [time] today? If not, no worries, just let me know and I'll open it back up."

**Marking sold elsewhere / withdrawing interest:**
> "Thanks for your interest! This one just sold, but I'll keep you in mind if I list something similar."

## After the sale
1. Mark the item **Sold** in the relevant tracker (`tracker/sales.csv` for ours, `tracker/marketplace-items.csv` for a client's) same day, with sold price and buyer payment method.
2. **Client payout (Sell-It-For-You add-on):** client gets 70% of the sale price, paid out via Venmo/check within **5 business days** of the sale. Log the payout date in `tracker/marketplace-items.csv`.
3. Roll unsold, stale listings into the weekly price-drop review (see `sop/07-marketplace-pipeline.md`).
