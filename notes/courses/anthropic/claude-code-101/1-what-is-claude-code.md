# What is claude code?

Claude Code is an agentic coding tool that works directly inside your terminal, VS Code, JetBrains, and the Claude Desktop app. Unlike Claude.ai, it has direct access to your files, terminal, and codebase — so instead of copy-pasting code, it does the work itself: reading your codebase, editing files across the project, running commands, and searching the web for docs.

It functions as an AI agent, meaning it runs in an **agentic loop**: you give a prompt → it gathers context → takes an action (edit a file, run a command) → verifies the result → either finishes or loops again. You can interrupt, steer, or add context at any point.

Three concepts matter for using it well:

- **Context window** — Claude's working memory; it can't hold your entire codebase at once, so it strategically locates what it needs and auto-compacts older conversation when the limit is reached.
- **Tools** — the mechanism that lets Claude go beyond text-in/text-out (reading files, running shell commands, web search, etc.).
- **Permissions** — three modes: default (asks before editing or running commands), auto-accept (edits without asking, still confirms commands), and plan mode (read-only planning before any action).

Bottom line: it's fast and powerful, but it can still misunderstand intent or introduce bugs, so staying in the loop — rather than skipping permissions entirely — is the safer way to work with it.

![image](/notes/courses/anthropic/claude-code-101/assets/agenticloop.1775686365141.jpg)

![image](/notes/courses/anthropic/claude-code-101/assets/video2ask.1775686376586.jpg)

