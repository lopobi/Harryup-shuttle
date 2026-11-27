# Harry Up Shuttle Contracts

One-page site with three views (switch with the top tabs or URL hash):

- `#passenger` – Passenger's Contract / Travel Agreement (details, luggage list, next of kin, signature)
- `#driver` – Driver's Contract / Employment Agreement (details, signature)
- `#admin` – lists signed contracts; admins can countersign driver contracts and delete entries

## Files
- `index.html` – the whole site (HTML, CSS and JS in one file)
- `reference/` – the original paper contracts the forms are based on

## Important: storage
Saving and the admin list use the Claude artifact database (`window.claude.use("db")` and `use("user")`).
That only exists when the page is opened as the published Claude artifact. If you open `index.html`
directly or host it elsewhere, the forms display but submitting shows a "need to be signed in" error.
To host it yourself, replace the `getDb()` / `getUser()` calls with your own backend
(e.g. a REST API with Spring Boot, Firebase, or Supabase) that stores each submission and checks admin login.
