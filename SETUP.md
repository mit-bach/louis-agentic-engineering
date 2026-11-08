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
- `~/tutor/`: his tutor harness;
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
   - **Then check it has content.** Cloning an empty repository still succeeds, so judge by what's there: `git -C ~/berth-kit rev-parse --verify -q HEAD` answers, `~/berth-kit/VERSION` exists, and `git -C ~/berth-kit describe --tags` shows `v3.1.0` or newer.
   - **Check that `v3.1.0` is the reviewed tree:** `git -C ~/berth-kit rev-parse 'v3.1.0^{commit}'` must print `226f723287df13d023fa4897b999b2ce7ce5256d`. If it prints anything else, treat the clone as failed (step 3).
   - Tell him the version.
3. **If the clone fails, comes back empty, or fails a check above,** stop. Delete `~/berth-kit` only if you just made it and it holds nothing but git's own folder. Tell him exactly what failed, and to send it to Dominik. Don't install Berth from anywhere else.

## Stage 2 · Install Berth and its MCP servers, in this chat

You run the Berth kit's own onboarding yourself, here.

**Never `cd` into the kit.** If you do, Claude Code can record `~/berth-kit` as this chat's folder, and Berth's restart then reopens the chat there instead of where he started it. So run every kit command by its full path (`~/berth-kit/tools/install.sh cmux --dry-run`, `python3 ~/berth-kit/tools/doctor.py`), or in a subshell (`(cd ~/berth-kit && tools/install.sh cmux --dry-run)`). START-HERE's paths are relative to the kit, so read every `tools/…` and `docs/…` in it as `~/berth-kit/tools/…` and `~/berth-kit/docs/…`.

1. **Read `~/berth-kit/onboarding/cmux/START-HERE.md` all the way through,** then `~/berth-kit/docs/WHY.md`, before you change anything on his Mac. Follow its ground rules as well as these.
2. **Go through its decisions with him, one at a time, in plain words.** Recommend, but let him choose. They're written to `~/.berth-onboarding/DECISIONS.md` and settled there, so no later stage asks them again.
3. **Install it the way its section 5 says,** one stage at a time, each with `--dry-run` first and his go-ahead.
   - Claude Code is his agent, so install the `agents` stage and skip `grok`.
   - **"Keep a baseline":** skip it. Your copy is a git clone, so `git -C ~/berth-kit status` already shows any change.
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

## Stage 3 · Show me what it can do

Now run agents for him from this one chat, using the two MCP servers you just installed: `berth` to start, file and track sessions, and `cmux-mcp` to watch them work. Read the `berth` and `cmux-claude` skills first (`~/.claude/skills/`); they say exactly how to start a session, place its job and watch for it to finish. This is the first taste of how Dominik's orchestrators run whole teams of agents, and it's where that grows later.

**Before you start:**
- Tell him what's about to happen. Each new session uses his Claude plan, and he says yes before you start any.
- Any permission prompt in a session you start is his to answer in that session's pane. The only dialog you clear yourself is the folder-trust question, after saying so.

**The run:**
1. **Make the places:** a Berth folder `Playground` (through the `berth` MCP), and a work folder `~/louis-playground/`.
2. **Start two Claude sessions at once** in `~/louis-playground/`, filed in `Playground`, each with its job placed from a file:
   - **"Scout":** "Write `transactions.md`: a one-page explanation, for a beginner, of what a database transaction is and why two people buying the last item at once needs one. Use one small example. When you're done, write the single word `done` in `scout.stop`."
   - **"Critic":** "Wait until `scout.stop` says `done`. Then read `transactions.md` and write `review.md`: the three places a beginner would get lost, and a one-line fix for each. When you're done, write `done` in `critic.stop`."
3. **Watch them work.** Look at each one's screen with `cmux-mcp` every so often, and tell him in a line what each is doing. Have him press ⌘⇧B to see both sessions in Berth's `Playground` folder.
4. **When both stop files say `done`,** read `transactions.md` and `review.md`, and show him the two together. Then explain what just happened:
   - two agents worked in parallel and handed off through files;
   - this chat started them, watched them and collected their results, without typing into them;
   - a prompt placed in a session's pane is read as his voice, while a message runs alongside the work.
5. **Show him one Berth move on them,** with his yes: fork "Scout", or put both to sleep and wake one. Let him do it from the Berth screen if he'd like to.
6. **Leave the sessions to him.** Tell him how to sleep them or move them to Berth's trash, and never close them yourself.

Note in `PROGRESS.md` when this stage is done.

## Stage 4 · His tutor harness

His tutor system, ported from the one Dominik uses every day: a rulebook, lesson formats, a startup hook, course tools, and two standing sessions in Berth, Tutor Orch and Tutor Prime. It lives in its own repository, [`mit-bach/louis-tutor`](https://github.com/mit-bach/louis-tutor), cloned into `~/tutor/`.

1. **Clone it:** `git clone https://github.com/mit-bach/louis-tutor ~/tutor`. If `~/tutor` already exists and is this harness, `git -C ~/tutor pull` instead.
2. **Follow `~/tutor/INSTALL.md`** all the way through. It runs the harness's self-check, makes the Berth folder `Tutor`, starts and primes Tutor Orch and Tutor Prime, and has him fill in his profile.
3. **Then tell him:** from now on, he starts a course by opening "Tutor Orch" in Berth and saying what he wants to learn.

## Stage 5 · The store

It comes with the store kit, in its own repository, cloned into `~/code/store/`.
- **If this repository's README lists the store kit's repository,** follow the instructions there.
- **If not,** tell him it isn't ready yet.

## When you're done

1. **Tell him what's set up,** in a short list, what the agents made in `~/louis-playground/`, and what isn't ready yet.
2. **Tell him what to read next:** `~/louis-agentic-engineering/ROADMAP.md`, then `~/tutor/README.md`.
3. **Tell him how updates arrive:**
   - this repository gets them with `git -C ~/louis-agentic-engineering pull`;
   - his tutor harness gets them with `git -C ~/tutor pull`, merged one change at a time with Tutor Orch, because his own edits live there too;
   - Berth gets them through the "Update" prompt in `~/berth-kit/README.md`.

   Whenever there's a new version, he pastes the README's prompt again. Each stage checks what's already done and skips it.
