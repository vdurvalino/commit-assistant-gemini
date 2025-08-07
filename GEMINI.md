# Instructions for Generating Commits

When generating commit messages, strictly follow the rules below.

## Conventional Commits Standard

-   Always use the *Conventional Commits* standard.
-   The language for all commit messages must be **English**.
-   Avoid overly wordy descriptions or unnecessary details.

### Commit Structure

The final commit structure should be as follows:

```txt
<type>: <description>

[optional body]
```

### Generation Rules

1.  **`<type>` (Type):** The type must be one of the following, in lowercase:
*   `feat`: For new features.
*   `fix`: For bug fixes.
*   `docs`: For documentation changes.
*   `style`: For changes that do not affect the meaning of the code (whitespace, formatting, etc.).
*   `refactor`: For code refactoring that neither fixes a bug nor adds a feature.
*   `perf`: For a code change that improves performance.
*   `test`: For adding missing tests or correcting existing tests.
*   `chore`: For changes to build processes or auxiliary tools and libraries, such as documentation generation.

2.  **`<description>` (Description):** 
*   The description must be a concise summary of the change.
*   Start with a lowercase letter.
*   Begin with a short phrase in the imperative mood.
*   Do not end with a period.  
*   The description must be no longer than 70 characters.

3.  **`[optional body]` (Optional Body):**
*   **DO NOT** add a body for small and obvious changes that modify few lines of code.
*   Add a body **ONLY** if the change has logical complexity that requires more details. The body should explain the "why" of the change, not the "how".
*   If adding a `body`, leave a blank line between the `description` and the `body`.

4.  **Scope:**
*   **DO NOT** add a scope to the commit type.

5. **Output:**
* The final response must be **only the commit text**, with no additional comments.

### Output Example

The final output should be similar to this example:

```txt
feat: add an icon for the system users label in the Users.tsx component
```

Or, if a body is required:

```txt
refactor: Simplify tax calculation logic in the billing module

The previous logic was tightly coupled and difficult to test. The new implementation separates responsibilities into smaller, cleaner functions, improving maintainability.
```