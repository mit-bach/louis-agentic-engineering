# Changes

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
