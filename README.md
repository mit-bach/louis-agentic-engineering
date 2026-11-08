# Agentic engineering, from a store up

**From Dominik, for Louis. Version 0.4.1, a preview (2026-11-08).**

This is a project, and a setup for learning. You'll build a small online store:
- **Its backend you write yourself, by hand.**
- **Agents can use it.** An AI agent can use the store as fully as a person can.
- **Your own harness.** Along the way you set up, and keep changing, your own Claude Code harness. That's the rules, tools and hooks that shape what an agent does.

It's built to grow three things:
1. your software engineering technicals;
2. your agentic engineering technicals;
3. a feel for what an **agent-first product** is, and for **managing a harness** the way an experienced agentic engineer does.

## Start here: one prompt sets up everything

You'll work the way Dominik does every day:
- **cmux,** a terminal app built for running many agent sessions;
- **Berth,** a catalog of all your sessions, with an MCP server so agents can start and run other agents;
- **cmux-mcp,** which lets one agent see and type into another's pane.

One prompt downloads every repository this project uses and installs everything. Your agent explains each step as it goes, and asks before it changes anything on your Mac.

1. **Install cmux:** download it from https://cmux.com, drag it into Applications, and open it once.
2. **In cmux, open a workspace,** and start Claude Code with `claude`. It doesn't matter which folder you're in.
3. **Paste this, and answer its questions:**

```text
I'm Louis, and I'm learning agentic engineering. My friend Dominik built me a project for it, and I want you to set up everything on this Mac from scratch and get it running.

1. Clone https://github.com/mit-bach/louis-agentic-engineering into ~/louis-agentic-engineering, which is where it stays for good. If it's already there, pull the newest version instead.

2. Read ~/louis-agentic-engineering/SETUP.md all the way through, then do what it says, one stage at a time. It downloads the rest, including Dominik's Berth kit, and installs cmux's tools, Berth and their MCP servers. Keep track the way it says, because this chat restarts once on the way.

3. I'm new to this. Explain each step in plain words before you do it, show me dry runs first, and ask me before you change anything on my Mac.

Ground rules: don't close, restart, or type into any of my other sessions unless I say so. If anything fails, stop and tell me what happened instead of working around it.
```

The chat restarts once, to load Berth's tools. When it reopens, type `continue`. When there's a new version of this project, paste the same prompt again: it picks up what's new and skips what's done.

## Repositories this uses

- **This one,** [`mit-bach/louis-agentic-engineering`](https://github.com/mit-bach/louis-agentic-engineering): the roadmap, your setup, and your tutor harness's method. Your agent clones it into `~/louis-agentic-engineering`.
- **[`mit-bach/berth-kit`](https://github.com/mit-bach/berth-kit):** Berth, cmux-mcp and their skills. Your agent clones it into `~/berth-kit` and installs Berth from there. If that clone ever fails, it uses the copy in `vendor/` instead. Its README, docs and changelog are worth reading.
- **Not ours:** cmux, the terminal app, from https://cmux.com.
- **Coming:** the store kit's repository, listed here once it exists.

## What's in this version

- **[`SETUP.md`](SETUP.md):** your agent's setup steps. Downloading the repositories and installing Berth and its MCP servers work now. The tutor harness and the store follow in the next versions.
- **[`vendor/`](vendor/):** a fallback copy of the Berth kit, version 3.0.1, with its checksum.
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

**So for now: run the prompt above, then read.**

## What to do now

1. **Run the setup prompt above,** and let it finish.
2. **Read `ROADMAP.md`,** start to finish.
3. **Before you open `harness/CLAUDE.md`, make one prediction.** Write down which file you think decides what a tutor does when you say a lesson was bad. Then read `harness/HARNESS.md` and `harness/CLAUDE.md`, and check your guess. Predicting first, then checking, is the habit this whole project trains.
4. **Write down every question,** and everything that's unclear. Send them to Dominik.
5. **For the store, later, you'll also need Docker Desktop.** Its first milestone gives the exact install steps.
