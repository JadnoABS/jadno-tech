# AGENT.md - Coding Agent Guidelines

## Commands
- **Build**: `npm run build` (type-check + vite build)
- **Dev**: `npm run dev` (vite dev server)
- **Test**: `npm run test:unit` (vitest unit tests)
- **Test single**: `npm run test:unit -- HelloWorld.spec.ts` (run specific test file)
- **E2E**: `npm run test:e2e:dev` (cypress dev) / `npm run test:e2e` (cypress headless)
- **Lint**: `npm run lint` (eslint with auto-fix)
- **Format**: `npm run format` (prettier)
- **Type-check**: `npm run type-check` (vue-tsc)

## Architecture
- **Framework**: Vue 3 + TypeScript + Vite
- **Testing**: Vitest (unit) + Cypress (e2e) + Vue Test Utils
- **State**: Pinia stores in `src/stores/`
- **Routing**: Vue Router in `src/router/`
- **Components**: `src/components/` with tests in `__tests__/`
- **Views**: `src/views/` for page components
- **Alias**: `@` maps to `src/` directory

## Code Style
- **Formatting**: Prettier (no semis, single quotes, 100 char width)
- **Linting**: ESLint with Vue/TypeScript rules
- **Imports**: Use `@/` alias for src imports
- **Tests**: Place in `__tests__/` folders, use `.spec.ts` extension
- **Components**: PascalCase, single-file components (.vue)
- **Naming**: camelCase for variables/functions, PascalCase for components
