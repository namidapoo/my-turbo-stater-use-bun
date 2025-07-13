# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Language Preferences

- Regardless of the input language, please provide the output in Japanese.

## Commit Message Guidelines

- Please add a prefix to your commit messages using conventional commit format:
  - `feat:` for new features
  - `fix:` for bug fixes
  - `docs:` for documentation changes
  - `style:` for formatting changes (no code logic change)
  - `refactor:` for code restructuring
  - `test:` for test additions/modifications
  - `chore:` for maintenance tasks
  - `ci:` for CI/CD related changes

## Project Overview

This is a Turborepo monorepo using Bun as the package manager. The project consists of:

- Two Next.js applications (`web` and `docs`)
- A shared UI component library (`@repo/ui`)
- Shared TypeScript configurations (`@repo/typescript-config`)

## Common Commands

All commands should be run from the root directory:

### Development

```bash
# Start all apps in development mode
bun dev

# Start a specific app
bun dev --filter=web
bun dev --filter=docs
```

### Build

```bash
# Build all apps and packages
bun run build

# Build a specific app
bun run build --filter=web
```

### Code Quality

```bash
# Run type checking across all packages
bun check-types

# Format code (uses Biome for TS/JS and Prettier for other files)
bun format

# Run linting
bun lint

# Run complete check (format + lint)
bun check

# Format from root directory (affects all files)
bun format:root
```

### Git Hooks

The project uses Lefthook for pre-commit hooks that automatically run:

- Biome formatting and linting
- Prettier formatting for non-JS/TS files

## Architecture

### Monorepo Structure

- `/apps/web` - Main web application (Next.js, port 3000)
- `/apps/docs` - Documentation site (Next.js, port 3001)
- `/packages/ui` - Shared React component library
- `/packages/typescript-config` - Shared TypeScript configurations

### Key Technologies

- **Build System**: Turborepo with dependency-aware task running
- **Package Manager**: Bun (enforced via preinstall script)
- **Framework**: Next.js 15 with App Router and Turbopack
- **Language**: TypeScript with strict type checking
- **Code Quality**: Biome for linting/formatting JS/TS, Prettier for other files
- **React**: Version 19.1.0

### CI/CD Workflows

- `code-quality.yml` - Runs Biome checks on push and PRs
- `claude.yml` and `claude-code-review.yml` - Claude AI integration for code review
- `auto-assign.yml` - Automatically assigns reviewers to PRs
- `approve-me.yml` - Auto-approval workflow

### Development Notes

- Each package has its own `biome.jsonc` configuration
- The root `biome.jsonc` uses tab indentation and double quotes
- TypeScript `noEmit` is used for type checking without generating output files
- All packages use ES modules (`"type": "module"`)
