```markdown
# apphosting-adapters Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill covers the core development patterns, coding conventions, and maintenance workflows for the `apphosting-adapters` TypeScript codebase. The repository is organized without a specific framework, focusing on modular TypeScript code, consistent file naming, and streamlined dependency management across multiple packages and starter templates.

## Coding Conventions

**File Naming**
- Use camelCase for file names.
  - Example: `myAdapter.ts`, `userService.test.ts`

**Imports**
- Use relative import paths.
  - Example:
    ```typescript
    import { myFunction } from './utils';
    ```

**Exports**
- Use named exports.
  - Example:
    ```typescript
    export function myFunction() { /* ... */ }
    export const MY_CONST = 42;
    ```

**Commit Patterns**
- Commit messages are freeform, sometimes with prefixes.
- Average commit message length: 64 characters.

## Workflows

### Dependency Update Across Multiple Packages

**Trigger:** When you need to update one or more npm dependencies across all relevant packages and starter templates.

**Command:** `/update-dependencies`

1. Identify outdated dependencies in all `package.json` files.
2. Update the version numbers in `package.json` for each affected package or starter template.
3. Regenerate or update the corresponding `package-lock.json` files.
4. Commit all changed `package.json` and `package-lock.json` files together.

**Files Involved:**
- `*/package.json`
- `*/package-lock.json`
- `packages/*/package.json`
- `starters/*/*/package.json`
- `starters/*/*/package-lock.json`

**Example:**
```bash
# Update a dependency in all packages
npx lerna exec -- npx npm-check-updates -u
# Then update lock files
npx lerna bootstrap
# Commit changes
git add .
git commit -m "chore: update dependencies across packages"
```

## Testing Patterns

- Test files follow the `*.test.*` naming convention.
  - Example: `userService.test.ts`
- The testing framework is not explicitly detected; check individual test files for framework usage.
- Place test files alongside the code they test or in dedicated test directories.

**Example:**
```typescript
// userService.test.ts
import { getUser } from './userService';

test('getUser returns correct user', () => {
  expect(getUser(1)).toEqual({ id: 1, name: 'Alice' });
});
```

## Commands

| Command              | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| /update-dependencies | Update npm dependencies across all packages and starter templates |
```
