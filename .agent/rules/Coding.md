# Coding, Security & Performance Standards

## 🧹 Clean Code
**ALL code MUST follow `@[skills/clean-code]` rules.**
- **Concise**: No over-engineering.
- **Self-documenting**: Clear variable names are better than redundant comments.
- **Testing**: Write tests for critical logic when applicable.

## ⚠️ Static Analysis & Safety
1. **Magic Numbers/Strings**:
   - Important values must be defined as variables, constants, or enums.
   - Do not hardcode repeated strings or numbers.
2. **Error Handling**:
   - Error messages should be meaningful. Clean up `console.log` statements used for debugging before finalizing code.
   - Use specific error handling over generic catch-all blocks.

## 🛡️ Security Protocol (from Security.md)
- **Secrets Management**: **NEVER** commit API keys, tokens, or credentials. Use `.env` files and ensure they are in `.gitignore`.
- **Dependency Safety**: Avoid deprecated packages.
- **Input Validation**: Validate ALL user inputs (API, forms). Sanitize database queries (use ORM or parameterized queries).
- **Authentication**: Use established libraries (Auth.js, Supabase Auth). Verify Row Level Security (RLS) if using Supabase.

## ⚡ Performance Protocol (from Performance.md)
- **Core Web Vitals**: Optimize for fast loading (LCP) and visual stability (CLS).
- **Code Efficiency**: Use Lazy Loading for heavy components. Monitor bundle size. Use `useMemo`/`useCallback` appropriately.
- **Image Optimization**: Use modern formats (WebP/AVIF) and explicit dimensions to prevent layout shifts.

## 🧠 Cognitive-First Execution (Think-Act-Reflect)
- **Think (Plan)**: For non-trivial logic, use `<thought>...</thought>` blocks to reason through your strategy, considering edge cases, security, and scalability before coding.
- **Chunk Edits (Windsurf Rule)**: If making a very large edit (>300 lines), break it up into multiple smaller edits to prevent output token errors.
- **Act (Execute)**: Write clean, modular, and well-documented code following the project's strict standards.
- **Reflect (Verify)**: Always verify your work (e.g., test scripts, terminal outputs). Do not blindly assume the code works.

## 🐛 Root-Cause Debugging Protocol
- **Trace the Source**: Only make code changes if you are **certain** that you can solve the problem. Address the *root cause* instead of the symptoms.
- **Isolate**: Throw away guessing. Add descriptive logging statements and error messages to track variable states. Add test functions to isolate the problem before deploying a patch.

## 📁 File Dependencies & Workflow
**Before modifying ANY file:**
1. **The "Shout" Protocol**: If you are about to modify a core, deeply-integrated component or legacy file, explicitly state the impact ("shout" it) in your `<thought>` block or task plan before touching it.
2. Check file imports and evaluate dependent elements.
3. Update ALL affected files together.
4. Read relevant skill files before writing complex code structures.
5. **Strict Documentation**: Complex functions MUST be documented with JSDoc/TSDoc (or equivalent) before modification.
