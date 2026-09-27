# SOP 5: Progress Report (every visit)

Generate this the same day as the visit, or first thing the next morning — momentum matters to clients who feel behind.

1. Make sure After photos from today are uploaded (`/Clients/<name>/<date>/After/`).
2. Open a Claude chat, attach today's After photos plus (if useful) the original Before photos for comparison.
3. Copy `prompts/progress-report-prompt.md`, fill in the brackets (client name, visit number, spaces done today, any notes from the client conversation), paste it with the photos.
4. Fill the output into `templates/progress-report.md`.
5. Update the **cumulative % complete** by comparing spaces done so far against the total space list from the Initial State Report — the prompt does the math if you give it both numbers.
6. This report's content feeds directly into the Workbook (next step) — don't skip it even on a quick visit.
7. Update `tracker/sessions.csv` with the running total.

Next: `sop/06-coaching-workbook.md`.
