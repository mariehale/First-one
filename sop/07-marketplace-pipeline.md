# SOP 7: Marketplace Pipeline (Sell pile → cash)

This runs on **every** Sell pile — our own house inventory or a client's Sell-It-For-You items. The only difference is which tracker row it lands in (see step 6).

## 1. Photograph the pile
Extra checklist beyond the general protocol in `sop/02-photo-capture-protocol.md`:
- [ ] 4–8 photos per item: front, back, any brand tag/label, close-up on flaws, one shot with a hand or common object for scale
- [ ] Daylight, near a window, plain background (a wall or the floor, not a cluttered table)
- [ ] File naming: `Item_ShortName_01.jpg`, `_02.jpg`...

## 2. Sort: Sellable vs. Donate vs. Toss
1. Open Claude, attach the item photos.
2. Run `prompts/marketplace-sort-prompt.md`.
3. Review the output — the AI can't feel the item's condition or judge sentimental value, so anything borderline gets a human decision, not the AI's.
4. Anything recalled, broken beyond repair, or with safety concerns (car seats, cribs, helmets) → automatic Donate/Toss regardless of AI output. Check recalls at cpsc.gov before listing baby/child gear.

## 3. Generate the listing
For each item marked Sellable:
1. Run `prompts/marketplace-listing-prompt.md` with that item's photos.
2. Fill the output into `templates/listing.md`.
3. Sanity-check the suggested price against 2–3 actual sold/similar local listings.

## 4. Post it
- Always from **Marie's** Facebook account (Marketplace requires 18+).
- Post within 48 hours of the sort — items lose momentum sitting in a pile.

## 5. Log it
- **Our own inventory:** `tracker/inventory.csv` → `tracker/sales.csv` once sold.
- **Client's Sell-It-For-You items:** `tracker/marketplace-items.csv` (tracks client name, item, list price, status, buyer, sold price, and the 70/30 payout — separate from our own inventory since this money isn't fully ours).

## 6. Manage it
See `sop/08-buyer-and-money-management.md` for messages, safety, pickup, and payout.

## Price drops
If an item hasn't sold in 7 days, drop the price 10–15% and re-list/renew. Check `tracker/marketplace-items.csv` weekly for anything stalling.
