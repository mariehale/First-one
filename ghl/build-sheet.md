# GHL Build Sheet — Honey!

Build these in order. Each section is a literal paste-in — the goal is zero decisions left to make while you're in the GHL UI.

---

## 1. Sub-account settings — DONE
- **Name:** Honey! — still shows as "The Honey Method" in GHL. No API operation renames a sub-account; rename it yourself in **Settings → Business Profile** (sub-account is live: `2Q37DK8iQ4ORYHL95ElX`)
- **Timezone:** America/Chicago (already set)
- **Business phone/email:** 708-486-0921 / marie@atrevenue.com (already set)

---

## 2. Pipeline — DONE, built via GHL's Ask AI (`ER193vIAQXjqDlYIxV1K`, see `live-ids.md`)

**GHL conventions (Marie's corrections, keep these permanently):**
1. Every pipeline already has native **Won**, **Lost**, and **Abandoned** opportunity statuses built in. Never build a custom stage for these — a "Lost" or "Past Client" stage lets an opportunity sit there forever instead of actually closing, which breaks the pipeline's conversion/win-rate reporting. Stages are for the *active* journey only; closing happens by changing the opportunity's native status, not by moving it to a terminal stage.
2. Review requesting/tracking doesn't belong in the pipeline either — it's a time-based nudge sequence with no natural "stage," so it's a **workflow** (see §7, Workflow I), not stages.

GHL's pipeline builder has a "Generate with AI" option (describe the pipeline, it drafts the stages). Use it instead of hand-renaming — go to **Settings → Pipelines → Create Pipeline → Generate with AI** and paste this:

> Create a pipeline called "Home Reset Pipeline" for a home organizing and resale business run by a mother-daughter team. Stages in order, active-journey only (no Won/Lost/Abandoned stages and no review-tracking stages — those are handled outside the pipeline): New Lead (a referral just reached out), Intake Sent (intake form sent, waiting on it back), Walkthrough Booked (free discovery call scheduled), Quoted (walkthrough done, quote sent), Booked - Waiver Signed (client signed the waiver and visits are scheduled), In Progress (job underway, may span multiple visits), Final Visit - Payout Pending (last visit done, any resale payout still owed to the client), Referral Asked (job complete, referral ask sent).

Each opportunity in this pipeline = one client engagement (matches one row in `tracker/clients.csv`). When a lead doesn't book, or a job falls through, mark the opportunity's status **Lost** (or **Abandoned** if it just went cold) — don't move it to a stage. Once the job is fully wrapped and the referral ask is sent, mark it **Won** — that's what makes reporting accurate, and the `past-client` tag (already created) covers segmentation from there. Review requesting runs entirely in Workflow I, independent of the pipeline.

**Faster alternative:** the sub-account already came pre-loaded (from the agency's default snapshot) with an 11-stage "Marketing Pipeline." Eight of its stages map 1:1 onto the list above with a rename; the other three duplicate native statuses or belong in a workflow instead, and should be deleted, not renamed:

| # | Current name | Action |
|---|---|---|
| — | Marketing Pipeline *(pipeline name)* | Rename to **Home Reset Pipeline** |
| 1 | New Lead | Keep as **New Lead** |
| 2 | Contacted | Rename to **Intake Sent** |
| 3 | Qualified | Rename to **Walkthrough Booked** |
| 4 | Estimate Sent | Rename to **Quoted** |
| 5 | Won Bid – Booked Job | Rename to **Booked (Waiver Signed)** |
| 6 | Lost Bid | **Delete** — use the native Lost status instead |
| 7 | Job Completed | Rename to **In Progress** |
| 8 | Payment Complete | Rename to **Final Visit / Payout Pending** |
| 9 | Follow-Up | Rename to **Referral Asked** |
| 10 | Review Requested | **Delete** — review tracking moves to Workflow I |
| 11 | Review Received | **Delete** — use the native Won status + Workflow I instead |

Either path lands in the same eight-stage pipeline. Exact IDs for the existing snapshot pipeline are in `ghl/live-ids.md` if you go the rename route.

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
`lead-new` · `intake-sent` · `quoted` · `waiver-signed` · `in-progress` · `final-visit-sent` · `payout-pending` · `referral-asked` · `past-client` · `marketplace-buyer` · `review-received`

**To add manually (Settings → Tags, seconds each):** `safety-cleared` · `safety-declined` — for the safety check in `sop/11-safety-screening.md`. Add these before building Workflows A and J, since both reference them.

(Two tags came pre-loaded with the snapshot — `follow-up` and `warm lead` — left alone since they don't conflict; ignore or delete them later if they're never used.)

---

## 5. Calendars — DONE, created via API

Both built as `event`-type calendars (that type doesn't need a `teamMembers` user ID, unlike personal/round-robin types):

**Calendar 1 — Free Discovery Walkthrough** (`OUJXmLMGkyNQEOrThITU`)
- Duration: 30 min, buffer 15 min before/after, bookable 4 hrs–30 days out
- Confirmation message set: *"You're booked! We'll walk the space together, ask what's driving you crazy, and send a quote within 24 hours. No prep needed."*

**Calendar 2 — Organizing Session** (`ToHoo5Kb2TobM24tfAcJ`)
- Duration: 3 hrs, buffer 30 min, bookable 24 hrs–60 days out
- Confirmation message set: *"You're on the calendar! One thing to know: don't tidy up before we arrive — we want to see the space as it really lives."*

**Business hours (fixed — see the note below):** Mon–Fri 9am–5pm, Sat 9am–1pm, America/Chicago, on both calendars.

**One manual touch-up remaining:** reminder notifications (24hr/2hr before for the walkthrough, 48hr/24hr before for the session) hit a server error via API, likely because GHL wants an existing notification template ID I don't have. Quickest fix: open each calendar in GHL → **Notifications** tab → toggle on the default reminder emails/texts and set the timing. Takes under a minute per calendar.

**GHL convention (Marie's correction, keep this permanently): "created" isn't "complete."** Both calendars were created via API with empty availability hours, which made them *exist* but not be *real enough* for a workflow trigger to resolve — GHL's Workflow AI generated a trigger referencing the calendar by name, and it still errored "Calendar not found" because the calendar had no business hours set. Before generating a workflow (or anything else) that references another object by name — a calendar, a form, a pipeline stage — confirm that object is fully configured in the GHL UI, not just present in a list somewhere.

---

## 6. Intake form — MANUAL ONLY, build in GHL desktop, no AI shortcut

Confirmed: unlike the pipeline (which GHL's Ask AI built correctly on the first try), forms are not buildable through any AI generator — this one needs the desktop form builder, by hand. Build as a GHL Form, fields mapped to custom fields above (matches `templates/client-intake-form.md` exactly):

1. Name / phone / email / address → standard contact fields
   - **Who referred you to us?** → maps to **Referred By**, **required** (safety check step 1, `sop/11`)
   - **Will anyone besides you be home during sessions?** → short text
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

## 7. Workflows — use GHL's Workflow AI

Each workflow below is written as one paste-ready paragraph for GHL's **Automation → Create Workflow → Generate with AI** box (the same "Ask AI" that built the pipeline). Don't retype it as a manual trigger/steps table — paste the whole paragraph in and let it draft the workflow, then just glance over what it built before publishing. All copy follows the voice rules in `BRAND.md` and `sop/10-coaching-language-guide.md`. Per `BRAND.md` rule 5, these transactional messages keep the taglines but dial back the deeper slang (Reveal, House of Honey stay for the workbook and site) — clear beats clever in a booking reminder.

**Build order:** Workflow A's trigger is the intake form, which doesn't exist until §6 is done manually. Build **B through I first** (then J once the two safety tags exist) — none of them depend on the form, they trigger off calendars, tags, and pipeline status that already exist — then come back to A last, once the form is live.

### A. New Lead Welcome (build this last, after §6)
> When a contact submits the intake form, add the tags lead-new and intake-sent, move their opportunity in the Home Reset Pipeline to the Intake Sent stage, and immediately send them this message by both email and SMS: "Honey! No shame — we've got you. Thanks for reaching out to Honey!. We got your form and we're excited to help. We'll be in touch within 24 hours to open the library and set up your free walkthrough — no prep needed." Then create a task for Marie due in 1 day: "Run the safety check for [contact name] (referrer vouches, NSOPW.gov name + address, court records, address check, quick online look). Add tag safety-cleared to send the walkthrough link, or safety-declined to stop." Do not send the walkthrough booking link in this workflow.

### B. Walkthrough Reminder — DONE, built and published
> When an appointment is booked on the Free Discovery Walkthrough calendar, send this confirmation immediately: "You're booked! We'll walk the space together, ask what's driving you crazy, and send a quote within 24 hours. No prep needed." Then send a reminder 24 hours before the appointment, and another reminder 2 hours before.

### C. Quote Follow-Up
> When a contact is tagged quoted, wait 3 days. If their opportunity has not reached the Booked stage by then, send: "Just checking in, Honey — any questions about the plan we sent over? Happy to adjust the package or timeline to fit what works for you."

### D. Session Reminder
> When an appointment is booked on the Organizing Session calendar, send this confirmation immediately: "You're on the calendar for [date]! One thing to know: don't tidy up before we arrive — we want to see the space as it really lives." Then send a reminder 48 hours before, and another reminder 24 hours before.

### E. Final Visit → Referral Ask
> When a contact is tagged final-visit-sent, wait 4 days, then send: "Honey, you deserve more — and so does anyone you know who's drowning in their own clutter. If a friend, a family member, or anyone comes to mind, we'd love an introduction. Refer someone and you both get $20 off, plus a spot in the House of Honey." Then add the tag referral-asked, move their opportunity to the Referral Asked stage, and mark the opportunity's status as Won.

### F. Sell-It-For-You Payout Reminder (internal only, not client-facing)
> When a contact is tagged payout-pending, create a task for Marie due in 5 business days: "Pay [contact name] their 70% Sell-It-For-You payout." When that task is marked complete, remove the payout-pending tag.

### G. Maintenance Upsell
> 60 days after a contact's opportunity is marked Won in the Home Reset Pipeline, send: "It's been about two months since your reset — how's the system holding up, Honey? We offer a quick maintenance visit (1–2 hrs) to reset anything that's drifted. Want to grab a spot?"

### H. Internal Workbook Reminder
> When an appointment on the Organizing Session calendar is marked completed, create a task for Marie and Honey due within 24 hours: "Generate and send the Progress Report and Workbook for [contact name]."

### I. Review Request Nudges
> When a contact is tagged final-visit-sent, wait 5 days, then send: "If you have 60 seconds, a review would mean the world to us — and it helps other overwhelmed people find their way to Honey!. [review link]" Wait 5 more days. If the contact is not tagged review-received by then, send a second, gentler nudge: "No pressure at all — but if you have a quick moment, we'd still love a review. [review link]" Wait 4 more days (14 days total since the first message). If the contact is still not tagged review-received, create a task for Marie: "No review yet from [contact name] after two nudges and two weeks — follow up personally or let it go." When the review-received tag is added at any point, end this workflow for that contact.

### J. Safety Cleared → Send Walkthrough Link (build after the two safety tags exist)
> When the tag safety-cleared is added to a contact, send them this message by both email and SMS: "Great news, Honey — the library is open! Grab a time for your free walkthrough here: [Free Discovery Walkthrough booking link]. No prep needed, and please don't tidy up first." Then move their opportunity in the Home Reset Pipeline to the Walkthrough Booked stage only after they book an appointment on the Free Discovery Walkthrough calendar. When the tag safety-declined is added instead, send nothing automatically, move the opportunity status to Lost, and create a task for Marie: "Send the polite decline to [contact name] (script in sop/11)."

Why a separate workflow: the walkthrough calendar link is never public (not on the microsite, not in Workflow A). The only way a stranger gets into our calendar is through `safety-cleared`. See `sop/11-safety-screening.md`.

---

## 8. Status
- [x] Custom fields and tags — created via API, see `ghl/live-ids.md`
- [x] Calendars — created via API, see §5
- [x] Pipeline — built via GHL's Ask AI, exactly 8 stages, no Won/Lost/Abandoned or review stages, see §2
- [ ] Tags `safety-cleared` and `safety-declined` — add manually, see §4
- [ ] Forms, workflows, microsite — still to build from this sheet (§6, §7) and `microsite-copy.md`

Once forms/workflows/site are built, tell me and I'll start logging real clients as contacts/opportunities via API instead of `tracker/clients.csv` rows.
