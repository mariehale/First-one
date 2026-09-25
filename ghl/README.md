# GHL Setup — The Honey Method

This runs the business's CRM/booking/automation layer in GoHighLevel, built to the same standard as a real, scaling business — not a bare-bones side-hustle setup.

## What's here
- **`build-sheet.md`** — ready-to-paste prompts for GHL's own AI generators (pipeline AI, Workflow AI) plus the custom fields/tags/calendars/forms spec. See "Why AI-generator prompts, not manual steps" below.
- **`microsite-copy.md`** — the site content, section by section, matching the design mockup: **https://claude.ai/artifact/HsUr1YzFYwB7BFtJJKTvV5**
- **`live-ids.md`** — the real location/pipeline/field/tag IDs from the live sub-account, for API reference.

## Status
- [x] Sub-account live: **The Honey Method** (`2Q37DK8iQ4ORYHL95ElX`)
- [x] Pipeline exists — came pre-loaded with 11 stages from the agency snapshot, mapped onto the Honey Method journey (`build-sheet.md` §2 has both the AI-generate prompt and the faster rename-only path)
- [x] Custom fields — all 7 created via API
- [x] Tags — all 10 created via API
- [ ] Calendars — blocked: the API can't look up a user ID for this sub-account. Either send me your GHL user ID (Settings → My Staff) or build the two calendars yourself from `build-sheet.md` §5 (~2 min each)
- [ ] Forms built from `build-sheet.md`
- [ ] Workflows — paste the 8 prompts in `build-sheet.md` §7 into GHL's Workflow AI
- [ ] Microsite built from `microsite-copy.md`

## Why AI-generator prompts, not manual steps
GoHighLevel's public API — the only access this session has, no browser/UI access into your account — has no write operations at all for pipelines, workflows, funnels/site pages, or forms. This isn't a gap in how I searched: the `workflows` domain has exactly one operation in the whole API, and it's read-only. GHL's own AI builders (the pipeline generator, Workflow AI, "AI Studio" for sites) call GoHighLevel's internal, non-public endpoints — no outside integration can drive them via API, this one included.

But those AI builders are sitting right there in your GHL UI, and they take a plain-language prompt. So instead of a manual click-by-click spec, `build-sheet.md` gives you one paste-ready paragraph per pipeline and per workflow — you paste it into GHL's own "Generate with AI" box and it builds the thing. Your remaining work is paste-and-check, not manual configuration.

What the API **can** do directly, no UI needed:
- Create custom fields, custom values, and tags — done
- Create calendars (booking pages) — blocked only on a user ID, see Status above
- Create/update contacts and opportunities, once a pipeline exists
- Create appointments

Once the pipeline, forms, and workflows are built (by you, via the AI-generator prompts) and the calendars are sorted, I'll start logging real clients as contacts/opportunities via API instead of `tracker/clients.csv` rows.
