# Setup, for your agent

**Louis:** your agent reads this file, not you. Send it the kickoff in `README.md`, and answer its questions.

**Agent:** you're setting up Louis's agentic development environment on his Mac. It's the setup Dominik works in every day:
- **cmux,** a terminal app built for running many agent sessions;
- **Berth,** a catalog of every session, with folders, sleep and wake, restart and fork, plus an MCP server so agents can start and run other agents;
- **cmux-mcp,** which lets an agent see and type into another session's pane.

After that come Louis's tutor harness and his store project.

**How to work with him:**
- He's new to this. Explain each step in plain words before you do it.
- Show a dry run first wherever there is one, and wait for his go-ahead.
- Ask before you change anything on his Mac.
- Never close, restart or type into his other sessions.
- If something fails, stop and tell him what happened. Don't work around it.
- Keep track in `~/.louis-setup/PROGRESS.md`: the stage, what's done, and what's next. At the end of each stage, tell him exactly what to do or paste next.

---

## Stage 0 · Check what's there

1. **Check each of these, and show him the result:**
   - this Mac runs macOS;
   - Claude Code runs (`claude --version`);
   - git is there (`git --version`);
   - uv is installed (`uv --version`), or Python 3.12 itself (`python3.12 --version`). The Berth installer needs one of the two, and Python 3.13 alone isn't enough. If neither is there, leave it: the Berth kit's onboarding installs uv once he says yes, and uv fetches Python 3.12 itself.
2. **Check where this repository lives.** It has to stay in one place for good, such as `~/louis-agentic-engineering`. If it's in Downloads, Desktop, Documents or iCloud, ask him to move it first.
3. **Check that the Berth kit came with this repository:** `ls vendor/berth-kit-*.zip`. If it's missing, stop and tell him this version doesn't include it yet.
4. **Don't install anything in this stage.**

## Stage 1 · cmux, Berth and their MCP servers

These come from the Berth kit, an edition made for him, which ships inside this repository in `vendor/`. The kit has its own onboarding, which runs in its own chat, inside cmux. Your job here is to get him there, and to check the result afterwards.

1. **He installs cmux himself.** He downloads it from https://cmux.com, drags it into Applications, and opens it once. Wait until he says it's open.
2. **Unpack the Berth kit where it will live for good,** because everything it installs runs from that folder:
   - check the zip against its `.sha256` file in `vendor/`, and stop if it doesn't match;
   - unzip it so its top folder becomes `~/berth-kit`;
   - tell him the version, from the kit's `CHANGELOG.md`.
3. **Hand him to the kit's own onboarding.** Read the "cmux" section of `~/berth-kit/README.md`, and give him its steps 3 and 4 exactly:
   - in cmux, open a workspace;
   - `cd ~/berth-kit` and start `claude`;
   - send it the kit's cmux prompt, which you copy for him word for word from that README.

   That chat installs Berth and the MCP servers, checks them, and walks him through his first day. On the way it asks him the day-one decisions, including Berth's session standard. Those are settled there, so no later stage asks them again.

   Tell him to come back here when it's finished, in a new Claude chat in this repository, opened inside cmux this time, and to say "stage 1 done".
4. **When he's back, check it worked, and show him each result:**
   - `berth status` answers, with its watcher and cmux up;
   - `python3 ~/berth-kit/tools/doctor.py` exits 0. A "note", such as a sidebar or shortcut he declined, is fine. A "FIX" isn't;
   - `claude mcp list` shows `berth` and `cmux-mcp`, both connected;
   - `berth sessions --json` lists his folder, and one row has `"you": true`. That row is this chat.

   If any of these fails, stop and tell him which one. Don't fix the Berth kit yourself.

From here on, Louis works inside cmux, and every session he starts is a row in Berth.

## Stage 2 · His tutor harness

Coming in the next version of this repository. It installs into `~/tutor/`.

## Stage 3 · The store

Coming with the store kit. It goes in `~/code/store/`.
