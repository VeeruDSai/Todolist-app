# STRUCTURE

## Root files
- `app.js` — main application entrypoint; configures Express, connects to MongoDB, defines routes, and starts the server.
- `package.json` — dependency manifest and npm lifecycle scripts.
- `README.md` — project overview, install/run instructions, and contribution notes.
- `LICENSE` — open source license text.

## Views
- `views/list.ejs` — main todo list page template.
- `views/about.ejs` — about page template.
- `views/header.ejs` / `views/footer.ejs` — reusable layout partials included by other views.

## Static assets
- `public/css/styles.css` — styling for the application.

## Missing or implied structure
- No dedicated `routes/`, `models/`, or `controllers/` directories.
- No `config/` folder; configuration is loaded inline from `config.env` with `dotenv`.
- No test suite or `tests/` directory.

## Deployment / config hints
- `app.js` reads `DATABASE` from `process.env`.
- A `config.env` file is expected but is not present in the repository snapshot.
