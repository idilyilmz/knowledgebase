# Running your first task

https://anthropic.skilljar.com/introduction-to-claude-cowork

## The task loop

This lesson teaches the core Cowork workflow — a four-step loop you'll use for every task:

1. **Describe what you want** — Give Claude what to look at, what you want back, and where it should go. Don't worry about perfect phrasing; Claude will ask about anything missing.
2. **Answer a few clarifying questions** — Claude confirms approach, priorities, and format before starting.
3. **Step away or step in** — A progress panel shows each step. You can leave it running or type in the chat to redirect mid-task.
4. **Open your finished work** — The result saves to your folder (or wherever you specified). Treat it as a capable first draft that's still yours to shape.

**A few things shaping how it runs:** Cowork can spin up *subagents* to handle independent pieces in parallel (e.g., one per vendor in a comparison), progress stays visible, you can steer while it works, everything runs in an isolated environment, and deletions require your approval.

**Practical advice:** Start small with clear-boundary tasks (organizing a folder, synthesizing documents) to build intuition before scaling up. The walkthrough example turns a messy folder of notes, spreadsheets, and emails into a finished leadership PowerPoint — same loop, bigger output.

Next lesson covers giving Cowork persistent context so you don't re-explain yourself each session.

## Giving Cowork context

This lesson covers how to make Cowork carry context across sessions so you're not re-explaining yourself each time.

**The core idea:** Each task starts fresh — Claude doesn't remember past conversations. A *project* solves this: a named workspace tied to a real folder on your machine, with instructions and memory that persist into every task you start inside it. Projects live in Cowork's sidebar and can be started from scratch, imported from a Chat project, or wrapped around an existing folder.

**What to put in the Instructions panel** (read at the start of every task in that project):
- Who's involved — names, roles, contact info
- Where things live — which folders hold what
- Output preferences — formats, save locations
- Project-specific rules — units, citation requirements, etc.

A few lines is enough. The payoff is that shorthand starts working: "send this to the client" or "file it where the Q3 report went" become meaningful.

**Two other places context lives:**
- **Files in the project folder** — Claude reads these too, so running notes or a growing glossary work well as files you update over time.
- **Global instructions** (Settings → Cowork → Global Instructions) — for preferences that apply everywhere, like your role, default formats, or standing rules like "ask before deleting."

**Sanity check:** Inside a project, ask *"Tell me what you know about how I work here"* to confirm Instructions and memory are being picked up.

Your practice task: create a project tied to something you're actively working on and add a few lines to Instructions — key people, where files live, one output preference. Next module covers plugins, which bring domain expertise into Cowork.