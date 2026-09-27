# SOP 9: Things We Almost Forgot

None of this is legal/financial advice — it's a checklist of things to go verify with an accountant, insurance agent, or your state's labor site before they bite you. But don't skip reading it.

## 1. Insurance
Organizers work inside other people's homes with other people's belongings. Look into a small-business **general liability policy** (often $25–50/month) before your first paid job — it covers you if something gets broken or someone's hurt on the job. Ask about a rider for items in your care, custody, or control, since that's exactly what this business does.

## 2. Waivers & consent
- Never start a job without the signed `templates/liability-waiver.md` (liability + photo release combined).
- The photo release matters separately from liability: this business runs private-photos-only by default (referral-only, not publicly advertised) — see `BRAND.md`. The waiver has three tiers: private only, private + anonymized referral show-and-tell, or public marketing. Get an explicit pick per client, not an assumption, and log it in `tracker/clients.csv` (`photo_consent` column).

## 3. Honey is a minor working in the business
Rules vary by state. Before this becomes more than an occasional family activity, check your state's child-labor rules for:
- Minimum age and permitted hours for minors, especially on school nights
- Whether a work permit is required
- Whether wages paid to a minor child by a parent-owned business are exempt from certain payroll taxes (many states have a parent-child exemption, but confirm it applies to your business structure)
Until you've confirmed this, keep Honey's hours light, after-school/weekend only, and treat pay as an allowance/profit-share rather than a formal wage until you've checked with an accountant.

## 4. Business structure & taxes
- Open a **separate bank account** for this business before money starts moving — makes taxes and the Marie/Honey split far easier to track.
- Side income is taxable regardless of business structure. Keep every receipt (supplies, gas, bins) — they're deductions.
- Ask an accountant whether/when to move from informal sole-proprietor to an LLC (usually once revenue or liability risk grows) and whether quarterly estimated taxes apply.

## 5. Scheduling & payments tooling
Right now this repo's CSVs are the whole system, which is fine at low volume. Once bookings pick up, consider a single tool that handles booking + invoicing + review requests together (e.g., Square, HoneyBook, Jobber, or GoHighLevel — this account already has a GoHighLevel connection available, so that's a real option if you want a pipeline: Lead → Quoted → Scheduled → In Progress → Completed → Payout Pending → Closed, with automated review-request texts). Ask if you want this actually built out.

## 6. Photo backup & ownership
Before/after photos are both proof of work and your best marketing asset. Keep the Google Drive folder structure from `sop/02-photo-capture-protocol.md` as the single source of truth, and turn on phone auto-backup to Drive so nothing lives only on one device.

## 7. Referrals — The House of Honey (the primary growth engine)
This is a small, referral-only side hustle — no public advertising by default (see `BRAND.md`). That means referrals carry the whole pipeline, and they're branded, not just tracked: a client who refers someone joins **The House of Honey**.
- Ask for a referral in the **final** workbook of a job (see `sop/06-coaching-workbook.md`), not before — a finished, felt result gets better referrals than a mid-job ask. "Honey, you deserve more" — and so does whoever you know who needs this.
- When a referral books, welcome the original client to the House of Honey in their next workbook (the `.house-banner` block in `templates/workbook.html`) — not just a discount code, an identity.
- Consider a referral discount ($20 off for both people) baked into that ask.
- Track who referred whom in `tracker/clients.csv` (`referred_by` column) so you know who to thank, and can send that person a small thank-you (a discount on their next visit, or a gift card) once the referral books.
- If a client consented to "private + anonymized referral show-and-tell" on their waiver, that's your best sales tool on a discovery call — a real, anonymized before/after beats any pitch.
- Public posting (Nextdoor/Facebook groups, `templates/social-post.md`) is kept in the repo as an optional fallback if referrals ever slow down, not the default plan — see `README.md`.

## 8. Recurring revenue
Offer a **maintenance visit** (monthly or quarterly, 1–2 hrs, keeping the system going) as an upsell in the final workbook of every full organize. This is usually easier margin than a new full job.

## 9. Cancellation / no-show policy
Decided and in `templates/client-quote.md`: payment is collected at booking, 72+ hours' notice moves it to a new date, same-week cancellations forfeit it. Not having a policy is how a business absorbs other people's schedule changes for free.

## 10. Honey's comfort and structure needs
- Every job uses the same photo protocol, same 4-pile system, same break timer, same visit wrap-up — sameness is a feature here, not a limitation. Don't improvise the process even when a job feels "simple."
- Keep a consistent job bag (see `sop/04-session-day-workflow.md`) so nothing about the *tools* changes, even when the *space* does.
- Homes can be dusty, smelly, or visually overwhelming in ways you can't predict from the intake form. It's fine to have an agreed signal Honey can give Marie to take a break or step outside, no explanation needed in the moment.

## 11. Seasonal calendar (carried over from the original plan)
Best seasons to prospect: back-to-school (closets, homework stations), pre-holidays (making room for gifts), January (resolutions), spring cleaning.
