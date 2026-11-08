# Agentic engineering, from a store up

**From Dominik, for Louis. Version 0.1, a preview (2026-11-07).**

This is a project, and a setup for learning. You'll build a small online store:
- **Its backend you write yourself, by hand.**
- **Agents can use it.** An AI agent can use the store as fully as a person can.
- **Your own harness.** Along the way you set up, and keep changing, your own Claude Code harness. That's the rules, tools and hooks that shape what an agent does.

It's built to grow three things:
1. your software engineering technicals;
2. your agentic engineering technicals;
3. a feel for what an **agent-first product** is, and for **managing a harness** the way an experienced agentic engineer does.

## What's in this version

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

**So for now, read. Don't install anything.**

## What to do now

1. **Read `ROADMAP.md`,** start to finish.
2. **Before you open `harness/CLAUDE.md`, make one prediction.** Write down which file you think decides what a tutor does when you say a lesson was bad. Then read `harness/HARNESS.md` and `harness/CLAUDE.md`, and check your guess. Predicting first, then checking, is the habit this whole project trains.
3. **Write down every question,** and everything that's unclear. Send them to Dominik.
4. **Check that you have these:**
   - a Mac with Claude Code;
   - git;
   - Python 3.12 or newer;
   - Docker Desktop;
   - a GitHub account.

   The first milestone gives exact install steps for anything that's missing.
5. **Send Dominik your GitHub username,** so he can give you access to the repos.
