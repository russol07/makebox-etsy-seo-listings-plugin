---
name: optimize-listing-seo
description: Improve the SEO of one existing Etsy listing in the seller's connected shop - title, 13 tags, description, materials and styles - from real facts, check it, show the before/after and apply it only after approval. Also writes copy-ready SEO when no connection is available.
---

# Improve listing SEO

Read [Etsy SEO rules](../../references/etsy-seo-rules.md) first.

## Without a connection

Ask the seller to paste the current title, tags and description. Write the improved version, check it against the rules by hand, and show it as copy-ready text with what changed and why. Do not claim anything was saved.

## Connected

1. Find the listing: `list_listings` (optionally `search` by a word in the title), then `get_listing`.
2. `get_seo_brief` for the rules, the current check, Etsy's suggested title, tag ideas from the seller's own shop and the facts the listing does not state.
3. Ask only for facts that would change the copy (material, size, who it is for, what is included). Write them into `seller_facts` exactly as the seller said them.
4. Write the new title, tags and description. Keep everything true; keep the seller's specifications.
5. `check_listing_seo` with `listing_id`. Fix every error; consider the advice.
6. `save_seo_draft` with only the fields you change. Show the returned before/after and the check.
7. After an explicit yes for exactly this draft: `apply_seo_changes` with `draft_id`, `revision`, `confirm: true`. It uses one action.
8. Report the result: `applied` (and whether Etsy confirmed it on the control read), `blocked` with the check, or the error and hint.

If the listing changed on Etsy after the draft (`listing-changed-since-draft`), read it again and redo the draft. Every applied change is in `list_changes` for 30 days; `revert_change` puts the old values back (free, after the seller's yes).
