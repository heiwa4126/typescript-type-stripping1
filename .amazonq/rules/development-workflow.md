# Development Workflow

## Adding New Test Cases

1. Create new `.ts` files in `src/` directory with descriptive names
2. Focus on TypeScript features that require `--experimental-transform-types`
3. Test execution with multiple methods:
   - `node src/filename.ts` (basic type stripping)
   - `node --experimental-transform-types src/filename.ts` (with transforms)
   - `tsx src/filename.ts` (for comparison)

## Priority Test Cases

Based on Node.js documentation, focus on testing:

- Enums (already implemented in `ex1_enum.ts`)
- Namespaces with runtime code
- Parameter properties in constructors
- Decorators (experimental)
- Import/export type syntax edge cases

## Execution Environment

- Ensure Node.js v25.2.0+ is available
- Use pnpm for package management
- Keep dependencies minimal (only dev dependencies for comparison tools)

## Documentation

- Update README.md with new test cases
- Document any unexpected behaviors or limitations discovered
- Include execution examples with expected output
