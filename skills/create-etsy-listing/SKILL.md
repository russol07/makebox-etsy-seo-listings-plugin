---
name: create-etsy-listing
description: Create a new physical Etsy listing in the seller's connected shop - category, attributes, price, quantity, shipping and processing profiles, photos, personalization and SEO copy - show it in full, and save it as an Etsy draft or publish it only after approval.
---

# Create an Etsy listing

Read [listing creation](../../references/listing-creation.md) and [Etsy SEO rules](../../references/etsy-seo-rules.md).

1. Product facts from the seller: what it is, materials, size, colours, who made it and when, what is included, personalization. Do not invent any of it.
2. `get_listing_requirements`: shipping profiles, processing profiles, return policies, currency. If a profile is missing, the seller must create it in Etsy Shop Manager first.
3. `search_categories` and pick the most specific match; `get_category_attributes` for it. Fill required attributes with values from the list.
4. Photos: for each one, `get_upload_link` gives a one-time URL; the seller (or the workspace panel) uploads the file there. Use the returned `upload_id` values in order; the first is the main photo.
5. Write the title, 13 tags and description, then `save_listing_draft` with all fields and the seller's facts in `seller_facts`. It returns `missing` fields and the copy check. Fix both.
6. Show the full listing: category, attributes, price, quantity, profiles, photos in order, personalization, title, tags, description.
7. Ask: save as an Etsy draft (free) or publish now. Publishing makes it public and Etsy charges the seller its listing fee; it uses one action.
8. After an explicit yes: `publish_listing` with `draft_id`, `revision`, `confirm: true` and `activate` true or false.
9. Report the result with the listing link, or the error and hint. If a step failed, calling `publish_listing` again with the same draft continues without creating a second listing.
