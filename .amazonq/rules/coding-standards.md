# Coding Standards

## TypeScript Guidelines

- Use strict TypeScript configuration as defined in tsconfig.json
- Prefer explicit type annotations for function parameters and return types
- Use `verbatimModuleSyntax: true` - import types with `type` keyword
- Follow `isolatedModules: true` constraints

## File Organization

- Place test files in `src/` directory
- Use descriptive filenames with prefixes (e.g., `ex1_enum.ts`, `ex2_namespace.ts`)
- Each file should test a specific TypeScript feature

## Testing Approach

- Create minimal examples that demonstrate specific TypeScript features
- Include console.log statements to verify runtime behavior
- Test both with and without `--experimental-transform-types` flag
- Document expected behavior vs actual behavior

## Code Style

- Use tabs for indentation (as per existing codebase)
- Keep examples simple and focused on the feature being tested
- Add comments explaining what TypeScript feature is being demonstrated
