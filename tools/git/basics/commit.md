# Common Commit Message Prefixes

**disclaimer**

this file was made by copilot under my instructions

## 🔧 Core, widely used prefixes
These cover 95% of everyday development work.

| Prefix | Meaning | Example |
|--------|---------|---------|
| **feat:** | A new feature | `feat: add user profile page` |
| **fix:** | A bug fix | `fix: correct null pointer crash` |
| **docs:** | Documentation changes | `docs: update API usage examples` |
| **style:** | Formatting, no logic changes | `style: reformat code with Prettier` |
| **refactor:** | Code changes that aren’t features or fixes | `refactor: simplify auth middleware` |
| **test:** | Adding or updating tests | `test: add unit tests for login flow` |
| **chore:** | Maintenance tasks, tooling, configs | `chore: update dependencies` |
| **perf:** | Performance improvements | `perf: optimize image loading` |
| **build:** | Build system or CI changes | `build: fix Dockerfile path` |
| **ci:** | Continuous integration changes | `ci: update GitHub Actions workflow` |

## 🧩 Optional but useful prefixes
These help when your workflow gets more complex.

| Prefix | Meaning | Example |
|--------|---------|---------|
| **revert:** | Reverts a previous commit | `revert: undo feature flag change` |
| **security:** | Security-related fixes | `security: patch XSS vulnerability` |
| **deps:** | Dependency updates (alternative to chore) | `deps: bump axios to 1.7.0` |
| **wip:** | Work in progress (avoid on main branches) | `wip: initial layout for dashboard` |

## 🎯 Tips for using prefixes well
- Keep the **prefix lowercase** and followed by a colon.
- Write commit messages in the **imperative mood** (“add”, not “added”).
- Keep the subject line short; add details in the body if needed.
- Be consistent—pick a set and stick to it.
