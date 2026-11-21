---
name: connect-your-shop
description: Connect the seller's Etsy shop to SEO Etsy by MakeBox AI, check the plan and actions left this month, reconnect after access expired, or disconnect the shop. Use when no shop is connected or a tool reports a connection error.
---

# Connect your Etsy shop

Read [connection, plans and errors](../../references/connection-and-plans.md).

1. `get_account_status`. If `terms_accepted` is false, ask the seller to finish sign-up on the account page shown in the hint.
2. If `shop` is null, or a tool returned `etsy-not-connected` or `etsy-reconnect-required`, call `get_connect_link` and give the seller the link. They open it in a browser where they are signed in to MakeBox and approve access on Etsy. Do not open it yourself. The link works for 15 minutes.
3. After the seller says it is done, call `get_account_status` again and confirm the shop name.

One Etsy shop per account. To disconnect, explain that listings on Etsy stay as they are, get an explicit yes, then `disconnect_shop` with `confirm: true`.
