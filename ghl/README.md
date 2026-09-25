# GHL Setup — The Honey Method

This runs the business's CRM/booking/automation layer in GoHighLevel, built to the same standard as a real, scaling business — not a bare-bones side-hustle setup.

## What's here
- **`build-sheet.md`** — the exact spec to build in GHL: pipeline stages, custom fields, tags, calendars, forms, and every automation workflow (trigger + copy). Most of this has to be built by hand in GHL's UI — see "Why not automated?" below — so this doc is written to be pasted straight in, section by section.
- **`microsite-copy.md`** — the site content, section by section, matching the design mockup: **https://claude.ai/artifact/HsUr1YzFYwB7BFtJJKTvV5**

## Status
- [ ] New GHL sub-account created (name/ID: `__________`) — once you have this, tell me and I'll run the API-buildable setup below.
- [ ] Pipeline built from `build-sheet.md`
- [ ] Custom fields built (I can do this via API once the sub-account exists)
- [ ] Calendars built (I can do this via API)
- [ ] Forms built from `build-sheet.md`
- [ ] Workflows built from `build-sheet.md`
- [ ] Microsite built from `microsite-copy.md`

## Why not everything is automated
GoHighLevel's public API — the only access this session has, no browser/UI access into your account — does not expose write operations for: creating a new sub-account, creating a pipeline, creating a workflow/automation, creating a funnel or website page, or creating a form. Those all live in GHL's visual drag-and-drop builders (including "AI Studio"), which are UI-only.

What the API **can** do, once a sub-account exists and its ID is confirmed:
- Create custom fields, custom values, and tags
- Create calendars (booking pages)
- Create/update contacts and opportunities (opportunities need a pipeline to already exist — built by hand first)
- Create appointments

So the plan is: you build the four UI-only pieces (pipeline, forms, workflows, site) from the specs in this folder — each is a short, literal copy-paste job — and I handle everything else via API plus keep this repo's SOPs/prompts/templates in sync with however GHL ends up structured.
