# Agentic engineering, from a store up

**From Dominik, for Louis. Version 0.8.0 (2026-11-11).**

## Paste this into Claude Code

First install **cmux** from https://cmux.com: drag it into Applications and open it. In cmux, open a workspace, run `claude`, and paste this:

```text
I'm Louis. Dominik built me a project to learn agentic engineering. Set up my whole environment on this Mac from scratch, in this one chat, and then show me what it can do.

1. Clone https://github.com/mit-bach/louis-agentic-engineering into ~/louis-agentic-engineering. If it's already there, pull the newest version instead.

2. Read ~/louis-agentic-engineering/SETUP.md all the way through and do every stage, in order. It downloads Dominik's Berth kit from https://github.com/mit-bach/berth-kit, installs Berth, cmux-mcp, their MCP servers and their skills, restarts this chat once to load them, and checks that everything works. Keep track the way it says, so you carry on after the restart.

3. Then go all in with the new tools, from this same chat. Run agents for me: start sessions with the Berth MCP, give them jobs, watch them work with cmux-mcp, and bring their results back here, the way SETUP.md's "Show me what it can do" stage says.

4. I'm new to this. Explain each step in plain words before you do it, show me dry runs first, and ask me before you change anything on my Mac or start a new session.

Ground rules: don't close, restart, or type into any session you didn't start unless I say so. Sessions are mine to close. If anything fails, stop and tell me what happened instead of working around it.
```

The chat restarts once, to load Berth's tools. When it reopens, type `continue`. To get a newer version later, paste the same prompt again: it pulls what's new and skips what's done.

## What this is

A project, and a setup for learning. You'll build a small online store:
- **Its backend you write yourself, by hand.**
- **Agents can use it.** An AI agent can use the store as fully as a person can.
- **Your own harness.** Along the way you set up, and keep changing, your own Claude Code harness. That's the rules, tools and hooks that shape what an agent does.

It's built to grow three things:
1. your software engineering technicals;
2. your agentic engineering technicals;
3. a feel for what an **agent-first product** is, and for **managing a harness** the way an experienced agentic engineer does.

You'll work the way Dominik does every day:
- **cmux,** a terminal app built for running many agent sessions;
- **Berth,** a catalog of all your sessions, with an MCP server so agents can start and run other agents;
- **cmux-mcp,** which lets one agent see and type into another's pane.

## Repositories this uses

- **This one,** [`mit-bach/louis-agentic-engineering`](https://github.com/mit-bach/louis-agentic-engineering): the roadmap and your setup. Your agent clones it into `~/louis-agentic-engineering`.
- **[`mit-bach/louis-tutor`](https://github.com/mit-bach/louis-tutor):** your tutor harness, ported from the tutor system Dominik uses: the rulebook, lesson formats, startup hook, course tools, and the Tutor Orch and Tutor Prime sessions. Your agent clones it into `~/tutor` and installs it.
- **[`mit-bach/louis-store`](https://github.com/mit-bach/louis-store):** your first course, the store kit: the brief, the contract, the step-by-step guides and the checks, with no backend code in it, since that's yours to write. Your agent clones it into `~/code/store`. All six milestones, M0 to M6, are ready. Fixes and optional extras arrive with `make update`.
- **[`mit-bach/berth-kit`](https://github.com/mit-bach/berth-kit):** Berth, cmux-mcp and their skills. Your agent clones it into `~/berth-kit` and installs Berth from there, and you update it with its README's "Update" prompt. Its README, docs and changelog are worth reading.
- **Not ours:** cmux, the terminal app, from https://cmux.com.

## What's in this version

- **[`SETUP.md`](SETUP.md):** your agent's setup steps. Downloading the repositories, installing Berth and its MCP servers, the "Show me what it can do" run, installing your tutor harness, and setting up the store all work now.
- **[`ROADMAP.md`](ROADMAP.md):** the whole plan. It covers what you build and in what order, what you write versus what your agents do, and how you check each step yourself.
- **[`OPTIONAL-SPECS.md`](OPTIONAL-SPECS.md):** extra tasks you can pick from once the main path is done, or alongside it.
- **[`CHANGES.md`](CHANGES.md):** what each version adds.

## What's coming next

These parts aren't in this version yet. Each one gets tested before you get it.
- **Running many agents at once:** the way Dominik's orchestrators run whole teams of agents. It builds on what the "Show me" stage starts.
- **The first course, "Meet your harness",** inside your tutor harness.

**So for now: run the prompt at the top, then read.**

## What to do now

1. **Run the prompt at the top,** and let it finish.
2. **Read `ROADMAP.md`,** start to finish.
3. **Before you open `~/tutor/CLAUDE.md`, make one prediction.** Write down which file you think decides what a tutor does when you say a lesson was bad. Then read `~/tutor/README.md` and `~/tutor/CLAUDE.md`, and check your guess. Predicting first, then checking, is the habit this whole project trains.
4. **Write down every question,** and everything that's unclear. Send them to Dominik.
5. **For the store, later, you'll also need Docker Desktop.** Its first milestone gives the exact install steps.
