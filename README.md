# ShramSahyog — Working Demo

A functional, client-only demo of the ShramSahyog cooperative gig platform
(Team ZERO, Smart India Hackathon 2026, SIH26089). No backend, no build step —
plain HTML/CSS/JS, data kept in the browser's `localStorage`.

## What actually works here

- **Find a worker** — customers submit a request; a SmartMatch function ranks
  available workers by skill, city, and rating.
- **Register as worker** — new worker profiles are created and persisted.
- **Worker dashboard** — accept/decline requests, mark jobs completed, see
  rating and total payout.
- **My bookings** — customers look up bookings by phone, pay (UPI/cash, with
  an automatic 5% cooperative fee), and rate the worker.
- **Cooperative admin** — read-only totals: workers, bookings, fund collected.
- **SMS / IVR simulation** — a prompt-based flow standing in for the
  offline/no-smartphone access path described in the pitch.
- **EN / हिं toggle** — swaps key headline strings to demonstrate multilingual UI.

Ten sample workers are seeded on first load so SmartMatch has something to
match against immediately. Use **Reset demo data** on the admin page to start over.

## Run locally

```bash
python3 -m http.server 8000
# visit http://localhost:8000
```
Or just double-click `index.html`.

## Run the smoke test

```bash
npm install
npm test
```
`test.js` drives the whole loop headlessly with jsdom — request → match →
accept → complete → pay → rate → register → admin → SMS simulation → language
toggle — and fails loudly if any step breaks.

## Deploy on GitHub Pages

1. Push this folder to a GitHub repo.
2. Settings → Pages → set source to your branch (root, or `/docs` if you move
   the files there).
3. Live at `https://<username>.github.io/<repo>/`.

## Known limitations (it's a hackathon demo)

- No real backend, auth, or payment gateway — everything lives in
  `localStorage` on one browser.
- "Login" as a worker is just picking your name from a dropdown.
- SMS/IVR is simulated with browser prompts, not a real telephony integration.
