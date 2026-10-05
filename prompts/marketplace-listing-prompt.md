# Prompt: Marketplace Listing Generator

**Use with:** the photo set for one specific Sellable item (front, back, tag/label, flaw close-ups, scale reference).
**Produces:** the content for `templates/listing.md`.
**How to use:** copy everything below, fill in the brackets, paste it into a Claude chat along with that item's photos. Run once per item.

---

Write a Facebook Marketplace listing from the attached photos of one item.

Item category/context (if known): [furniture / kids gear / clothing / decor / appliance / tools / other]
Local area for pickup: [city/neighborhood]
Any known flaws not obvious from photos: [notes, or "none"]

Produce:
1. **Title** — brand + item + key detail (e.g., "IKEA Hemnes 6-Drawer Dresser – White"). Keep it searchable.
2. **Suggested price** — a number, with one sentence explaining the reasoning (condition, typical resale range for this category). Note that this should be sanity-checked against 2-3 actual local sold listings before posting.
3. **Description** — size/dimensions if visible or estimable, condition (honest about any visible flaws), pickup area, and "cash or Venmo at pickup."
4. **Category** for Marketplace's own category field.
5. **Bundle suggestion** — only if the item is small/cheap enough that bundling would sell faster (e.g., "consider bundling with other kids' books").
