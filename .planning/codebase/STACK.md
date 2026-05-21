# STACK

## Runtime
- Node.js (JavaScript runtime)
- Express 4.18.2 web framework
- EJS templating engine for server-side views

## Application libraries
- `express` for HTTP routing and middleware
- `dotenv` for environment variable loading from `config.env`
- `body-parser` for parsing URL-encoded POST bodies
- `mongoose` for MongoDB object modeling
- `lodash` for utility functions and string capitalization
- `ejs` for view rendering

## Database
- MongoDB via Mongoose
- Primary deployment path uses `process.env.DATABASE` for a MongoDB Atlas connection
- Local development path is supported through a commented `mongoose.connect("mongodb://127.0.0.1:27017/todolistDB")`

## Runtime behavior
- Server listens on port `3000`
- Static assets served from `public/`
- Views rendered from `views/` using EJS partials (`header.ejs`, `footer.ejs`)

## Notes
- This is a classic Node/Express monolith with server-side rendered pages and database-backed state.
- No frontend build step is present; static assets are plain CSS and served directly.
