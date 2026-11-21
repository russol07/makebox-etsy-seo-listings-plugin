# Creating a listing

Physical listings only. Digital downloads are created in Etsy Shop Manager.

## What Etsy needs

| Field | Where it comes from |
|---|---|
| Category (`taxonomy_id`) | `search_categories`; the most specific match |
| Required attributes | `get_category_attributes`; values from its list |
| Price, quantity | the seller; price in the shop currency, quantity 1 to 999 |
| Who made it, when | the seller: `i_did`, `someone_else` or `collective`; `made_to_order` or an era such as `2020_2026` |
| Shipping profile | `get_listing_requirements` |
| Processing profile | `get_listing_requirements`; Etsy refuses physical listings without one |
| Weight and size | needed when the shipping profile calculates rates |
| Photos | at least one to publish; up to 20; JPEG, PNG or GIF up to 10 MB each |

`save_listing_draft` lists what is still `missing`. `publish_listing` also checks the category's required attributes and the shipping profile type before it writes anything.

## Personalization

One text question for the buyer (`question`, optional `instructions`, `required`, `max_characters`). The service uses Etsy's current personalization endpoint.

## Publishing

- `activate: false` saves an Etsy draft. It is free and the seller can finish it in Shop Manager, or call `publish_listing` again with `activate: true` later.
- `activate: true` makes the listing public. Etsy charges the seller its listing fee, and it uses one action.
- After an error, call `publish_listing` again with the same draft: finished steps are not repeated. When the result is `uncertain`, check Etsy before anything else.
