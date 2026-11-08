# Changes

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
