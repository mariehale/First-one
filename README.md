# The Honey Method

*(Placeholder name — see `BRAND.md`.)*

**No shame. Just space.**

A mother-daughter team that organizes homes, sells what clients don't need, and helps them let go of the guilt around how it got that way. This repo is the operating manual: every step-by-step process, every AI prompt, every template, and every tracker the business runs on.

**Why "AI-compatible" matters here:** every job produces the same predictable outputs — an Initial State Report, a Progress Report per visit, and a branded Coaching Workbook per visit — generated the same way every time by pasting photos into Claude with the prompts in `prompts/`. Same process every time is also exactly what makes this work for Honey: nothing is improvised, every job follows the same numbered steps.

## Start here
| If you want to... | Go to |
|---|---|
| See the whole client journey, step by step | `sop/` (read `01` through `10` in order, once) |
| Copy-paste the actual AI prompts | `prompts/` |
| Fill in a report, quote, listing, waiver, or the workbook | `templates/` |
| Log a client, a visit, a sale, or an expense | `tracker/` |
| Brand voice, colors, name | `BRAND.md` |

## Who does what
| | Marie | Honey |
|---|---|---|
| Client calls, quotes, scheduling | ✅ | |
| Hands-on organizing | ✅ | ✅ |
| Before/after & marketplace photos (`sop/02`) | | ✅ |
| Running the AI prompts & filling templates | ✅ | ✅ |
| Posting listings & answering buyers | ✅ | |
| Meeting buyers for pickups | ✅ | with Marie only |
| Tracking money (`tracker/`) | ✅ | ✅ |

**Why Marie posts listings and handles buyers:** Facebook Marketplace requires 18+, and Honey should never meet or message a buyer alone. Full safety rules: `sop/08-buyer-and-money-management.md`.

## The client journey (full detail in `sop/`)
1. **Intake** (`sop/01`) — first contact through signed waiver and booking.
2. **Photo capture** (`sop/02`) — the before-photo checklist every job starts with.
3. **AI Initial Assessment** (`sop/03`) — turns before-photos into the client's Home Reset Plan: room-by-room assessment, time estimate, resale potential, step-by-step strategy.
4. **Session day** (`sop/04`) — the on-site Keep/Sell/Donate/Toss workflow, every visit.
5. **Progress Report** (`sop/05`) — a short update after every visit, tracking cumulative % complete against the original plan.
6. **Coaching Workbook** (`sop/06`) — the branded, cute deliverable sent after every visit (see `templates/workbook.html`).
7. **Marketplace pipeline** (`sop/07`) — Sell pile → AI sort (sellable/donate/toss) → AI-written listing → posted.
8. **Buyer & money management** (`sop/08`) — safety rules, message scripts, payouts.
9. **Things we almost forgot** (`sop/09`) — insurance, waivers, minor-labor rules, taxes, backups, reviews, recurring revenue.
10. **Coaching language guide** (`sop/10`) — the shame-aware scripts behind every client-facing word.

## Pricing (starter — raise after ~5 jobs)
| Package | What's included | Price |
|---|---|---|
| **Quick Refresh** | One small space, ~2–3 hrs | $150 |
| **Room Reset** | One full room, ~4–5 hrs | $275 |
| **Hourly** | Bigger/unusual jobs, 2 people, 3-hr minimum | $60/hr for the team |
| **Sell-It-For-You add-on** | We photograph, list, and sell the client's items | We keep 30%, client keeps 70% |

Supplies (bins, labels, baskets) billed at cost, or the client buys from a list sent ahead of time.

## Marketplace reselling — our own inventory
Same pipeline as client Sell-It-For-You items (`sop/07`), tracked in `tracker/inventory.csv` → `tracker/sales.csv` instead of `tracker/marketplace-items.csv`. Start with our own house — free inventory, good practice, first portfolio photos. Sells well locally: furniture, kids' gear/toys, brand-name clothes/shoes, home decor, small appliances, tools & seasonal gear (sell *before* the season). Skip anything broken, recalled, or dirty — check car seats/cribs against cpsc.gov recalls first.

## Money
- Log every sale/job in `tracker/sales.csv`, every expense in `tracker/expenses.csv`, every client Sell-It-For-You item in `tracker/marketplace-items.csv`.
- **Marie/Honey split:** agree on this and write it here. `__________`
- Consider putting 10–20% of every payout into Honey's savings.
- Open a separate business bank account and keep every receipt — see `sop/09` before this grows past a hobby.

## First 30 days
**Week 1**
- [ ] Fill in the money split above
- [ ] Buy the supply kit (label maker, clear bins, drawer dividers, trash bags, 4 labeled Keep/Sell/Donate/Toss bins, cleaning supplies, measuring tape)
- [ ] Pick a real business name and swap it into `BRAND.md` and this README
- [ ] Get liability insurance quotes (`sop/09`)
- [ ] Organize one space in our own house using the full SOP flow, start to finish, as a dry run

**Week 2**
- [ ] Run the full AI pipeline once end-to-end on our own house (Initial Assessment → session → Progress Report → Workbook)
- [ ] List the first 10 items from our own Sell pile
- [ ] Organize a second space at home

**Week 3**
- [ ] Post before/afters in local Facebook groups and on Nextdoor
- [ ] Book 1–2 discounted "portfolio" jobs with friends (photos + review in exchange)

**Week 4**
- [ ] First real paid client, full journey start to finish
- [ ] Review the trackers: what made the most per hour, what to change

## Repo map
```
BRAND.md              brand voice, colors, tagline
sop/                   the step-by-step manual, 01-10, read in order once
prompts/               copy-paste AI prompts for reports, workbook copy, and marketplace
templates/             fill-in-the-blank docs: quotes, reports, workbook, waiver, listings
tracker/               clients.csv, sessions.csv, sales.csv, expenses.csv, inventory.csv, marketplace-items.csv
```
