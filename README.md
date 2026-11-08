# Agentic engineering, from a store up

**From Dominik, for Louis. Version 0.3.0, a preview (2026-11-07).**

This is a project, and a setup for learning. You'll build a small online store:
- **Its backend you write yourself, by hand.**
- **Agents can use it.** An AI agent can use the store as fully as a person can.
- **Your own harness.** Along the way you set up, and keep changing, your own Claude Code harness. That's the rules, tools and hooks that shape what an agent does.

It's built to grow three things:
1. your software engineering technicals;
2. your agentic engineering technicals;
3. a feel for what an **agent-first product** is, and for **managing a harness** the way an experienced agentic engineer does.

## Start here: one prompt sets up your environment

You'll work the way Dominik does every day:
- **cmux,** a terminal app built for running many agent sessions;
- **Berth,** a catalog of all your sessions, with an MCP server so agents can start and run other agents;
- **cmux-mcp,** which lets one agent see and type into another's pane.

Your agent installs them for you, one step at a time, and explains each step as it goes.

1. **Clone this repository somewhere it can stay for good,** such as `~/louis-agentic-engineering`. Don't put it in Downloads, Desktop, Documents or iCloud.
2. **Open that folder in your terminal,** and start Claude Code with `claude`.
3. **Send it this:**

```text
I'm Louis. Dominik gave me this repository to learn agentic engineering, and you're running inside my clone of it. Set up my development environment: read SETUP.md all the way through and do what it says, one stage at a time. I'm new to this, so explain each step in plain words before you do it, show me dry runs first, and ask me before you change anything on my Mac.
```

Berth comes inside this repository, in an edition made for you, so this repository is the only one you need access to.

## What's in this version

- **[`SETUP.md`](SETUP.md):** your agent's setup steps. Stage 1 (cmux, Berth and the MCP servers) works now. The tutor harness and the store follow in the next versions.
- **[`vendor/`](vendor/):** the Berth kit, version 3.0.0, in an edition made for you, with its checksum.
- **[`ROADMAP.md`](ROADMAP.md):** the whole plan. It covers what you build and in what order, what you write versus what your agents do, and how you check each step yourself.
- **[`OPTIONAL-SPECS.md`](OPTIONAL-SPECS.md):** extra tasks you can pick from once the main path is done, or alongside it.
- **[`harness/`](harness/):** the rulebook and the two lesson formats of your tutor harness. Read them now; don't install them yet. Start with [`harness/HARNESS.md`](harness/HARNESS.md), then [`harness/CLAUDE.md`](harness/CLAUDE.md).
- **[`CHANGES.md`](CHANGES.md):** what each version adds.

## What's coming next

These parts aren't in this version yet. Each one gets tested before you get it.
- **The store kit:**
  - the starter repo;
  - the exact API contract;
  - the step-by-step guides;
  - the check suite you'll run after every step.
- **The harness's moving parts:**
  - the startup hook;
  - the `new-course` skill;
  - the lesson checker;
  - the transcript reader;
  - the first course, "Meet your harness".

**So for now: set up your environment with the prompt above, then read.**

## What to do now

1. **Run the setup prompt above,** and finish stage 1.
2. **Read `ROADMAP.md`,** start to finish.
3. **Before you open `harness/CLAUDE.md`, make one prediction.** Write down which file you think decides what a tutor does when you say a lesson was bad. Then read `harness/HARNESS.md` and `harness/CLAUDE.md`, and check your guess. Predicting first, then checking, is the habit this whole project trains.
4. **Write down every question,** and everything that's unclear. Send them to Dominik.
5. **For the store, later, you'll also need Docker Desktop.** Its first milestone gives the exact install steps.
