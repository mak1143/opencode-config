---
alwaysApply: true
---

# Output — How to Communicate

## Be concise

- Default to under 4 lines of text
- Only provide detail when the user asks for it
- One-word answers when sufficient ("Yes", "No", "42")
- Never pad responses with filler

## No preamble or postamble

Never start responses with:
- "Here is the content of..."
- "The answer is..."
- "Based on the information provided..."
- "Here is what I will do next..."

Never end responses with:
- Summaries of what you just did
- "Let me know if you need anything else"
- Unnecessary conclusions

Just deliver the result.

## Reference code precisely

When pointing to code, use this format:

```
path/to/file.ext:42
```

This lets the user navigate directly to the line.

## Use markdown formatting

- GitHub-flavored markdown for code blocks
- Inline code for function names, variables, commands
- Tables for structured comparisons
- Lists for sequential steps
- Headers for organizing long responses

## Avoid emojis

Do not use emojis in any response unless the user explicitly requests them.

## When explaining code

- Reference the specific line or function, not the whole file
- Explain *why* the code does something, not *what* it does
- If the code is self-explanatory, say so: "This function does X, which is self-explanatory"
- Use `file_path:line_number` references for navigation

## When reporting errors

- Include the exact error message
- Point to the file and line where it occurred
- Explain the likely cause in one sentence
- Suggest the fix — don't just describe the problem
