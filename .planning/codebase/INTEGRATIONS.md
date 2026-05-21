# INTEGRATIONS

## Database integration
- Uses Mongoose to connect to MongoDB.
- Primary connection string is read from environment variable `DATABASE`.
- Local development is expected to use MongoDB running at `mongodb://127.0.0.1:27017/todolistDB` when uncommented.

## External services
- No external third-party APIs are consumed in the codebase.
- The only external dependency is the MongoDB database service.

## Frontend integration
- Express serves static files from `public/`.
- Server-side EJS templates in `views/` compose the HTML pages.
- `list.ejs` renders dynamic task lists and a form for adding items.

## Deployment notes
- The README references a render.com deployment URL, suggesting this app has been deployed as a simple Node/Mongo app.
- Environment-dependent startup is required for production due to database credentials in `config.env`.
