# Your first prompt

## Installing Claude Code

You can install Claude Code in several environments:

- **Terminal** — On macOS/Linux/WSL, use curl (or Homebrew, but no auto-updates). On Windows, use PowerShell's `Invoke-RestMethod`, curl in CMD, or winget. Run `claude` in any directory to give it access to that folder and its subfolders. Initial setup covers theme, sign-in (Pro/Max/Enterprise), or API key.
- **VS Code** — Install the official Anthropic extension from the Extensions panel, then open via Command Palette ("Claude Code Open in New Tab") or the sidebar icon.
- **JetBrains** — Install the plugin from the Marketplace, restart the IDE, and click the Claude logo to open a terminal-style pane.
- **Desktop** — After signing into Claude Desktop, toggle "Code" at the top to work in a specific folder or cloud environment.
- **Web** — Visit `claude.ai/code` to work remotely on GitHub repositories.

**Which to pick?** Terminal gets new features first; IDE integrations mirror it closely; Desktop is good for background work; Web is best for remote GitHub work.

## Your First Prompt

Talk to Claude Code like any AI assistant, but be descriptive. Two settings shape the experience (cycle with `Shift + Tab`):

- **Approval mode** — Claude asks before every file edit or command.
- **Auto-accept mode** — File edits happen automatically, but commands still need approval.
![image](/notes/courses/anthropic/claude-code-101/assets/video4autoaccept.1775686381332.jpg)
- **Plan mode** — Claude uses read-only tools to analyze the codebase, ask clarifying questions, and return a detailed plan before touching anything. Ideal for complex, multi-step changes or safe code reviews.
![image](/notes/courses/anthropic/claude-code-101/assets/video4planmode.1775686383837.jpg)
**Example workflow** — Adding a dark mode toggle: open your project's root directory, run `claude`, enter Plan Mode, and describe the change (e.g., "add a dark mode toggle to the header with good contrast against my existing light theme"). Review the plan, accept it, then approve each step as Claude executes.
![image](/notes/courses/anthropic/claude-code-101/assets/video4demoenteringpromptinplanmode.1775686382790.jpg)

**Bottom line:** be descriptive, and lean on Plan Mode when you want Claude to think before it codes.