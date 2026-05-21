# ARCHITECTURE

## High-level architecture
- Single-process Express application in `app.js`.
- Uses server-side rendering with EJS templates.
- Application logic, routing, and data models reside in one file rather than separated layers.

## Logical layers
- Presentation: `views/` contains EJS templates (`list.ejs`, `about.ejs`) and shared partials (`header.ejs`, `footer.ejs`).
- Routing / controllers: Express route handlers in `app.js` manage page rendering, form submission, deletion, and custom list creation.
- Data persistence: Mongoose models handle MongoDB collections.

## Data model
- `Item` model: stores individual todo items with a single `name` field.
- `List` model: stores named custom lists, each with an array of `Item` objects.
- Default items are created and inserted when the database is empty.

## Request flow
1. User requests `/` or `/:customListName`.
2. App queries MongoDB for existing items or list documents.
3. App either inserts defaults, creates a new list, or renders the found list.
4. POST `/` creates a new item in the default list or a custom list.
5. POST `/delete` removes an item from the default list or a custom list.

## Architectural characteristics
- Monolithic: routing, data access, and business logic are co-located.
- Stateful persistence via MongoDB.
- Simple page-based UX without SPAs or client-side JavaScript beyond basic form submission.
