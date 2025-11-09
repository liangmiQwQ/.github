# Contributing Guide

Thank you! We are so excited that you are interested in our project and would like to contribute. Before starting your contribution, please take a moment to read the following tips to save time.

## Before Contributing

Before opening an issue or submitting a pull request, please make sure your problem description is clear and includes necessary steps to reproduce, expected behavior, and actual results.

Please check existing issues and pull requests to avoid duplicates. Use the search function to see if similar topics have been discussed before.

For new feature proposals, please open an Issue or start a Discussion first to gather feedback from maintainers and the community before implementing.

## Setup Project

If you're new to Git and GitHub, we recommend familiarizing yourself with basic concepts like forking, cloning, committing, and pushing. [GitHub's documentation](https://docs.github.com/) provides excellent guides for beginners.

- Create a new branch for your feature or bugfix: `git checkout -b feat/your-feature-name`
- Keep your branch updated with the main branch: `git fetch origin && git rebase origin/main`
- Use descriptive branch names that reflect the purpose of your changes

We follow conventional commit standards. Each commit message should be structured as:
```
<type>(<scope(optional)>): <description>
```

### JavaScript Projects

Project dependencies generally use pnpm, rarely use bun or npm. We recommend using `@antfu/ni` to handle dependencies to avoid using the wrong package manager, and enable corepack.

```bash
# Enable corepack (if not already enabled)
corepack enable

# Install @antfu/ni
npm install -g @antfu/ni

# Install dependencies
ni

# Run development server
nr dev

# Run tests
nr test
```

If the project uses pnpm-workspace, we recommend using catalogs to manage dependencies, ensuring accurate separation between `dependencies` and `devDependencies`

- Production dependencies should be in `dependencies`
- Development dependencies should be in `devDependencies`
- Use workspace protocol for local packages: `"package-name": "workspace:*"`

Typically use ESLint for code formatting and code checking; some projects use Oxlint + Oxfmt / Dprint / Prettier

- Run linting: `nr lint` or `nr lint:fix`
- Ensure your code passes all lint checks before submitting

### Other Projects

**Java Projects:**
- Typically use Gradle for build management
- Do not modify project configuration files or wrappers unless absolutely necessary
- If the project doesn't have a configured formatter, follow editorconfig (if it exists)

**Rust Projects:**
- Ensure code passes clippy checks: `cargo clippy -- -D warnings`
- Format with cargo: `cargo fmt --check`
- Ensure all tests pass: `cargo test`

**Other Languages:**
- Follow the existing project structure and conventions
- Use the established build tools and formatters for that project
- Maintain consistency with the existing codebase

## Creating Pull Request

We will review your PR and ensure CI passes (if available)

Before submitting your pull request:

1. Ensure all tests pass
2. Verify code meets linting standards
3. Update documentation if necessary
4. Add tests for new functionality

We typically use squash and merge to keep the commit history clean. Please ensure your PR contains logically grouped changes.

Your PR title should follow [conventional commit format](https://www.conventionalcommits.org/en/v1.0.0/), for example:
- `feat: add user authentication`
- `fix: resolve memory leak in data processor`
- `docs: update API documentation`

If your PR hasn't been reviewed within two weeks, please:
- Mention relevant maintainers using `@liangmimi`
- Or contact us at `github@liangmi.dev`

## Possible Follow-up Actions

If reviewers request changes:
1. Convert your PR to a draft: This indicates it's not ready for review
2. Make the requested changes
3. Convert back to "Ready for Review" when done

You can push additional commits to your existing branch - there's no need to create a new pull request. We'll see your updates automatically.

Thank you for contributing! 🎉
