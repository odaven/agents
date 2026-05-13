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
- Commit messages follow Conventional Commits: `type(scope): description` or `type: description`
  - `feat:` `fix:` `docs:` `style:` `refactor:` `perf:` `test:` `build:` `ci:` `chore:` `revert:`
  - Example: `feat(auth): add JWT validation`, `fix(api): handle null responses`
- PR titles follow Conventional Commits style.
- Don't merge PRs without explicit instruction.
- Don't close issues without explicit instruction.
- Don't rewrite shared history unless explicitly requested.
- Don't force push unless explicitly requested.

---

## Testing

- Prefix test names with a number: `"1. should return active users"`, `"2. should return empty when ..."`
- Keep numbering sequential; update when inserting, removing, or reordering.
- Assert complete objects, not individual fields.

---

## TypeScript

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
