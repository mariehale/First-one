# GHL Build Sheet — The Honey Method

Build these in order. Each section is a literal paste-in — the goal is zero decisions left to make while you're in the GHL UI.

---

## 1. Sub-account settings — DONE
- **Name:** The Honey Method ✅ (sub-account is live: `2Q37DK8iQ4ORYHL95ElX`)
- **Timezone:** America/Chicago (already set)
- **Business phone/email:** 708-486-0921 / marie@atrevenue.com (already set)

---

## 2. Pipeline — rename existing stages, don't build a new one

The sub-account came pre-loaded (from the agency's default snapshot) with an 11-stage **"Marketing Pipeline"** that maps cleanly onto the Honey Method journey — richer than the original 8-stage plan, actually, since it splits "asked for a referral" from "asked for a review." No new pipeline needed. In GHL: **Settings → Pipelines → Marketing Pipeline**, rename the pipeline itself and each stage per this table:

| # | Current name | Rename to |
|---|---|---|
| 1 | Marketing Pipeline *(pipeline name)* | **Home Reset Pipeline** |
| 2 | New Lead | New Lead *(keep)* |
| 3 | Contacted | Intake Sent |
| 4 | Qualified | Walkthrough Booked |
| 5 | Estimate Sent | Quoted |
| 6 | Won Bid – Booked Job | Booked (Waiver Signed) |
| 7 | Lost Bid | Lost |
| 8 | Job Completed | In Progress |
| 9 | Payment Complete | Final Visit / Payout Pending |
| 10 | Follow-Up | Won — Referral Asked |
| 11 | Review Requested | Review Requested *(keep)* |
| 12 | Review Received | Past Client |

Each opportunity in this pipeline = one client engagement (matches one row in `tracker/clients.csv`). Exact pipeline/stage IDs are recorded in `ghl/live-ids.md` for API reference — you don't need them for the UI rename.

---

## 3. Custom fields (contact-level) — DONE, created via API

| Field name | Type | Options / notes |
|---|---|---|
| Spaces | Text | e.g. "Pantry, Garage" |
| Package | Dropdown | Quick Refresh / Room Reset / Hourly |
| Total Estimated Hours | Number | From the Initial State Report |
| Photo Consent | Dropdown | Private only / Private + anonymized referral / Public marketing |
| Referred By | Text | Who sent this client — see `sop/09`, section 7 |
| Cumulative % Complete | Number | Updated after every visit, from the Progress Report |
| Sell-It-For-You Opt-In | Yes/No | From intake question 8 |

These mirror `tracker/clients.csv` exactly — once GHL is live, GHL becomes the source of truth and the CSV becomes a backup export, not the primary log.

---

## 4. Tags — DONE, created via API
`lead-new` · `intake-sent` · `quoted` · `waiver-signed` · `in-progress` · `final-visit-sent` · `payout-pending` · `referral-asked` · `past-client` · `marketplace-buyer`

(Two tags came pre-loaded with the snapshot — `follow-up` and `warm lead` — left alone since they don't conflict; ignore or delete them later if they're never used.)

---

## 5. Calendars — blocked, needs your user ID

GHL's API requires a `teamMembers` entry with a real user ID to create a calendar, and the API connection here can't look up users for this sub-account (returns empty — likely a permissions/scope gap on this specific connection). Two ways to unblock:
- Go to **Settings → My Staff** in the GHL sub-account, open your own user, and send me the user ID from the URL, or
- Just build the two calendars below yourself — it's a 2-minute job per calendar in the UI, faster than the back-and-forth to get you the ID.

**Calendar 1 — Free Discovery Walkthrough**
- Duration: 20 min (phone) or 30 min (in-home)
- Buffer: 15 min before/after
- Confirmation message: *"You're booked! We'll walk the space together, ask what's driving you crazy, and send a quote within 24 hours. No prep needed."*
- Reminder: 24 hr and 2 hr before

**Calendar 2 — Organizing Session**
- Duration: 3 hr default (matches Room Reset), adjustable per booking for Quick Refresh (2 hr) or Hourly jobs
- Buffer: 30 min between sessions (travel/reset time)
- Confirmation message: *"You're on the calendar for [date]! One thing to know: don't tidy up before we arrive — we want to see the space as it really lives."*
- Reminder: 48 hr and 24 hr before

---

## 6. Intake form

Build as a GHL Form, fields mapped to custom fields above (matches `templates/client-intake-form.md` exactly):

1. Name / phone / email / address → standard contact fields
2. Which space(s)? → maps to **Spaces**
3. What's driving you crazy about this space? → long text
4. Goal (usable vs. picture-perfect)? → long text
5. Anything sentimental/emotionally difficult we should know about? → long text (optional)
6. Items belonging to someone else needing extra care? → long text (optional)
7. Pets or allergies? → long text
8. Sell unwanted items (Sell-It-For-You) or donate everything? → maps to **Sell-It-For-You Opt-In**
9. Photo comfort level → maps to **Photo Consent**
10. Preferred days/times → long text
11. Anything else? → long text (optional)

On submit: add tag `intake-sent` → `lead-new`, move opportunity to **Intake Sent** stage, trigger Workflow A below.

---

## 7. Workflows

Write these in GHL's automation builder exactly as specified — trigger, then steps, then the copy. All copy follows the voice rules in `BRAND.md` and `sop/10-coaching-language-guide.md`: warm, specific, never shame-based. Per `BRAND.md` rule 5, these transactional messages keep the taglines but dial back the deeper slang (Reveal, House of Honey, etc. stay for the workbook and site, where the audience has already opted in) — clear beats clever when it's a booking reminder.

### A. New Lead Welcome
**Trigger:** Intake form submitted
**Steps:**
1. Send email/SMS immediately:
   > "Honey! No shame — we've got you. Thanks for reaching out to The Honey Method. We got your form and we're excited to help. We'll be in touch within 24 hours to open the library and set up your free walkthrough — no prep needed."
2. Internal task for Marie: "Review intake form for [Contact Name], schedule walkthrough"

### B. Walkthrough Reminder
**Trigger:** Appointment booked on Discovery Walkthrough calendar
**Steps:** confirmation (calendar default above) + 24hr reminder + 2hr reminder (calendar defaults above)

### C. Quote Follow-Up
**Trigger:** Tag `quoted` added, no booking within 3 days
**Steps:**
1. Wait 3 days
2. If still no booking, send:
   > "Just checking in, Honey — any questions about the plan we sent over? Happy to adjust the package or timeline to fit what works for you."

### D. Session Reminder
**Trigger:** Appointment booked on Organizing Session calendar
**Steps:** confirmation + 48hr reminder + 24hr reminder (calendar defaults above)

### E. Final Visit → Referral Ask
**Trigger:** Tag `final-visit-sent` added
**Steps:**
1. Wait 4 days (let the workbook land and the feeling settle in first)
2. Send:
   > "Honey, you deserve more — and so does anyone you know who's drowning in their own clutter. If a friend, a family member, or anyone comes to mind, we'd love an introduction. Refer someone and you both get $20 off, plus a spot in the House of Honey."
3. Add tag `referral-asked`, move opportunity to **Won — Referral Asked**

### F. Sell-It-For-You Payout Reminder (internal only, not client-facing)
**Trigger:** Tag `payout-pending` added
**Steps:**
1. Create internal task for Marie: "Pay [Contact Name] their 70% Sell-It-For-You payout — due within 5 business days" with a due date 5 business days out
2. On task completion, remove `payout-pending` tag

### G. Maintenance Upsell
**Trigger:** 60 days after opportunity marked **Won**
**Steps:**
1. Send:
   > "It's been about two months since your reset — how's the system holding up, Honey? We offer a quick maintenance visit (1–2 hrs) to reset anything that's drifted. Want to grab a spot?"

### H. Internal Workbook Reminder
**Trigger:** Any organizing session appointment marked completed
**Steps:**
1. Internal task for Marie/Honey: "Generate + send Progress Report and Workbook for [Contact Name] — due within 24 hours" (see `sop/05` and `sop/06`)

---

## 8. Status
- [x] Custom fields and tags — created via API, see `ghl/live-ids.md`
- [x] Pipeline — exists (renamed from the agency's default snapshot), see §2 above for the rename table
- [ ] Calendars — blocked on a user ID, see §5
- [ ] Forms, workflows, microsite — still to build from this sheet and `microsite-copy.md`

Once forms/workflows/site are built, tell me and I'll start logging real clients as contacts/opportunities via API instead of `tracker/clients.csv` rows.
