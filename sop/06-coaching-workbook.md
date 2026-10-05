# SOP 6: The Coaching Workbook (sent after every visit)

This is the branded, client-facing deliverable — it's what makes clients feel cared for between visits and is a big part of the referral engine. It goes out after **every** visit, not just the last one.

1. Have the Progress Report content from `sop/05-progress-report.md` ready — the workbook reuses it, it doesn't duplicate the work.
2. Open a Claude chat and run `prompts/coaching-workbook-prompt.md`, filling in the brackets. This generates the *copy* for each workbook section (it does not touch the design).
3. Open `templates/workbook.html` in a text editor. Replace each `{{TOKEN}}` with the matching generated text and the photo file paths from today.
4. Open the HTML file in a browser → Print → Save as PDF (letter size).
5. Email the PDF to the client within 24 hours of the visit. Subject line:
   `Your Home Reset Workbook — Visit [#] — [Client Last Name]`
6. Save a copy to `/Clients/<name>/<date>/Workbook.pdf` in Drive.

## What's inside the workbook (see `templates/workbook.html`)
- Cover page with client name, visit number, date, and the hero tagline ("Clutter, Meet Your Match.")
- "What We Accomplished Today" — before photo alongside **The Reveal** (the after photo, styled in the magenta spotlight accent — see `BRAND.md`)
- "Your New System" — plain-language instructions for keeping the new setup working
- "Habit of the Week" — one small, specific coaching challenge (see `sop/10-coaching-language-guide.md` for how to write these — they're about letting go, not just tidying)
- Progress bar — % of the whole home reset complete
- "A Note From Your Organizer" — one genuine, specific compliment, delivered with a little flourish
- **House of Honey banner** — only include this block when the client referred someone new this visit; delete it otherwise
- "Next Visit" — date and what's planned

Once you like the design, this is also the piece worth upgrading in Canva for a more polished/printable look — the HTML version is the functional starting point.
