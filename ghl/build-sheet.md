# GHL Build Sheet — The Honey Method

Build these in order. Each section is a literal paste-in — the goal is zero decisions left to make while you're in the GHL UI.

---

## 1. Sub-account settings
- **Name:** The Honey Method
- **Business category:** Home Services / Organizing
- **Timezone:** (your local timezone)
- **Business phone/email:** (the number/email you want clients to see)

---

## 2. Pipeline

**Pipeline name:** Home Reset Pipeline

**Stages, in order:**
1. **New Lead** — a referral just reached out
2. **Intake Sent** — intake form sent, waiting on it back
3. **Quoted** — walkthrough done, quote sent
4. **Booked** — waiver signed, visit(s) scheduled
5. **In Progress** — job underway (multi-visit jobs stay here across all their visits)
6. **Final Visit / Payout Pending** — last visit done; if a Sell-It-For-You payout is owed, it's tracked here until paid
7. **Won — Referral Asked** — job complete, referral ask sent
8. **Lost** — didn't book, or job fell through

Each opportunity in this pipeline = one client engagement (matches one row in `tracker/clients.csv`).

---

## 3. Custom fields (contact-level)

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

## 4. Tags
`lead-new` · `intake-sent` · `quoted` · `waiver-signed` · `in-progress` · `final-visit-sent` · `payout-pending` · `referral-asked` · `past-client` · `marketplace-buyer`

---

## 5. Calendars

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

Write these in GHL's automation builder exactly as specified — trigger, then steps, then the copy. All copy follows the voice rules in `BRAND.md` and `sop/10-coaching-language-guide.md`: warm, specific, never shame-based.

### A. New Lead Welcome
**Trigger:** Intake form submitted
**Steps:**
1. Send email/SMS immediately:
   > "Thanks for reaching out to The Honey Method! We got your form and we're excited to help. We'll be in touch within 24 hours to set up a free walkthrough — no prep needed."
2. Internal task for Marie: "Review intake form for [Contact Name], schedule walkthrough"

### B. Walkthrough Reminder
**Trigger:** Appointment booked on Discovery Walkthrough calendar
**Steps:** confirmation (calendar default above) + 24hr reminder + 2hr reminder (calendar defaults above)

### C. Quote Follow-Up
**Trigger:** Tag `quoted` added, no booking within 3 days
**Steps:**
1. Wait 3 days
2. If still no booking, send:
   > "Just checking in — any questions about the plan we sent over? Happy to adjust the package or timeline to fit what works for you."

### D. Session Reminder
**Trigger:** Appointment booked on Organizing Session calendar
**Steps:** confirmation + 48hr reminder + 24hr reminder (calendar defaults above)

### E. Final Visit → Referral Ask
**Trigger:** Tag `final-visit-sent` added
**Steps:**
1. Wait 4 days (let the workbook land and the feeling settle in first)
2. Send:
   > "It's been so good working in your space with you. If you know anyone else who could use a hand — a friend, a family member, anyone — we'd love an introduction. Refer someone and you both get $20 off your next visit."
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
   > "It's been about two months since we finished your reset — how's the system holding up? We offer a quick maintenance visit (1–2 hrs) to reset anything that's drifted. Want to grab a spot?"

### H. Internal Workbook Reminder
**Trigger:** Any organizing session appointment marked completed
**Steps:**
1. Internal task for Marie/Honey: "Generate + send Progress Report and Workbook for [Contact Name] — due within 24 hours" (see `sop/05` and `sop/06`)

---

## 8. Once this is built
Tell me the sub-account is set up and I will, via API:
- Confirm the pipeline stages exist as expected
- Create the custom fields and tags (or verify yours match this sheet)
- Create the two calendars
- Start logging real clients as contacts/opportunities instead of `tracker/clients.csv` rows
