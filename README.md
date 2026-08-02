# CareBridge — Prototype

A clickable frontend prototype for CareBridge: an app that helps a remote caregiver (Arjun)
manage his parent's medical records across multiple doctors, verify AI-extracted readings,
and generate two kinds of briefings — one for the doctor, one for whoever's in the room.

This is a **prototype**: there is no real backend, database, or auth. All data lives in
`lib/mockData.ts` and any "confirm" or "edit" action just updates local React state.

## Stack

- Next.js 16 (App Router) + TypeScript
- Tailwind CSS v4 (theme tokens in `app/globals.css`)
- lucide-react icons
- Fonts via `next/font/google`: Source Serif 4 (display), Inter (body), IBM Plex Mono (data)

## Run locally

```bash
npm install
npm run dev
```

Open http://localhost:3000 — it starts at the Welcome screen, then "Continue as Arjun" → Dashboard.

## Project structure

```
app/
  page.tsx                    Welcome screen
  (app)/layout.tsx            Shared sidebar shell
  (app)/dashboard/            Main dashboard — the centerpiece
  (app)/organ/[id]/           Organ detail + record verification
  (app)/specialist/           Specialists list
  (app)/specialist/[id]/      Doctor Briefing / What to Mention toggle
  (app)/vault, calendar,
        family, emergency-id/ Baseline feature stubs
components/                   Reusable UI (OrganCard, ReviewQueue, RippleAlertBanner, etc.)
lib/mockData.ts                All mock data for the prototype
```

## Deploy to Vercel

1. Push this folder to a new GitHub repo.
2. Go to https://vercel.com → **Add New Project** → import the repo.
3. Keep all default settings (Vercel auto-detects Next.js) → **Deploy**.
4. Your live URL will be ready in ~1 minute — no environment variables needed.

Or, from the CLI, inside this folder:

```bash
npx vercel
```

## Design tokens

Colors (in `app/globals.css`, from the provided palette image):

| Token | Hex | Use |
|---|---|---|
| `sage-deep` | `#659287` | Nav, headings, primary buttons |
| `sage` | `#88BDA4` | Secondary accents |
| `mint-soft` | `#B1D3B9` | Borders, card backgrounds |
| `mint-pale` | `#E6F2DD` | Page background |
| `amber` | `#D98E4A` | Reserved for things needing attention (Verify button, alerts) |
