# SOP 11: Safety Screening (Honey's idea)

We walk into strangers' homes, and one of us is a minor. This SOP is how we stay safe **for $0**, every client, same order, no exceptions. It runs between intake (`sop/01` step 2) and the walkthrough (step 3): **nobody gets the walkthrough booking link until they're cleared.**

## Honest limits first
There is no free, official, nationwide criminal background check. What we *can* do for free is check the public sources that catch the things that matter most, plus lean on the one thing a paid check can't give us: **someone we know vouching for them.** Being referral-only is our biggest safety feature.

If we ever pay for a background report on a client, those services fall under federal consumer-report rules (FCRA) — read their terms before using one. The free public lookups below don't need any of that.

## Part 1: The 15-minute check (Marie, before sending the walkthrough link)

Do all five, in order. Log the result in GHL (tag, see Part 4) and the `notes` column of `tracker/clients.csv`.

| # | Check | Where (free) | What we're looking for |
|---|---|---|---|
| 1 | **Referrer vouches** | Text the person listed in "Who referred you?" | They actually know this person. Script: *"Hey! [Name] said you sent them our way — thank you! How do you know them?"* No referrer, or the referrer doesn't know them → stop, polite decline. |
| 2 | **Sex offender registry** — name *and* address | **NSOPW.gov** (National Sex Offender Public Website, searches every state at once) | Search the client's name, then search the service address to see who's registered at or near it. Any match at that address → decline. |
| 3 | **Court records** | Your state's free online court case search (search "[your state] court case search") | Violent charges, protective orders, anything involving minors → decline. Old traffic/debt cases → ignore. |
| 4 | **Address is real and theirs** | County assessor/property search, or Google Maps street view | The address exists and it's a home, not a vacant lot or an address that doesn't match what they told us. Renters won't show as owners — that's fine. |
| 5 | **Quick online look** | Google their name + city; their Facebook profile | A real person with a real history. Brand-new or empty profiles plus no referrer = decline. |

**Cleared = all five pass.** If anything is unclear, the answer is no. We don't need every client.

## Part 2: Who else will be there
Intake form now asks: *"Will anyone besides you be home during sessions?"* Unknown adults who'll be home and weren't part of the walkthrough → Marie asks about it before booking.

## Part 3: On-site rules (non-negotiable, every visit)

1. **Marie does the first walkthrough.** Honey comes to paid sessions only after Marie has been in the home.
2. **Honey is never alone with a client or anyone in the home** — not in a separate room, not while Marie steps out to the car. If Marie leaves the room, Honey comes too or the client does.
3. **Check-in text.** Marie texts a trusted adult (not on the job) the address when we arrive and again when we leave. Share live location (Find My / Google Maps) for the length of the session.
4. **Code word.** We agree on one simple word ahead of time. Either of us says it = we pack up and leave, no explanation needed in the moment, no arguing afterward. Honey is allowed to use it any time she feels unsafe or even just "off" — she does not have to explain why, and it's never treated as a mistake.
5. **Exit script** (Marie says it, calm and friendly): *"We're going to wrap up a little early today — we'll text you to reschedule."* Then leave. Figure out the rest from the car.
6. **Car parked facing out, keys and phones on us** (not in a job bin).

## Part 4: Red flags — decline or leave
- Pushback on the referrer check or the ID check at the walkthrough ("why do you need that?")
- Wants Honey to come alone, or asks about Honey specifically in a way that feels off
- Heavy drinking/drug use, aggression, or weapons left out during the walkthrough
- Keeps changing the address, or wants to meet somewhere other than the home
- Anything that makes either of us uneasy. A gut feeling is enough.

**Decline script** (polite, no reason given): *"Thanks so much for thinking of us! Our schedule is full right now, so we're not able to take this one on — wishing you the best with the space."*

## Part 5: Photo ID at the walkthrough
At the walkthrough, Marie confirms the person matches the name on the form (a quick look at their ID is fine: *"Just so our records match — can I see an ID real quick?"*). Don't photograph or store it.

## Part 6: Marketplace buyers
Already covered in `sop/08` — Honey never messages or meets a buyer, public place or police "safe exchange zone," porch pickup only with Marie home. One addition: before any porch pickup, Marie checks the buyer's Facebook profile (account age, Marketplace ratings). New account + no ratings → public meetup only, no porch pickup.

## How this lives in GHL
- **Tags:** `safety-cleared`, `safety-declined` (add manually in Settings → Tags; takes seconds)
- **Intake form:** "Who referred you?" (required, maps to **Referred By**) and "Will anyone besides you be home during sessions?" — see `ghl/build-sheet.md` §6
- **Workflow A** creates Marie's "run the safety check" task when the intake form comes in
- **Workflow J** sends the walkthrough booking link *only* when `safety-cleared` is added — see `ghl/build-sheet.md` §7
- The walkthrough calendar link is **not** on the public microsite — the site's button goes to the "Say hello" form instead.
