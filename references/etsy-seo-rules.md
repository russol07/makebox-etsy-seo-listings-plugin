# Etsy SEO rules

The same rules the service checks in `check_listing_seo` and `get_seo_brief`. Errors block saving to Etsy; the rest is advice.

## Etsy's limits (errors)

- Title: at most 140 characters; letters, numbers, punctuation, ™ © ®. The characters `%`, `:`, `&` and `+` at most once each.
- Tags: at most 13, each at most 20 characters; letters, numbers, spaces, `-` and `'` only; no duplicates.
- Materials: letters, numbers and spaces only. Styles: at most 2, each at most 45 characters.
- Description: not empty.

## What the checker also blocks

- A tag that names a different material, product form or delivery type than the listing (for example "digital download" on a physical sign).
- A claim no one stated: waterproof, dishwasher safe, gift box included, free shipping, warranty, licence and similar. If it is true, the seller says so and you put it in `seller_facts`.

## Good copy (advice)

- Title: 80 to 140 characters, at most 16 words. Name the item first, then confirmed traits: material, colour, size, style, recipient. No sales words.
- Tags: exactly 13, each 2 to 3 words. Put the main search phrase in the title too. Keep the seller's tags that still fit.
- Description: 120+ words in 3+ blocks separated by blank lines: what the item is (main phrase in the first sentence), key details, then size, options and use.

## Never

- Invent facts, prices, reviews or results.
- Use another shop's listings, tags or images as a source.
- Promise views, ranking or sales.
