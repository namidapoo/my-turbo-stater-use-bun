# My Turbo Starter with Bun

A modern monorepo starter template powered by Turborepo and Bun, featuring Next.js applications with shared components and configurations.

## Language

- [Japanese README](./README.ja.md)

## Features

- **Monorepo Architecture**: Powered by Turborepo for efficient task orchestration
- **Bun Package Manager**: Fast, modern JavaScript runtime and package manager
- **Next.js 15**: Latest version with App Router and Turbopack
- **Shared Components**: Reusable UI component library
- **TypeScript**: Full type safety across all packages
- **Code Quality**: Biome for fast linting and formatting, Prettier for other files
- **Git Hooks**: Automated code quality checks with Lefthook
- **CI/CD**: GitHub Actions workflows for quality checks and reviews

## What's Inside?

This monorepo includes the following packages and apps:

### Apps

- `web`: Main web application (Next.js) - http://localhost:3000
- `docs`: Documentation site (Next.js) - http://localhost:3001

### Packages

- `@repo/ui`: Shared React component library
- `@repo/typescript-config`: Shared TypeScript configurations

## Prerequisites

- [Bun](https://bun.sh/) >= 1.2.18
- Node.js >= 18

## Getting Started

1. Clone the repository:

```bash
git clone <repository-url>
cd my-turbo-stater-use-bun
```

2. Install dependencies:

```bash
bun install
```

3. Start development:

```bash
bun dev
```

## Common Commands

Run these commands from the root directory:

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
bun run build --filter=docs
```

### Code Quality

```bash
# Run type checking
bun check-types

# Format all code
bun format

# Run linting
bun lint

# Run complete check (format + lint)
bun check

# Format from root directory (affects all files)
bun format:root
```

## Project Structure

```
my-turbo-stater-use-bun/
├── apps/
│   ├── web/         # Main web application
│   └── docs/        # Documentation site
├── packages/
│   ├── ui/          # Shared component library
│   └── typescript-config/  # Shared TypeScript configurations
├── biome.jsonc      # Biome configuration
├── lefthook.yml     # Git hooks configuration
├── turbo.json       # Turborepo configuration
└── package.json     # Root package configuration
```

## Configuration

### Biome

This project uses Biome for JavaScript/TypeScript linting and formatting. Configuration is in `biome.jsonc`.

### Prettier

Prettier is used for formatting non-JS/TS files (JSON, YAML, Markdown, etc.).

### TypeScript

Each package has its own `tsconfig.json` extending from shared configurations in `@repo/typescript-config`.

### Git Hooks

Pre-commit hooks are configured with Lefthook to ensure code quality:

- Biome formatting and linting for JS/TS files
- Prettier formatting for other files

## Contributing

1. Create a feature branch
2. Make your changes
3. Ensure all checks pass: `bun check`
4. Commit with conventional commit messages
5. Create a pull request

### Commit Message Format

```
type: subject

body (optional)
```

Types:

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc)
- `refactor`: Code refactoring
- `test`: Test changes
- `chore`: Maintenance tasks
- `ci`: CI/CD changes

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

Built with:

- [Turborepo](https://turbo.build/repo)
- [Bun](https://bun.sh/)
- [Next.js](https://nextjs.org/)
- [Biome](https://biomejs.dev/)
- [TypeScript](https://www.typescriptlang.org/)
