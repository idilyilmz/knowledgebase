## Daily Workflows

### The Explore → Plan → Code → Commit Workflow

The core workflow to internalize — skipping it means more course-correcting later.

- **Explore & Plan** — Use Plan Mode (`Shift + Tab` until "Plan Mode" appears). Claude reads files and does research without editing anything, then returns a plan. Review it, revise specific areas if needed, and only approve once it looks right. This is the cheapest place to course-correct.
![image]()
- **Code** — Once you approve the plan, Claude works through it (with or without auto-accept). To make this phase smoother: define clear success criteria, give Claude useful tools (e.g., the Claude in Chrome extension for testing web UIs), and provide a reliable test suite it can validate against. If Claude keeps hitting the same issue, ask it to save the fix to `CLAUDE.md`.
- **Commit** — Before pushing, run a subagent code reviewer for a fresh, unbiased pass over the work. Then have Claude generate a commit message in your style.

### Context Management

Context is Claude's working memory — every prompt, file read, and tool result eats into it. When the window fills up, Claude auto-compacts (summarizing to free space, with some detail loss possible).

Three commands to know:

- `/compact` — manually summarize when you're mid-feature and need to keep going.
- `/clear` — wipe everything and start fresh (use this when switching to a new feature so old context doesn't bias it).
- `/context` — see a visual breakdown of what's taking up your window.

For anything you want Claude to remember across sessions, put it in `CLAUDE.md` rather than rediscovering it each time.

**Tips to save context:** be specific in prompts (vague prompts cost *more* context because Claude has to explore), turn off unused MCP servers (they load all their tools upfront — Skills are a lighter alternative), and use subagents for tasks where you only need the answer. Subagents run in their own context window and return just a summary.

### Code Review

A few built-in features that smooth out the git workflow:

- **Subagent code review** — restrict it to read-only tools and check the config into your repo so your whole team uses the same reviewer.
- **`/commit-push-pr` skill** — handles commit, push, and PR creation in one step. If you've configured a Slack MCP server with channels in `CLAUDE.md`, it'll auto-post the PR link.
- **`claude --from-pr <PR_NUMBER>`** — resumes the session linked to a PR, handy for addressing review comments or fixing failing builds later.

**Bottom line:** Explore → Plan → Code → Commit is the spine of effective Claude Code use. Manage context deliberately with `/compact`, `/clear`, and `CLAUDE.md`, and lean on subagents both for keeping context clean and for unbiased reviews before you push.