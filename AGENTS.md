# Personal AGENTS.md

## Communication

- Be concise. Cut to the substantive part, avoid fluff.
- Assume competence. Don't explain obvious things or adopt a patronizing tone.
- Offer alternatives when a better approach exists.

---

## Git

- Never push directly to `main`, `master`, or `develop`.
- Branch names: `feat/add-user-search`, `fix/null-pointer-on-login`, `refactor/simplify-cache`
- One logical change per commit. Don't mix refactoring with functional changes.
- Use Conventional Commits for commit messages and PR titles: `type(scope): description` or `type: description`
  - Example: `feat(auth): add JWT validation`, `fix(api): handle null responses`
- Never merge PRs or close issues without explicit instruction.
- Never rewrite shared history or force-push unless explicitly requested.

---

## Testing

- Prefix test names with a number: `"1. should return active users"`, `"2. should return empty when ..."`
- Keep numbering sequential; update when inserting, removing, or reordering.
- Assert complete objects, not individual fields.

---

## Scope and Change Management

- Change only what was requested.
- Stop immediately when explicitly asked to stop.
- Ask before expanding scope.
- Don’t fix unrelated failures to force green tests.
- Don’t refactor beyond what the request requires.

---

## TypeScript

- Prefer optional chaining (`?.`) for null-safe property and method access.  
  Don’t mix `obj?.x` with `obj.x && ...` in the same access path:

  ```typescript
  // Good
  const includesPattern = obj?.field?.includes("pattern");

  // Bad
  const includesPattern = obj?.field && obj.field.includes("pattern");
  ```

- Use dot notation for field access. Bracket notation only for dynamic keys or special characters:

  ```ts
  // Good
  user.name;
  obj[dynamicKey];

  // Bad
  user["name"];
  ```

- Always use curly braces for control flow blocks, even single-line:

  ```ts
  // Good
  if (condition) {
    doSomething();
  }

  // Bad
  if (condition) doSomething();
  ```

- Use a named options object for functions with 3+ parameters:

  ```ts
  type GetUserOptions = { userId: string; includeProfile: boolean; locale: string };
  async function getUser(options: GetUserOptions): Promise<User> { ... }
  ```

- Inline `Promise.all` calls when they're simple and readable. Extract to named variables when calls have many arguments or are hard to read inline.
- File order: constants → exports → private helpers (in order of first use).
- Mirror source structure for test files: `src/users/service.ts` → `test/users/service.test.ts`
