# Contributing to MediBook

Thank you for your interest in contributing! This guide explains how to get involved.

## Getting Started

1. **Fork** the repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/your-username/medibook.git
   cd medibook
   ```
3. Follow the [README setup instructions](README.md#-getting-started) to run both backend and frontend

## Branching Strategy

| Branch | Purpose |
|---|---|
| `main` | Production-ready code |
| `develop` | Integration branch for features |
| `feature/*` | New features |
| `fix/*` | Bug fixes |
| `docs/*` | Documentation only |

Always branch from `develop`, not `main`.

```bash
git checkout develop
git pull origin develop
git checkout -b feature/your-feature-name
```

## Commit Message Format

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add doctor search by specialty
fix: resolve time slot double-booking race condition
docs: update API endpoint table in README
refactor: extract booking validation to separate method
test: add unit tests for AppointmentService
```

## Pull Request Process

1. Ensure all existing tests pass
2. Add tests for new functionality where applicable
3. Update `README.md` if you change any setup steps or API endpoints
4. Submit your PR against the `develop` branch
5. Fill out the PR template completely
6. Request a review from a maintainer

## Code Style

### Backend (C#)
- Follow [Microsoft C# coding conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- Use `async/await` consistently for all database operations
- Keep controllers thin — logic belongs in services
- All public methods on interfaces/services should have XML doc comments

### Frontend (Angular/TypeScript)
- Use standalone components (no NgModules)
- Prefer `inject()` function over constructor injection in new components
- Use `AsyncPipe` in templates rather than `.subscribe()` where possible
- Follow the Angular style guide naming conventions

## Reporting Bugs

Open an issue and include:
- Steps to reproduce
- Expected vs actual behaviour
- Browser/OS/framework versions
- Any relevant console errors or logs

## Suggesting Features

Open an issue with the `enhancement` label. Describe:
- The problem it solves
- Proposed solution
- Any alternatives considered
