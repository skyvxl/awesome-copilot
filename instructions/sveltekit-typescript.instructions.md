---
description: 'SvelteKit with TypeScript development standards and best practices'
applyTo: '**/*.svelte, **/*.ts, **/*.js, **/*.scss, **/*.css'
---

# SvelteKit + TypeScript Development Instructions

Instructions for building high-quality SvelteKit applications with TypeScript, following modern patterns and best practices.

## Project Context

- SvelteKit 2.x with TypeScript
- TypeScript for type safety across the entire application
- File-based routing with SvelteKit's conventions
- Modern build tooling (Vite as default)
- Server-side rendering (SSR) and static site generation (SSG) capabilities
- Progressive enhancement and accessibility-first approach

## Development Standards

### Architecture

- Use SvelteKit's file-based routing system
- Organize routes by feature or domain for scalability
- Separate UI components from business logic
- Implement proper separation of concerns between client and server code
- Use load functions for data fetching and page initialization
- Leverage SvelteKit's form actions for data mutations
- Structure stores by domain and responsibility

### TypeScript Integration

- Enable strict mode in `tsconfig.json` for maximum type safety
- Use `$types` imports for auto-generated types from load functions
- Define proper types for component props using `ComponentProps<T>`
- Implement generic components where appropriate
- Type all store values and derived stores
- Use `PageData`, `LayoutData`, and `ActionData` types consistently
- Define interfaces for API responses and external data

### Component Design

- Follow the single responsibility principle for components
- Use PascalCase for component names and kebab-case for file names
- Keep components small and focused on one concern
- Implement proper prop validation with TypeScript
- Use slots for flexible composition patterns
- Design components to be testable and reusable
- Follow Svelte's reactive principles with proper state management

### State Management

- Use Svelte stores (`writable`, `readable`, `derived`) for global state
- Implement custom stores for complex state logic
- Use component-level reactive statements (`$:`) for local derived state
- Leverage context API (`setContext`, `getContext`) for component trees
- Keep stores focused and avoid large monolithic state objects
- Use store subscriptions responsibly to prevent memory leaks
- Implement proper store cleanup in component lifecycle

### Routing and Navigation

- Use SvelteKit's file-based routing conventions
- Implement proper error pages (`+error.svelte`)
- Use layout files (`+layout.svelte`) for shared UI structure
- Leverage route parameters and optional parameters effectively
- Implement proper loading states with `+page.ts` or `+page.server.ts`
- Use `goto` and `invalidate` functions for programmatic navigation
- Handle route transitions and page lifecycle properly

### Data Loading and API Integration

- Use `+page.server.ts` for server-side data loading
- Implement `+page.ts` for universal (client/server) data loading
- Use form actions in `+page.server.ts` for data mutations
- Leverage `fetch` with proper error handling in load functions
- Implement proper data validation using libraries like Zod
- Use `depends` for cache invalidation strategies
- Handle loading states and error boundaries appropriately

### Server-Side Features

- Implement API routes using `+server.ts` files
- Use proper HTTP methods and status codes
- Implement request validation and sanitization
- Use environment variables for configuration
- Implement proper authentication and authorization
- Use database connections and ORM integrations appropriately
- Handle file uploads and static asset serving

### Forms and Validation

- Use SvelteKit's progressive enhancement with form actions
- Implement proper client-side and server-side validation
- Use `enhance` action for better form UX
- Handle form errors and success states appropriately
- Implement proper CSRF protection
- Use TypeScript for form data validation
- Provide accessible form feedback and error messages

### Performance Optimization

- Leverage SvelteKit's automatic code splitting
- Use proper preloading strategies with `data-sveltekit-preload-data`
- Implement lazy loading for non-critical components
- Optimize bundle size with proper imports
- Use Svelte's compile-time optimizations
- Implement proper caching strategies
- Monitor and optimize Core Web Vitals

### Testing

- Use Vitest for unit testing components and utilities
- Implement Playwright for end-to-end testing
- Use `@testing-library/svelte` for component testing
- Test user interactions and accessibility
- Mock external dependencies and API calls
- Write tests for load functions and form actions
- Test both client-side and server-side functionality

### Security

- Implement proper input validation and sanitization
- Use HTTPS in production environments
- Implement Content Security Policy (CSP)
- Handle authentication securely with sessions or JWTs
- Protect against common vulnerabilities (XSS, CSRF, injection)
- Validate and sanitize all user inputs
- Use environment variables for sensitive configuration

### Accessibility

- Use semantic HTML elements appropriately
- Implement proper ARIA attributes and roles
- Ensure keyboard navigation support
- Provide screen reader support
- Test with accessibility tools and screen readers
- Follow WCAG guidelines for color contrast and design
- Implement proper focus management

## Implementation Process

1. Plan application architecture and routing structure
2. Set up project structure with proper TypeScript configuration
3. Define types and interfaces for data models
4. Implement core layout and routing structure
5. Create reusable UI components with proper typing
6. Implement data loading with load functions
7. Add form handling with actions and validation
8. Implement authentication and authorization
9. Add error handling and loading states
10. Optimize performance and bundle size
11. Ensure accessibility compliance
12. Add comprehensive testing coverage
13. Document components and API endpoints

## Best Practices

### File Structure
```
src/
├── lib/
│   ├── components/     # Reusable UI components
│   ├── stores/         # Global state stores
│   ├── utils/          # Utility functions
│   ├── types/          # TypeScript type definitions
│   └── server/         # Server-only utilities
├── routes/
│   ├── (app)/          # Route groups
│   ├── api/            # API endpoints
│   └── +layout.svelte  # Root layout
├── app.html            # HTML template
└── app.d.ts            # Global type definitions
```

### Naming Conventions

- Routes: Use kebab-case for file and folder names
- Components: Use PascalCase for component names, kebab-case for files
- Stores: Use camelCase with descriptive names
- Types: Use PascalCase for interfaces and types
- Functions: Use camelCase for function names
- Constants: Use UPPER_SNAKE_CASE for constants

### Import Patterns

- Use `$lib` alias for library imports
- Use relative imports for route-specific files
- Group imports by type (external, internal, types)
- Use `$types` for auto-generated SvelteKit types

### Error Handling

- Implement proper error boundaries with `+error.svelte`
- Use `fail` action for form validation errors
- Handle network errors gracefully
- Provide meaningful error messages to users
- Log errors appropriately for debugging

### Code Style

- Use Prettier for consistent formatting
- Implement ESLint with Svelte-specific rules
- Use TypeScript strict mode
- Follow Svelte's reactive principles
- Keep reactive statements simple and focused
- Avoid side effects in reactive statements

## Common Patterns

- Page data loading with proper TypeScript types
- Form actions with validation and error handling
- Store composition for complex state management
- Component composition with slots and props
- Authentication flows with load functions
- API integration with proper error handling
- Progressive enhancement patterns
- Responsive design with Svelte transitions

## Tools and Libraries

- **Development**: SvelteKit, TypeScript, Vite
- **Styling**: Tailwind CSS, PostCSS, SCSS
- **State**: Svelte stores, custom stores
- **Validation**: Zod, Yup, or similar schema validation
- **Testing**: Vitest, Playwright, Testing Library
- **Linting**: ESLint, Prettier, svelte-check
- **Database**: Prisma, Drizzle, or similar ORM
- **Auth**: lucia-auth, Auth.js, or custom implementation

## Additional Guidelines

- Follow SvelteKit's conventions and best practices
- Use meaningful commit messages with conventional commits
- Implement proper logging and monitoring
- Keep dependencies minimal and up to date
- Document complex components and functions
- Use TypeScript features like branded types where appropriate
- Implement proper error recovery mechanisms
- Consider performance implications of reactive statements