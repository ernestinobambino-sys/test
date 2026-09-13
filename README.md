# Command Deck

A **private** personal life dashboard — one page for your email, projects, finances,
tasks, health, and a searchable memory vault so nothing about your work ever gets lost.

- **Live page (private to your account):**
  https://claude.ai/code/artifact/8730ace5-d84e-4f6a-8f7b-a3eb63818f4f
- Open it on your phone or laptop with that one link. Nobody else can see it.
- `dashboard.html` in this repo is the complete source — a single self-contained file.

## Panels

| Panel | What it does | Source |
|-------|--------------|--------|
| **Today** | Add / check off / clear daily tasks | Saved in the deck (private) |
| **Inbox** | Recent + unread email, one click into Gmail | Live — your Gmail connector |
| **Finances** | Income / expenses you log + a running balance line | Saved in the deck |
| **Projects & Build Memory** | Every app/site you're building, with status & notes | Saved in the deck |
| **Health** | Water, sleep, mood, and a week-logged strip | Saved in the deck |
| **Memory Vault** | Searchable notes, logins, decisions, ideas (#tags) | Saved in the deck |
| **Ask the Deck** | Ask Claude to brief your day / summarise your inbox | Your Claude account |
| **Notion** | Live search of your Notion workspace | Live — your Notion connector |
| **Drive** | Recent Google Drive files, quick-open | Live — your Drive connector |
| **Creative Studio** | Recent Higgsfield generations + credits left | Live — your Higgsfield connector |

Everything you type is stored per-account and survives reloads. Live panels use *your own*
connected accounts in claude.ai — no API keys or tokens live in the page.

## Honest limits

- **No live bank balances.** There's no bank connector, so Finances tracks what you log
  (plus live Shopify revenue once that's wired — see below). It is not an automatic bank feed.
- **Shopify revenue is pending.** The Shopify connector's token was expired when this was
  built, so its live shape couldn't be verified yet. Reconnect Shopify in
  claude.ai → Settings → Connectors and it can be folded into Finances as a quick follow-up.
- **Higgsfield thumbnails aren't shown inline** (the artifact security policy blocks external
  images); Creative Studio lists each generation with an "open" link instead.
- It's hosted **privately on claude.ai**, not physically on your PC. This file is the path to
  self-hosting later.

## Self-hosting later

`dashboard.html` opens in any browser as a static file, but its live features
(saved data, connectors, Ask) run on claude.ai's artifact runtime via `window.claude`.
To run it fully on your own machine you'd replace those three pieces with your own backend:

- **Saved data** (`claude.use("db")`) → your own database or local storage.
- **Live connectors** (`claude.use("mcp")`) → your own OAuth apps for Gmail / Notion / Drive.
- **Ask** (`claude.use("sample")`) → your own call to the Claude API.

The UI, layout, and panel logic all carry over unchanged.
