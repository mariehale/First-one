# Live GHL IDs — Honey!

Reference only — not needed for the UI work in `build-sheet.md`. Used for API calls (creating contacts/opportunities for real clients).

**Location ID:** `2Q37DK8iQ4ORYHL95ElX`
**Company (agency) ID:** `EMbO9rqpNSi4I4cLyzjS`

## Pipeline — DONE, built via GHL's Ask AI
**Pipeline ID:** `ER193vIAQXjqDlYIxV1K` ("Home Reset Pipeline")

| Stage | Stage ID |
|---|---|
| New Lead | `8275b3aa-2bb8-4f11-a579-69c974f495d4` |
| Intake Sent | `07846d4c-2a25-45cc-9d41-53934f998143` |
| Walkthrough Booked | `85be8a16-9edd-4e5e-8d54-f8e8dcc109ea` |
| Quoted | `bdafa8b9-0c1f-4c7f-bfd0-4a42da1a3b09` |
| Booked - Waiver Signed | `980a74be-368c-4b32-a547-24312c9f265d` |
| In Progress | `1a49485c-c159-4351-9a2e-9b6c0656ba12` |
| Final Visit - Payout Pending | `dd99989b-178e-486d-91d5-7030938d9491` |
| Referral Asked | `def4be08-04cb-4915-b2ca-6a8e42b79592` |

Exactly the 8 active-journey stages, no Won/Lost/Abandoned or review stages — built correctly on the first pass.

**Leftover, unused:** the original pre-loaded "Marketing Pipeline" (`ljUHn2NXpQIQ7rDpZwEU`, 11 stages) is still in the account since a new pipeline was created instead of renaming it. Safe to delete whenever, no rush.

## Custom fields (contact-level)
| Field | Field key | ID |
|---|---|---|
| Spaces | `contact.spaces` | `ZAJ279H08G6uYm3kTjee` |
| Package | `contact.package` | `o6Pd0TYV1v90DrY492I6` |
| Total Estimated Hours | `contact.total_estimated_hours` | `ecIWqkFbHYB6vDgjoVvK` |
| Photo Consent | `contact.photo_consent` | `lWWsuOb42XxlPALDf4Jo` |
| Referred By | `contact.referred_by` | `70hMikCqQrOqXV2DuzZh` |
| Cumulative % Complete | `contact.cumulative__complete` | `vREllg2EHHDootRBLMHm` |
| Sell-It-For-You Opt-In | `contact.sellitforyou_optin` | `bf2Y6N2ZS1eJHomLfylB` |

## Tags
`lead-new` `intake-sent` `quoted` `waiver-signed` `in-progress` `final-visit-sent` `payout-pending` `referral-asked` `past-client` `marketplace-buyer` `review-received`

## Calendars
Created via API as `event`-type calendars, which don't require a `teamMembers` user ID (unlike personal/round-robin types). Business hours (Mon–Fri 9–5, Sat 9–1, America/Chicago) set via `createCalendarSchedule` after the fact — the calendars didn't fully "exist" for workflow triggers until this was added (see `build-sheet.md` §5).

| Calendar | ID | Slug |
|---|---|---|
| Free Discovery Walkthrough | `OUJXmLMGkyNQEOrThITU` | `free-discovery-walkthrough` |
| Organizing Session | `ToHoo5Kb2TobM24tfAcJ` | `organizing-session` |

Find each calendar's public booking link under **Calendars → [calendar name] → Widget/Share** in the GHL UI — the exact URL depends on your account's domain setup, so grab it there rather than guessing it here.
