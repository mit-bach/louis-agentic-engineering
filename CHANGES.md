# Changes

## 0.8.0 · 2026-11-11 · The whole store course is out

- **The store kit** now has M6: your orders, the spec you write, the frontend your agent builds from it, the walkthrough by hand, and the no-spec control. All six milestones are in. You get it with `make update` in `~/code/store`.
- **`ROADMAP.md`:** M6 takes about 2 days, so the course is about 13 working days.
- **`OPTIONAL-SPECS.md`:** a new spec, errors the browser can read.

## 0.7.6 · 2026-11-10 · Store milestone M5

- **The store kit** now has M5:
  - checkout that's safe to retry;
  - errors written for agents;
  - your customer's agent, and what it may do;
  - least privilege, tested;
  - evals of your shopping agents.

  You get it with `make update` in `~/code/store`.
- **`ROADMAP.md`:** M5 takes about 2 days, so the course is about 12 working days.

## 0.7.4 · 2026-11-08 · Store milestone M4

- **The store kit** now has M4: orders, checkout in one transaction, the race and the deadlock test, two agents racing for one unit, and your first audit of your harness. You get it with `make update` in `~/code/store`.
- **`ROADMAP.md`:** M4 takes about 2 days.

## 0.7.3 · 2026-11-08 · Store milestone M3

- **The store kit** now has M3: visitor sessions, the cart, shopping agents, and your reviewer as a skill in your tutor harness. You get it with `make update` in `~/code/store`.

## 0.7.2 · 2026-11-08 · Store milestone M2

- **The store kit** now has M2: archiving, editing, adjusting stock, your first race, and the wall on both sides. You get it with `make update` in `~/code/store`.
- **`ROADMAP.md`:** M2 takes about 2 days.
- **`OPTIONAL-SPECS.md`:** a new spec, your own migration runner.

## 0.7.0 · 2026-11-08 · Your first course: the store kit

- **New repository:** [`mit-bach/louis-store`](https://github.com/mit-bach/louis-store), the store kit, with milestones M0 and M1. Every operation is reachable over HTTP, from the command line, and as an agent tool.
- **`SETUP.md` stage 5** clones it into `~/code/store` and sends you to Tutor Orch to start course 01.
- **`ROADMAP.md`:** M1 now includes the command line, and takes about 2 days.

## 0.6.0 · 2026-11-08 · Your tutor harness, installed for real

- **New repository:** [`mit-bach/louis-tutor`](https://github.com/mit-bach/louis-tutor), your tutor harness. It's ported from the tutor system Dominik uses every day: the rulebook, five lesson formats, the startup hook, `new-course`, the lesson linter, a self-check, the course template, Tutor Orch's role and records, and a `new-course` skill.
- **`SETUP.md` stage 4** clones it into `~/tutor`, runs its self-check, and starts Tutor Orch and Tutor Prime in Berth.
- **Removed:** `harness/`, the earlier read-only drafts. The real harness replaces them.

## 0.5.1 · 2026-11-08 · One source for Berth

- **Removed:** `vendor/`. Berth comes only from [`mit-bach/berth-kit`](https://github.com/mit-bach/berth-kit), which is public and reviewed. If cloning it fails, setup stops and tells you, instead of installing an older copy.
- **`SETUP.md`:** it always checks that `v3.1.0` is the reviewed commit, and skips Berth's "Keep a baseline" step, since your copy is a git clone.

## 0.5.0 · 2026-11-08 · The prompt comes first, and it shows you what it can do

- **`README.md`:** the prompt is now the first thing on the page. It sets everything up in one chat, then runs agents for you.
- **`SETUP.md`:** a new stage 3, "Show me what it can do". From this one chat, your agent:
  - starts two Claude sessions through Berth, "Scout" and "Critic", which hand work to each other through files;
  - watches them with cmux-mcp;
  - brings their results back to you, and shows you a Berth move on them.

  The tutor harness and the store are now stages 4 and 5.
- **Coming:** running whole teams of agents, the way Dominik's orchestrators do.

## 0.4.2 · 2026-11-08 · Setup fixes from Berth's maintainer

- **`SETUP.md`:**
  - an empty clone is caught by what's in it, not by whether `git clone` succeeded;
  - the empty folder is deleted before the fallback copy is unzipped;
  - the agent never `cd`s into the kit, so Berth's restart reopens the chat where it started;
  - the fallback copy keeps Berth's "Keep a baseline" step.

## 0.4.1 · 2026-11-08 · A check on the Berth kit you clone

- **`SETUP.md`:** a clone tagged `v3.1.0` is accepted only if that tag is the reviewed commit `226f7232…`. Otherwise setup uses the copy in `vendor/`.

## 0.4.0 · 2026-11-08 · One prompt downloads and installs everything

- **`README.md`:** one prompt to paste into Claude Code inside cmux, from any folder. It clones this repository into `~/louis-agentic-engineering`, then follows `SETUP.md`.
- **`SETUP.md`:**
  - it clones the Berth kit from `mit-bach/berth-kit` into `~/berth-kit`, falling back to `vendor/` if the clone fails or comes back empty;
  - it runs Berth's own onboarding in the same chat, which restarts once and carries on from `~/.louis-setup/PROGRESS.md`;
  - stages 3 and 4 pick up the tutor harness and the store when they arrive.
- **Updates:** paste the same prompt again. It pulls what's new and skips what's done.

## 0.3.4 · 2026-11-07 · Every repository it uses, linked

- **`README.md`:** a new section, "Repositories this uses". It links this repository and the Berth kit's, says where cmux comes from, and will list the store kit's repository once it exists.

## 0.3.3 · 2026-11-07 · Berth 3.0.1

- **`vendor/`:** the Berth kit is now 3.0.1, which fixes a one-time "catalog unreadable" that could appear on a brand-new install, while everything was starting at once.
- **`SETUP.md`:** the checksum step works for whichever kit version is in `vendor/`.

## 0.3.2 · 2026-11-07 · The repository is the way in

- **`README.md`:** you start from a clone of this repository, with the exact command. Updates reach you with `git pull`.

## 0.3.1 · 2026-11-07 · Works from the emailed zip too

- **`README.md`:** you can start from the zip Dominik emailed, unzipped somewhere permanent, as well as from a clone. The kickoff prompt says "copy" instead of "clone".

## 0.3.0 · 2026-11-07 · Berth comes with it

- **New:** `vendor/berth-kit-3.0.0.zip` and its `.sha256`. It's the Berth kit, version 3.0.0, in an edition made for you, with the same Berth and cmux-mcp. Stage 1 of `SETUP.md` now works from start to finish.
- **`SETUP.md`:** stage 1 checks the zip with `shasum -a 256 -c`, unzips it to `~/berth-kit`, and reads the kit's `VERSION`.
- **Still to come:** the tutor harness install (stage 2), the store kit (stage 3), and "Meet your harness".

## 0.2.2 · 2026-11-07 · Your harness runs on Berth

- **`harness/CLAUDE.md`:** the keeper starts each course's tutor through `new-course`, as a Berth session in that course's folder, never elsewhere or by forking. It lists and files your sessions, and waking, sleeping and closing them stay your calls. The rulebook is still under its 1,500-word budget.
- **`harness/HARNESS.md`:** a new section, "Your sessions, in Berth", and two new terms, Berth and fork.
- **`ROADMAP.md`:**
  - after "Meet your harness", you file your sessions in Berth folders;
  - the M4 audit reads Berth's list of your sessions, and you compact through Berth;
  - the capstone starts with one fork on purpose.
- **Still to come:** the bundled Berth kit, the tutor harness install, the store kit, and "Meet your harness".

## 0.2.1 · 2026-11-07 · Fixes before the Berth kit is bundled

- **`SETUP.md`:**
  - the Python check now asks for uv or Python 3.12 itself, because the Berth installer needs one of them;
  - stage 1 now takes the Berth kit from `vendor/`, an edition made for you, instead of a repository you'd need access to;
  - its last check uses `berth sessions --json`;
  - the day-one decisions are asked once, in the kit's onboarding.
- **`harness/HARNESS.md`:** every course folder gets its own `.claude/settings.json`, because Claude Code reads settings only from the folder a session starts in.
- **Still to come:** the bundled Berth kit (next version), the tutor harness install, the store kit, and "Meet your harness".

## 0.2.0 · 2026-11-07 · Your environment, set up by your agent

- **New:** `SETUP.md`, and a kickoff prompt in `README.md`. Stage 1 installs cmux, Berth and their MCP servers, through the Berth kit's own onboarding (version 3.0.0 or newer).
- **Changed:** `README.md` and `ROADMAP.md` start with that setup.
- **Still to come:** the tutor harness install (stage 2), the store kit (stage 3), and the "Meet your harness" course.

## 0.1.0 · 2026-11-07 · Preview

- **In it:**
  - `README.md`;
  - `ROADMAP.md`;
  - `OPTIONAL-SPECS.md`;
  - the tutor harness's rulebook (`harness/CLAUDE.md`), its map (`harness/HARNESS.md`), and its two lesson formats (`harness/formats/`).
- **Not in it yet:**
  - the store kit: the starter repo, the API contract, the guides and the checks;
  - the harness's tools, hook and skill;
  - the "Meet your harness" course.
- **What to do:** read it. There's nothing to install yet.
