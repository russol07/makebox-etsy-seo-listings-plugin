# Connection, plans and errors

## Connect

1. Add the connection `https://app.makebox.ai/seo/mcp` and sign in with a MakeBox account (password or Google). The first approval asks the seller to accept the terms and starts on the free MCP Start plan.
2. `get_connect_link` returns a link valid for 15 minutes. The seller opens it in a browser where they are signed in to MakeBox and approves access on Etsy. Do not open it yourself.
3. One Etsy shop per account.

## Actions

- One action = applying SEO changes to a listing, or publishing a new listing.
- MCP Start (free): 5 actions per calendar month (UTC), counted per Etsy shop. MCP Unlimited has no monthly action limit.
- Reading, checking, drafts, Etsy drafts (`activate: false`) and reverts are free.
- If Etsy refuses a write, the action is returned. If the outcome is unknown, it stays used and nothing is retried.
- `get_account_status` shows the plan and actions left. Plan details are on the pricing page in the hint; never send the seller to a payment page from the chat.

## Common errors

| Error | What to tell the seller |
|---|---|
| `terms-not-accepted` | Finish sign-up on the account page. |
| `etsy-not-connected`, `etsy-reconnect-required` | Connect the shop with a new link from `get_connect_link`. |
| `free-allowance-used` | This month's free actions are used; they renew on the 1st (UTC). |
| `draft-revision-mismatch` | The draft changed after review; show it again. |
| `listing-changed-since-draft` | The listing was edited on Etsy; read it again and redo the draft. |
| `listing-draft-incomplete` | Ask for the fields named in `field`. |
| `uncertain: true` | Read the listing first; never retry automatically. |

Every refused call also returns a `hint`. Relay it.
