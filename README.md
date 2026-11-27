# Harry Up Shuttle Contracts

One-page site with three views (switch with the top tabs or URL hash):

- `#passenger` – Passenger's Contract / Travel Agreement (details, luggage list, next of kin, signature)
- `#driver` – Driver's Contract / Employment Agreement (details, signature)
- `#admin` – lists signed contracts; admins can countersign driver contracts and delete entries

## Files
- `index.html` – the whole site (HTML, CSS and JS in one file)
- `reference/` – the original paper contracts the forms are based on

## Storage
`createLocalStore()` in `index.html` saves contracts in the browser's `localStorage` (keys `harryup:passengers`, `harryup:drivers`).
It is used automatically when the Claude artifact database (`window.claude.use("db")`) isn't available, e.g. when you open `index.html` directly or host it anywhere.

Limits of browser storage:
- Data lives only in that browser on that device. Contracts signed on a customer's phone will NOT show up on the admin's computer.
- The Admin page has no login in this mode; anyone opening `#admin` on that browser sees the data.
- About 5 MB total; each signature is a small PNG, so hundreds of contracts fit.

For shared storage across devices, swap `getDb()` / `getUser()` for a real backend (Spring Boot REST API, Firebase, Supabase).
