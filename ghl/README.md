# GHL Setup — Honey!

This runs the business's CRM/booking/automation layer in GoHighLevel, built to the same standard as a real, scaling business — not a bare-bones side-hustle setup.

## What's here
- **`build-sheet.md`** — ready-to-paste prompts for GHL's own AI generators (pipeline AI, Workflow AI) plus the custom fields/tags/calendars/forms spec. See "Why AI-generator prompts, not manual steps" below.
- **`microsite-copy.md`** — the site content, section by section, matching the design mockup: **https://claude.ai/artifact/HsUr1YzFYwB7BFtJJKTvV5**
- **`live-ids.md`** — the real location/pipeline/field/tag IDs from the live sub-account, for API reference.

## Status
- [x] Sub-account live (`2Q37DK8iQ4ORYHL95ElX`) — [ ] still displays as "The Honey Method" in GHL; rename it to **Honey!** in Settings → Business Profile (no API for this, see below)
- [x] Pipeline — **Home Reset Pipeline** built via GHL's Ask AI, exactly 8 active-journey stages, no Won/Lost/Abandoned or review stages (see `live-ids.md` for IDs). The old pre-loaded "Marketing Pipeline" is unused and safe to delete whenever.
- [x] Custom fields — all 7 created via API
- [x] Tags — all 11 created via API (includes `review-received`, added for the review-nudge workflow)
- [x] Calendars — both created via API as `event`-type calendars (no user ID needed after all). One manual touch-up: reminder notifications need to be toggled on in the GHL UI, see `build-sheet.md` §5
- [ ] Tags `safety-cleared` / `safety-declined` — add manually in Settings → Tags (safety check, `sop/11`)
- [ ] Intake form — **manual only**, confirmed no AI shortcut exists for forms (unlike the pipeline). Build in GHL desktop from `build-sheet.md` §6
- [ ] Workflows — paste the 10 prompts in `build-sheet.md` §7 into GHL's Workflow AI (includes Workflow I: two review-request nudges, then an internal alert at 2 weeks if no review)
- [ ] Microsite built from `microsite-copy.md`

## Why AI-generator prompts, not manual steps
GoHighLevel's public API — the only access this session has, no browser/UI access into your account — has no write operations at all for pipelines, workflows, funnels/site pages, or forms. This isn't a gap in how I searched: the `workflows` domain has exactly one operation in the whole API, and it's read-only. GHL's own AI builders (the pipeline generator, Workflow AI, "AI Studio" for sites) call GoHighLevel's internal, non-public endpoints — no outside integration can drive them via API, this one included.

But those AI builders are sitting right there in your GHL UI, and they take a plain-language prompt. So instead of a manual click-by-click spec, `build-sheet.md` gives you one paste-ready paragraph per pipeline and per workflow — you paste it into GHL's own "Generate with AI" box and it builds the thing. Your remaining work is paste-and-check, not manual configuration.

What the API **can** do directly, no UI needed:
- Create custom fields, custom values, and tags — done
- Create calendars (booking pages) — done
- Create/update contacts and opportunities, once a pipeline exists
- Create appointments

**Still on you:** the intake form (manual, desktop, §6), the 10 workflows (Ask AI, build B–I first, then J, A last — §7), and the microsite from `microsite-copy.md`, plus toggling on calendar reminders. Once those are in place, tell me and I'll start logging real clients as contacts/opportunities via API instead of `tracker/clients.csv` rows.
