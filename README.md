
# <img src="./public/react-gears.svg" alt="React gears illustration" width="48" style="vertical-align: middle;" /> Modern React Template Lite

A modern, accessibility-first React 19 application built with Vite 7 and TypeScript 5. This template enforces strict rules for accessibility (WCAG 2.2 AA), performance, and code quality.

## 📚 DeepWiki Project Knowledge Base

> **Explore the full documentation, architecture, and deep technical notes for this project on DeepWiki:**
>
> [![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/asudbury/modern-react-template-lite)
>
> - Comprehensive guides, diagrams, and design decisions
> - Contributor onboarding and advanced usage tips
> - Maintainer notes, troubleshooting, and best practices
>
> **This is the canonical knowledge base for the project. If you're contributing, maintaining, or deploying, start here!**


### Fully functional version
There is a fully functional version available here [modern-react-template](https://github.com/asudbury/modern-react-template)

## Features

### Core Features (Always Enabled)
- ♿ [**Accessibility-first**](https://www.w3.org/WAI/WCAG22/quickref/) (WCAG 2.2 AA compliant)

- 📝 [**Commitlint**](https://commitlint.js.org/#/) enforcing conventional commit messages
- 🔒 [**ESLint**](https://eslint.org/) static analysis
- 🪝 [**Husky**](https://typicode.github.io/husky/) pre-commit + commit-msg hooks
- 💅 [**Prettier**](https://prettier.io/) code formatting
- ✨ [**React 19**](https://react.dev/) with the latest features
- 🧪 [**Vitest + React Testing Library**](https://vitest.dev/) unit testing and accessible queries

## Quick Start

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

Visit `http://localhost:5173` to see your application.

## For Forks: What's Enabled by Default?

This template is designed to be **fork-friendly**. Here's what works out of the box:

### ✅ Enabled by Default (No Configuration Needed)
React 19 development with Vite
TypeScript with strict mode
ESLint + Prettier
Husky pre-commit hooks
Commitlint for commit messages
Unit tests with Vitest

**No workflows will fail on your fork!** Disabled features simply won't run. See [QUICKSTART.md](./QUICKSTART.md) to enable features you want.

## Available Scripts

### Development
- `npm run dev` - Start development server
- `npm run build` - Build for production (no GitHub Pages side effects)
- `npm run preview` - Preview production build

### Code Quality
- `npm run lint` - Run ESLint
- `npm run lint:fix` - Fix ESLint issues
- `npm run prettier` - Format code with Prettier
 - Conventional commits enforced via commitlint on `git commit`

### Testing
- `npm run test` - Run unit tests in watch mode
- `npm run test:unit` - Run unit tests
- `npm run test:coverage` - Run tests with coverage
- `npm run test:ui` - Run tests with UI

## Project Structure

```
modern-react-template-lite/
├── .github/
│   └── copilot-instructions.md # Copilot coding guidelines
├── .husky/
│   ├── commit-msg              # Commit message validation
│   └── pre-commit              # Pre-commit hooks
├── src/
│   ├── assets/                 # Static assets
│   ├── test/                   # Test setup/mocks
│   ├── App.tsx                 # Root app component
│   ├── App.test.tsx            # Root app tests
│   ├── main.tsx                # Entry point (includes error boundary)
│   └── index.css               # Global styles
├── .env.example                # Environment variables template
├── .gitignore                  # Git ignore rules
├── .gitleaksignore             # Secret scanning ignore rules
├── .prettierrc                 # Prettier configuration
├── eslint.config.js            # ESLint configuration
├── package.json                # Dependencies and scripts
├── tsconfig.json               # TypeScript configuration
├── vite.config.ts              # Vite configuration
└── vitest.config.ts            # Vitest configuration
```

## Code Quality & Security

### Pre-commit Hooks

Husky enforces code quality on every commit:
1. Format code with Prettier
2. Run unit tests
3. Lint with ESLint
4. Build the project

If any of these checks fails, the commit is blocked and the corresponding
command's error output is shown in your terminal (for example ESLint errors
or failing tests). Fix the reported issues and re-run `git commit`.

Additionally, a Husky `commit-msg` hook runs **commitlint** to enforce
[Conventional Commits](https://www.conventionalcommits.org/) for commit
messages. Example:

```text
feat: add a new component
fix: handle invalid user IDs in updateUser
chore: configure commitlint for commit messages
```

## Key Conventions

### Accessibility

- Every component is keyboard-navigable
- Screen reader friendly with proper ARIA attributes
- WCAG 2.2 AA compliant
- Color contrast ratios meet minimum requirements


### Code Style

- **No inline JSX handlers** - Use `useCallback` or named functions
- **Named exports** - No default exports for components
- **Design tokens only** - No hardcoded colors or spacing
- **Strict TypeScript** - All code must be fully typed

All public APIs (exported functions, components, types) must include JSDoc comments:

```tsx
/**
 * Button Component
 *
 * An accessible button component following WCAG 2.2 AA guidelines.
 *
 * @example
 * ```tsx
 * <Button variant="primary" onClick={handleClick}>
 *   Click me
 * </Button>
 * ```
 */
export function Button({ variant = 'primary', ...props }: ButtonProps) {
  // Implementation
}
```

See `.github/copilot-instructions.md` for detailed JSDoc formatting guidelines.

### Component Guidelines

```tsx
// ✅ Good: Named function with useCallback
const handleClick = useCallback(() => {
  doSomething();
}, [doSomething]);

return <button onClick={handleClick}>Click me</button>;

// ❌ Bad: Inline function
return <button onClick={() => doSomething()}>Click me</button>;
```

### Testing

- **Unit tests** - Use Vitest + React Testing Library
- **Query by role** - Use accessible queries (`getByRole`, `getByLabelText`)
- **User events** - Use `userEvent.setup()`, never `fireEvent`


If a commit is rejected due to an invalid commit message, commitlint prints a
clear error explaining which rule failed (for example, missing `feat:`/`fix:`
prefix or subject line that is too long). In that case, amend your commit
message using:

```bash
git commit --amend
```

and update the message until commitlint passes.

## Environment Variables

Create a `.env` file based on `.env.example`:

```bash
cp .env.example .env
```

All environment variables must be prefixed with `VITE_` to be exposed to the client.

For local tooling and CI toggles, additional variables are defined in
`.env.example` (not exposed to the client), including:

- `SKIP_COMMITLINT` – set to `true` to temporarily skip commit message
  linting enforced by Husky + commitlint

## CI/CD Pipeline

The CI pipeline runs on every push and pull request:

1. **Lint** - ESLint checks
2. **Format** - Prettier checks
3. **Test** - Unit tests with Vitest
4. **Build** - Production build

## Contributing

2. Write tests for all new features
3. Ensure accessibility compliance
4. Run all checks before committing
5. Keep PRs small and focused

## Browser Support

This template targets modern browsers with the following minimum versions:

- Chrome/Edge: Latest 2 versions
- Firefox: Latest 2 versions
- Safari: Latest 2 versions

## License

MIT

## Resources

### Core Framework & Styling

- [React 19 Documentation](https://react.dev)
- [Vite Documentation](https://vite.dev)

### Data, Validation & Accessibility

- [Accessibility (WCAG 2.2 AA)](https://www.w3.org/WAI/WCAG22/quickref/)


### Testing

- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Vitest Documentation](https://vitest.dev)

### Linting, Formatting & Git Hooks

- [Commitlint](https://commitlint.js.org/#/)
- [ESLint](https://eslint.org/)
- [Husky](https://typicode.github.io/husky/)
- [Prettier](https://prettier.io/)
