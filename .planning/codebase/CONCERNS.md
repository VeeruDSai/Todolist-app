# CONCERNS

## Technical risks
- No input validation for user-submitted todo item names.
- `process.env.DATABASE` is assumed present, but missing configuration will cause startup failure.
- The `listSchema` is defined as a plain object instead of a Mongoose schema instance, which can produce inconsistent behavior.
- `body-parser` is used even though Express 4.18 includes built-in body parsing.

## Reliability gaps
- Error handling is minimal; many promise rejections are only logged and do not provide user feedback.
- The app has a single hard-coded server port (`3000`) instead of using `process.env.PORT`.
- MongoDB connection errors are not handled explicitly, so startup failure may be silent.

## Security concerns
- No authentication or authorization exists, so anyone who can access the app may add or delete list items.
- The app allows dynamic route creation via `/:customListName`, which can create unexpected route names and may conflict with fixed routes like `/about`.
- There is no rate limiting, CSRF protection, or sanitization beyond default EJS escaping.

## Maintainability issues
- All application logic lives in `app.js`, which makes the code harder to extend or refactor.
- No dedicated directories for models, controllers, or routes increase technical debt.
- The repository has no automated tests, so future changes may regress behavior silently.
