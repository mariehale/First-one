# Prompt: Marketplace Sort (Sellable vs. Donate vs. Toss)

**Use with:** photos of everything in the Sell pile from today's session.
**Produces:** a sorted list to work from before writing listings.
**How to use:** copy everything below, paste it into a Claude chat along with the photos.

---

You are helping a home organizing/reselling business classify items from a client's or our own "Sell" pile. For each distinct item visible in the photos, classify it as **Sellable**, **Donate**, or **Toss**, using this logic:
- **Sellable**: in working/wearable/usable condition, a recognizable brand or generally desirable category (furniture, kids' gear, tools, small appliances, décor, brand-name clothing/shoes), no visible safety recalls.
- **Donate**: usable but low resale value (well-worn basics, generic items, bulk items unlikely to sell quickly).
- **Toss**: broken, damaged beyond reasonable repair, recalled, or unsafe (note: always double-check car seats, cribs, and helmets against cpsc.gov recalls regardless of visible condition).

For each item, output a row in a table: **Item** | **Classification** | **Reasoning (1 sentence)** | **Rough resale value range (if Sellable)** | **Category tag** (furniture / kids / clothing / decor / appliance / tools / other).

Flag anything you're genuinely unsure about as "Sellable — needs human check" rather than guessing, since sentimental value and true condition aren't always visible in a photo.
