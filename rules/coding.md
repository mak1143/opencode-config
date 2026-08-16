---
alwaysApply: true
---

# Coding — Implementation Conventions

## Match existing style

Every codebase has its own conventions. Follow them exactly.

- Read neighboring files before writing new ones
- Use the same naming patterns (camelCase, snake_case, PascalCase)
- Import from the same sources (don't introduce new libraries without checking)
- Follow the same file organization and folder structure
- Use the same error handling patterns

If a codebase uses `const` everywhere, don't introduce `let`. If it uses named exports, don't add default exports.

## Prefer editing over creating

- Always modify an existing file before creating a new one
- If creating a new file is necessary, check how similar files are structured
- Use the `edit` tool for changes to existing files
- Use the `write` tool only for brand new files

## Preserve formatting

When editing code:

- Match the exact indentation (tabs vs spaces, indent width)
- Preserve surrounding whitespace and blank lines
- Keep consistent brace/bracket style with the rest of the file
- Don't reformat unrelated code — make the minimal change needed

## No unsolicited comments

- Never add comments to code unless the user explicitly asks
- Never add TODO comments
- Never add explanatory comments above obvious code
- If code needs a comment to be understood, refactor it instead

## Security basics

- Never log, print, or expose secrets, API keys, or credentials
- Never commit secrets to files that may be version controlled
- Validate all user/external input before using it
- Use parameterized queries — never interpolate strings into SQL
- Sanitize output that goes to HTML, shell, or URLs

## Error handling

- Match the existing error handling pattern in the file/project
- If the project uses try/catch, use try/catch
- If the project uses result types, use result types
- Never silently swallow errors — always propagate or log
- Return meaningful error messages when possible

## Library usage

- Never assume a library is available — check package.json, imports, or requirements
- Don't add new dependencies without the user's approval
- Follow the library's recommended patterns, not outdated examples

## Type safety

- Use explicit types when the codebase uses TypeScript
- Match the strictness level of the existing tsconfig
- Prefer interfaces over type aliases when the codebase does
- Don't use `any` unless the existing code does

## File operations

- Use absolute paths when passing to tools
- Quote paths that contain spaces
- Check that parent directories exist before creating files
- Verify file contents after writing (read back a portion)
