# CONVENTIONS

## Current patterns
- Uses CommonJS `require()` imports in `app.js`.
- Consistent use of `const` for module imports and unchanging values.
- EJS is used for all view rendering with simple HTML templates and partial includes.
- Route handlers are written as inline anonymous functions.

## Naming and style
- Variable names use camelCase (`itemSchema`, `customListName`, `defaultItems`).
- Mongoose models are named `Item` and `List`, matching their document responsibility.
- Route paths are clear and REST-adjacent: `/`, `/delete`, and dynamic `/:customListName`.

## Observations and gaps
- No linting or formatter is present; code style is maintained manually.
- `listSchema` is declared as a plain object, not a `new mongoose.Schema(...)` instance, which is inconsistent with the `itemSchema` definition.
- There is no centralized application structure; all app logic is in `app.js`.
- The codebase relies on inline comments rather than formal documentation inside code.
