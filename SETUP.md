# Setup, for your agent

**Louis:** your agent reads this file, not you. You started it with the prompt in `README.md`. Answer its questions, and press the keys when it asks you to.

**Agent:** you're setting up Louis's agentic development environment on his Mac, from nothing, in this one chat. It's the setup Dominik works in every day:
- **cmux,** a terminal app built for running many agent sessions;
- **Berth,** a catalog of every session, with folders, sleep and wake, restart and fork, plus an MCP server so agents can start and run other agents;
- **cmux-mcp,** which lets an agent see and type into another session's pane.

After that come Louis's tutor harness and his store project.

**What lives where.** Each of these stays put for good, because what's installed runs from it:
- `~/louis-agentic-engineering`: this repository;
- `~/berth-kit`: the Berth kit;
- `~/tutor/`: his tutor harness, later;
- `~/code/store/`: his store, later.

**How to work with him:**
- He's new to this. Explain each step in plain words before you do it.
- Show a dry run first wherever there is one, and wait for his go-ahead.
- Ask before you change anything on his Mac.
- Never close, restart or type into his other sessions.
- If something fails, stop and tell him what happened. Don't work around it.
- **Keep track** in `~/.louis-setup/PROGRESS.md`: the stage and step, what's done, and what's next. This chat restarts once, during stage 2. When it reopens and he says "continue", read that file and carry on from where it says.

---

## Stage 0 · Check what's there

1. **Check each of these, and show him the result:**
   - this Mac runs macOS;
   - **this chat is running inside cmux:** `cmux --version` answers, and he confirms the window is cmux. If it isn't, stop. Tell him to install cmux from https://cmux.com (drag it into Applications, open it once), open a workspace there, start `claude`, and paste the README's prompt again. Berth needs this chat to be inside cmux;
   - Claude Code runs (`claude --version`);
   - git is there (`git --version`). If macOS offers to install the developer tools instead, let him accept, then check again;
   - uv is installed (`uv --version`), or Python 3.12 itself (`python3.12 --version`). The Berth installer needs one of the two, and Python 3.13 alone isn't enough. If neither is there, leave it: stage 2 installs uv once he says yes.
2. **Check this repository is at `~/louis-agentic-engineering`,** and up to date (`git -C ~/louis-agentic-engineering pull`). If he cloned it somewhere else, ask him whether to use that copy or clone a fresh one there. Never use Downloads, Desktop, Documents or iCloud.
3. **Don't install anything in this stage.**

## Stage 1 · Download the Berth kit

1. **If `~/berth-kit` already exists,** stop and ask him what it is before you touch it.
2. **Clone it where it will live for good:** `git clone https://github.com/mit-bach/berth-kit ~/berth-kit`.
   - Then check it isn't empty: `~/berth-kit/VERSION` exists, and `git -C ~/berth-kit describe --tags` shows `v3.1.0` or newer.
   - Tell him the version.
3. **If the clone fails or comes back empty,** remove the empty folder, and use the copy that ships in this repository instead:
   - from inside `~/louis-agentic-engineering/vendor/`, run `shasum -a 256 -c berth-kit-*.zip.sha256`, and stop unless it prints `OK`;
   - unzip it into his home folder, so its top folder becomes `~/berth-kit`;
   - read the version from `~/berth-kit/VERSION`.

## Stage 2 · Install Berth and its MCP servers, in this chat

You run the Berth kit's own onboarding yourself, here, with its commands run from inside `~/berth-kit`.

1. **Read `~/berth-kit/onboarding/cmux/START-HERE.md` all the way through,** then `~/berth-kit/docs/WHY.md`, before you change anything on his Mac. Follow its ground rules as well as these.
2. **Go through its decisions with him, one at a time, in plain words.** Recommend, but let him choose. They're written to `~/.berth-onboarding/DECISIONS.md` and settled there, so no later stage asks them again.
3. **Install it the way its section 5 says,** one stage at a time, each with `--dry-run` first and his go-ahead.
   - Claude Code is his agent, so install the `agents` stage and skip `grok`.
   - On a clone of the kit, skip "Keep a baseline", which is for a copy that came without git.
4. **Restart this chat the way its section 6 says,** so you get the new tools. Before you do:
   - write in `PROGRESS.md` that you're at stage 2, step 5;
   - tell him to send "continue" once the chat reopens.
5. **When it reopens, check it worked, and show him each result:**
   - everything its section 6 lists after the restart;
   - `claude mcp list` shows `berth` and `cmux-mcp`, both connected;
   - `berth sessions --json` lists his folder, and one row has `"you": true`. That row is this chat.

   If any of these fails, stop and tell him which one. Don't fix the Berth kit yourself.
6. **Walk him through `~/berth-kit/onboarding/cmux/FIRST-DAY.md`,** letting him press the keys himself.

From here on, Louis works inside cmux, and every session he starts is a row in Berth.

## Stage 3 · His tutor harness

It installs into `~/tutor/`, in a later version of this repository.
- **If this repository has `harness/INSTALL.md`,** follow it.
- **If not,** tell him it isn't ready yet, and go to "When you're done".

## Stage 4 · The store

It comes with the store kit, in its own repository, cloned into `~/code/store/`.
- **If this repository's README lists the store kit's repository,** follow the instructions there.
- **If not,** tell him it isn't ready yet.

## When you're done

1. **Tell him what's set up,** in a short list, and what isn't ready yet.
2. **Tell him what to read next:** `~/louis-agentic-engineering/ROADMAP.md`, then `harness/HARNESS.md`.
3. **Tell him how updates arrive:**
   - this repository gets them with `git -C ~/louis-agentic-engineering pull`;
   - Berth gets them through the "Update" prompt in `~/berth-kit/README.md`.

   Whenever there's a new version, he pastes the README's prompt again. Each stage checks what's already done and skips it.
