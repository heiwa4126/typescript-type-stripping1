# Project Context Rules

## Project Purpose

This is a testing project for Node.js TypeScript Type Stripping functionality introduced in Node.js v25.2.0. The project tests TypeScript features that are NOT supported by native type stripping and require the `--experimental-transform-types` flag.

## Key Project Information

- **Main Goal**: Test TypeScript constructs that don't work with basic type stripping
- **Node.js Version**: Targeting v25.2.0+ with type stripping support
- **Package Manager**: pnpm
- **Runtime**: Node.js native TypeScript execution

## Supported vs Unsupported Features

### Basic Type Stripping (works without flags):

- Type annotations on variables, parameters, return types
- Interface declarations
- Type aliases
- Generic type parameters

### Requires `--experimental-transform-types` flag:

- `enum` declarations
- `namespace` declarations
- Parameter properties (constructor shorthand)
- Decorators
- TSX/JSX syntax

## Testing Commands

- Basic execution: `node src/hello.ts`
- With transform flag: `node --experimental-transform-types src/ex1_enum.ts`
- Alternative runtimes: `tsx` or `bun` for comparison
