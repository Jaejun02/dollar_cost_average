# Contributing Guidelines

Thanks for contributing! To keep the project consistent and maintainable, please follow these guidelines when working with this repository.

---

## Branch Naming Convention

Branches should clearly indicate their purpose. Use **lowercase with hyphens** and prefix by type:

* `feature/<short-description>` – for new features
  *e.g.* `feature/user-authentication`
* `fix/<issue-id>-<short-description>` – for bug fixes
  *e.g.* `fix/123-login-crash`
* `chore/<short-description>` – for maintenance, tooling, or config updates
  *e.g.* `chore/upgrade-dependencies`
* `docs/<short-description>` – for documentation updates
  *e.g.* `docs/update-readme`

💡 Keep branch names short and descriptive. If tied to an issue, include the issue number.

---

## Commit Message Convention

We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) standard.

Each commit message should be structured as:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Allowed `<type>` values:

* **feat**: A new feature
* **fix**: A bug fix
* **docs**: Documentation changes only
* **style**: Code style/formatting (no logic change)
* **refactor**: Code change that neither fixes a bug nor adds a feature
* **perf**: Performance improvement
* **test**: Adding or updating tests
* **chore**: Changes to build process, tooling, or dependencies

### Examples:

* `feat(auth): add OAuth login flow`
* `fix(api): handle null response in user service`
* `docs: update installation instructions`
* `chore(env): add pre-commit configuration`

---

## Developer Setup

We use **conda** to manage dependencies, including developer tools.

1. **Create and activate the environment:**

   ```bash
   conda env create -f environment.yml
   conda activate dca
   ```

   This installs both runtime dependencies (e.g. `pandas`, `numpy`, `polars`) and developer tools (`black`, `ruff`, `pre-commit`, `commitizen`).

2. **Install Git hooks with pre-commit:**

   ```bash
   pre-commit install
   pre-commit install --hook-type commit-msg
   ```

   * **pre-commit** runs Black and Ruff automatically on staged code.
   * **commitizen** checks commit messages against Conventional Commits.

3. **Optional – use Commitizen to guide commit creation:**

   ```bash
   cz commit
   ```

   This provides an interactive prompt to generate a correctly formatted commit message.

---

## Pull Request Guidelines

1. Ensure your branch is **rebased on latest `main`** before opening a PR.
2. Use a **descriptive PR title** (ideally aligned with Conventional Commits).
3. Link related issues in the PR description (*e.g.* “Closes #123”).
4. Make sure tests/docs are updated if applicable.

---

## Code Style

* **Black** is used for formatting with a maximum line length of **100 characters** (overriding the default of 88).
* **Ruff** is used for linting and import sorting, also set to a maximum line length of **100 characters**.
* These are automatically run via pre-commit hooks on commit.
* You can also run them manually:

  ```bash
  black .
  ruff check . --fix
  ```

---

## Enforcement

* Commits with invalid messages will be **blocked** by the `commit-msg` hook.
* Commits with code that fails Black or Ruff will also be blocked until fixed.
* This ensures the codebase and history remain consistent for all contributors.