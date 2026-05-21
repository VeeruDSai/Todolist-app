# TESTING

## Current state
- No automated tests exist in the repository.
- `package.json` includes only a placeholder `test` script: `echo "Error: no test specified" && exit 1`.

## Manual verification
- App behavior is currently validated by running the server and exercising the UI:
  - add items on the home list
  - create custom lists by name via the URL
  - delete items using the checkbox
  - view the About page
- Database behavior is verified through MongoDB inserts, finds, and deletes.

## Recommended test coverage
- Unit tests for data models and schema validation.
- Integration tests for route behavior:
  - GET `/` returns the Today list
  - POST `/` adds items to default and custom lists
  - POST `/delete` removes items correctly
  - GET `/:customListName` creates and loads custom lists
- End-to-end tests to confirm template rendering and page flows.

## Suggested tooling
- `jest` or `mocha` for JavaScript testing
- `supertest` for Express route integration tests
- `mongodb-memory-server` for fast database-backed test runs
- Optionally `eslint` and `prettier` to enforce consistency as tests are added
