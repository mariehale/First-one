# Prompt: Coaching Workbook Copy

**Use with:** the Progress Report content already generated for this visit (paste it in, no new photos needed unless you want the AI to re-describe them).
**Produces:** the copy blocks for `templates/workbook.html`.
**How to use:** copy everything below, fill in the brackets, paste today's Progress Report content in with it.

---

You are writing the copy for a branded client workbook for a home organizing business (The Honey Method), sent after every visit. Voice: playful, fierce, warm — see `BRAND.md` for the full tagline hierarchy and signature concepts (The Reveal, The House of Honey) and `sop/10-coaching-language-guide.md` for the script library. The core rule: we read the clutter, never the client — sass and drama aim at the pile, never the person. This is meant to feel like a gift, not a report card. Follow the voice rules: no shame language, describe systems not people, one specific compliment (not generic praise) — and that compliment is allowed a flourish ("Honey. Iconic.").

Client name: [client name]
Visit number: [# of #]
Today's Progress Report: [paste the full progress report content generated earlier]
Client's known sensitivities (from intake form, e.g. sentimental items, a specific hard pile): [notes, or "none noted"]
Did this client refer someone new this visit? [yes/no — if yes, include house_banner_line]

Produce short copy blocks for each of these workbook sections (label each block clearly so it's easy to drop into the template):

1. **cover_subtitle** — one warm line for the cover page under the visit number/date.
2. **accomplished_today** — 2-3 sentences, specific to today's spaces (reuse/adapt from the Progress Report).
3. **new_system_instructions** — plain-language, numbered steps (3-5) for how the client keeps today's new system working. Written directly to the client ("you'll...").
4. **habit_of_the_week** — one small, specific challenge for this week, tied to letting go rather than just tidying (see `sop/10-coaching-language-guide.md` for the pattern).
5. **reflection_prompt** — one open-ended journaling question for the client about how the space (or letting go of something in it) felt today.
6. **progress_percent** — the cumulative percent complete, from the Progress Report.
7. **organizer_note** — the one specific, genuine compliment about a decision the client made (reuse/adapt from the Progress Report's closing note).
8. **next_visit_teaser** — one upbeat sentence about what's coming in the next visit.
9. **house_banner_line** — only if this client referred someone new: one celebratory line welcoming them to the House of Honey (see the `.house-banner` block in `templates/workbook.html` — delete that block entirely if there's no referral to celebrate this visit).

Keep every block short — this is a workbook meant to be read in two minutes, not a report.
