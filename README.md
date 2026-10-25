# Crave AI Agent — Official WhatsApp AI Agent

**Crave Productions Pvt Ltd** — Premium Bakery & Custom Cake Shop, Katugastota, Sri Lanka.

Contact: `wa.me/94702888052` · craveproductions917@gmail.com

---

## What this is

A WhatsApp AI agent (built on [Baileys](https://github.com/WhiskeySockets/Baileys) +
OpenRouter/DeepSeek) that represents Crave Productions to customers on WhatsApp.

- **Crave Assistant** — the AI persona. Replies in warm, natural Sinhala,
  answers questions about the bakery, gathers order details (occasion,
  flavour, size, delivery date/address), and *never quotes prices* — it
  always tells the customer a team member will follow up with pricing.
- This is a pure customer-support chat agent, not a command-menu bot —
  every message a customer sends goes straight to the AI, there is no
  `.menu` / command system for customers.
- The `/settings` page lets the owner (after logging in with the
  phone/password sent to their own WhatsApp when the bot first connects)
  add extra business notes for the AI (menu, delivery areas, hours, bank
  details) and manage a cake catalog (name + description + photo) — when a
  customer asks about a cake by name, the bot sends that photo automatically.
- The `/` pairing page is gated behind a private access code — only staff
  who know the code can create a new WhatsApp session.

## Setup

1. `npm install`
2. Set your own environment variables (see below) on your host.
3. `npm start`, open the pairing page, enter the access code, and scan the
   QR with the Crave Productions WhatsApp number.

### Key environment variables
- `OWNER_NUMBER` — defaults to `94702888052` (Crave hotline)
- `ADMIN_PASSWORD` — internal admin API password; set your own in production
- `PAIR_ACCESS_CODE` — the code required to pair a new WhatsApp session on
  the `/` page; set your own in production
- `OPENROUTER_API_KEY` / `OPENROUTER_MODEL` — powers Crave Assistant

## Editing the AI's business knowledge

Two ways:
1. **`/settings` page** (recommended, no code needed) — log in as the owner
   and use "AI System Prompt — Extra Business Notes" and "Cake Catalog".
2. **Code** — open `index.js` and find `callCraveAI` — the `systemPrompt`
   string there is the AI's core behaviour (tone, the "no prices" rule).
