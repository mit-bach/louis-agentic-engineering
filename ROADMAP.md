# The roadmap

This is the whole plan, from the first setup to the finished store. Every step tells you three things: what works at the end, what you write yourself, and how you check it yourself. That holds for the last step as much as for the first.

## What you're building

You're building a small online store:
- a catalogue of products;
- a cart for each visitor;
- a checkout that never sells something that isn't there.

The hard part is the classic one. When two customers try to buy the last unit at the same moment, exactly one gets it, and the other gets a clean "out of stock". They must never get a crash, and the store must never end up with negative stock.

There are three things about how you build it:
1. **You write the backend by hand.** Dominik's rule: "you can't have the AI just write all the files." You can read documentation and ask an AI to explain things. But you write the files, so you understand how and why they work.
2. **The store is agent-first.** Each operation you write becomes a tool the same day. An AI agent can browse, fill a cart, check out and run the admin side, under exactly the same rules a person is held to.
3. **You build your own harness as you go.** Each milestone changes how your agents work, one piece at a time.

---

## The three threads

Every milestone has all three.

**1. Code.** The backend, written by you. That means:
- the database tables, as SQL migration files;
- the operations: products, sessions, the cart, checkout;
- the API routes, and what each error becomes;
- the locking that makes checkout safe;
- the tools that let an agent call your operations.

**2. Agent-first.** For each piece you build, you ask how an agent would use it. Then you connect your agent to it and watch what it does. A handful of principles come up again and again, each one taught when it first matters:
- **Rules live in the operations and the database,** so every caller has to pass them, agents included.
- **An agent's power is exactly its list of tools.** A customer's agent gets customer tools, and nothing more.
- **Errors are written for whoever reads them next,** and that's often a model deciding what to do.
- **Agents retry,** so anything that matters must be safe to repeat.
- **You measure an agent with tests of its behaviour (evals),** not by reading a few transcripts.

**3. Harness.** You have two harnesses:
- your **tutor harness**, the system in `~/tutor` that teaches you ([`mit-bach/louis-tutor`](https://github.com/mit-bach/louis-tutor));
- your **coding agent's setup**, inside the store's repo.

Each milestone makes one change to one of them, small enough that you can see its effect.

---

## The line: what you write, and what your agents do

This line holds at every step:
- **You write by hand, and can explain every line:** migrations, operations, routes, locking, and tool functions.
  - **Your agents, the tutor included, may:** explain, answer questions about documentation, review your changes and point out the problems, and quiz you.
  - **They may not** write or edit your backend code.
- **Given to you exactly, and you type it in:** config and glue. That's the Dockerfile, the compose file, the environment file, the database connection, the health check, and the tool server's skeleton. Each line is explained. There's nothing to learn by guessing at syntax, so you won't have to.
- **Your agent builds, and you specify and check:** the frontend (the web pages), at the end. You write the spec first, and you accept only what you've checked.

**How the line is held:**
- **At first, by a rule** in your agent's rules file.
- **From milestone 2, by a wall you build yourself:** a hook and a setting that make Claude Code refuse to edit your backend files. Turning a rule into a wall is one of the harness lessons.
- **By explain-back:** at each step, your tutor asks you three questions, and you answer them in your journal.

---

## How you'll build intuition: predict, run, compare

Intuition here means **knowing what something will do before you run it.** You'll train it on purpose.
- **Predict before every experiment.** You write a one-line guess in `PREDICTIONS.md` before you run it. Afterwards you write what happened, and why you were wrong if you were. The guesses come in three kinds:
  - **about the database:** "what happens if both buyers read the stock before either one writes?";
  - **about the agent:** "will it pick the right tool if the description says *X*?";
  - **about the harness:** "with only a rule, will the agent edit my file if I insist?"
- **A control experiment for every safeguard.** You take the safeguard away (the lock, the hook, the tool limit, the spec), predict what will happen, run it, and put it back.
- **Notice the parallels:** a rule in the database and a hook in your harness do the same job. Both are a wall every caller hits, not a polite request.
- **Keep score.** Your tutor tallies how often your predictions are right, separately for code, agent and harness. Watching that number rise is how you'll know the intuition is forming.

---

## How every step works

The guides are split into steps, and each step is one piece of building. Each step gives you:
1. **What works at the end.**
2. **What you write, and what's given.**
3. **The idea,** explained when you need it, plus **a worked example on a different problem:** a small library, with authors, books and loans. You see the shape without seeing your answer.
4. **The exact contract:** the file, the names, the behaviour, the exact error text, and one hint.
5. **An immediate check,** with exactly what passing looks like.
6. **"Decide first",** where there's a real design choice. You get the options and the facts. You write your choice and why in `JOURNAL.md` before you open the answer.

**A step is done when all of these are true:**
1. `make check M=<n>` passes, and the guide shows you exactly what passing looks like.
2. The one manual check works.
3. You've asked your reviewer to look at your changes, and you've fixed or answered each thing it found.
4. Your tutor's three questions are answered in `JOURNAL.md`.
5. `PREDICTIONS.md` has this step's guesses, each with what happened.
6. It's committed, and `git status` shows exactly the files the guide lists.

**Your tutor opens the next step only once your journal has this one's entries.**

---

## The courses and milestones

These estimates are for full days of work.

### Setup · Your agentic development environment (half a day)
- **What works:** one prompt from `README.md` downloads every repository and installs Berth and its MCP servers inside cmux. From then on, every session you start is a row in Berth.
- **Done:** your agent's checks in `SETUP.md` all pass, the chat you're in shows up in Berth, and two agents it started for you ("Scout" and "Critic") have handed work to each other and back to you.

### Course 00 · Meet your harness (half a day)
- **Lesson 1:** you read the harness's map, predict which file controls three behaviours, and check.
- **Lesson 2:** you move one of the tutor's settings (a slider), predict how the next lesson changes, and compare.
- **Then:** you file your sessions in Berth folders, one per course.

### M0 · Setup, and an agent that follows your rules (half a day)
- **What works:**
  - your API and its own Postgres database run in Docker;
  - `GET /health` answers that both are up;
  - your repo is on GitHub.
- **Harness:** you write your coding agent's rules file, `AGENTS.md`, in your own words.
  - **Control:** ask your agent to write a backend file, once with the rules file and once without it. Predict first.

### M1 · Products, and the store's first tools (2 days)
- **You write:**
  - the products table;
  - a seed of at least 8 products, in a catalogue you choose;
  - the operations to list, get and create a product;
  - their routes, their commands, and their tools.
- **Decide first:**
  - what identifies a product;
  - how to store money;
  - which fields are required;
  - real defaults or none;
  - where the "never negative" rules live.
- **Agent-first, three ways in:** the same operations become HTTP routes, a command line (`./store products list`, built for a program to read: JSON out, errors on stderr, exit codes that mean something), and agent tools. You ask your agent to add three products to your store, once through the tools and once through the command line.
- **Harness:** your first tool server, connected to Claude Code.
  - **Control:** a vague tool description against a precise one.
- **Done:** `make check M=1` passes. It checks the answers your API gives (201, 404, 409, 422), your commands' output and exit codes, your tools, that every route has a command and a tool, and that your operations don't depend on the web framework.

### M2 · The admin side, and your first race (2 days)
- **You write:** edit, delete and adjust stock.
- **Decide first:**
  - delete a product, or archive it, given that orders will point at products;
  - how to change stock safely when two admins do it at once.
- **Agent-first:** the admin tools.
- **Harness: the wall.** A hook and a setting refuse edits to your backend files, for both your coding agent and your tutor.
  - **Control:** ask each agent to "fix the bug" in one of your files, with the rule only, and then with the wall.
- **Done:** `make check M=2` passes. That includes a race:
  - 50 simultaneous "+1" and 50 simultaneous "−1" stock changes must leave the stock exactly where it started;
  - removing more than is in stock must give a clean 409, with nothing changed.

### M3 · Visitors and carts (1.5 days)
- **You write:**
  - visitor sessions, each one a random token that expires after an hour;
  - the check that reads the token on every request;
  - the cart.
- **Decide first:**
  - should adding to the cart check stock?
  - what happens to a cart line whose product gets archived?
  - how does a customer's agent hold its session?
- **Agent-first:** the cart tools.
  - **Prediction:** asked to shop as two different customers, does your agent keep their carts apart?
- **Harness:** your reviewer becomes a skill.
  - **Control:** whether a vague description or a precise one makes it trigger.
- **Done:** `make check M=3` passes. It covers:
  - two visitors' carts stay separate;
  - a missing token, a made-up token and an expired token each get the exact 401 message;
  - quantity 0 is refused;
  - adding the same product twice sets its quantity, rather than adding a second line.

### M4 · Checkout, and two buyers at once (2 days)
- **You write:** checkout, as one transaction:
  - lock the products involved;
  - check that every line has enough stock;
  - write the order with the prices paid;
  - lower the stock;
  - empty the cart.

  If any line falls short, nothing changes at all.
- **Decide first:**
  - should orders be tied to sessions, given that expired sessions get deleted?
  - is one update per item enough, or do you need to lock first?
  - where does the total come from?
- **Agent-first:** the checkout tool.
  - **Prediction:** two agents are told to buy the last unit at once. What does the losing agent tell its customer?
- **Harness:** you audit your own tutor harness. You read your rule log, Berth's list of your sessions and two session transcripts. Then you write half a page on which changes held and which didn't. If you haven't changed a rule yet, the audit has to produce one change. You also compact a session through Berth for the first time.
- **Done:**
  1. **`make check M=4` passes.** It covers:
     - a normal checkout;
     - an empty cart;
     - not enough stock, with nothing changed;
     - an order keeping its prices after a price changes;
     - a total that ignores anything the client sends.
  2. **The race test:** `python checks/race_test.py --rounds 20` prints `20/20 rounds: one 201, one 409, stock 0`, with no 500 errors and no negative stock.
  3. **The control:** you remove your lock, predict, run the race again, write down what happened and why, and put the lock back.
  4. **The deadlock test:** two carts hold the same two products, added in opposite orders, and check out together for 20 rounds with no errors.

### M5 · Agent-first, for real (2 days)
- **You write:**
  - **Checkout that's safe to repeat.** A repeated request with the same key returns the first order, instead of placing a second.
  - **Errors returned to agents as clear messages.**
- **Decide first:**
  - should an agent ask its customer before it checks out? A customer's click is their consent, so what's the agent's equivalent?
  - what exactly does a customer's agent get?
- **Agent-first:**
  - **Tool scope:** an agent with customer tools only, against one that also has admin tools. Predict what each one does when asked to "get me a better price".
  - **Evals:** five shopping tasks, run automatically and checked in the database. You rewrite your tool descriptions, run them again, and see the score move.
- **Done:**
  - `make check M=5` passes, including the repeat test: the same key sent twice, and twice at the same instant, gives exactly one order;
  - the tool check passes: every customer and admin action has a tool;
  - your eval scores, before and after, are in your journal.

### M6 · The frontend, built by your agent (2 days)
- **You write the spec first:**
  - each page;
  - what it calls;
  - where the session token lives;
  - what the page shows for each error.
- **Your agent builds it** in Next.js, with Tailwind and shadcn.
- **Harness:** you review your agent's plan before it builds.
  - **Control:** the same request with no spec, on a throwaway branch.
- **Done:**
  1. The build and the linter pass.
  2. **A walkthrough:**
     - two private browser windows have separate carts;
     - when both windows buy the last unit, one gets the confirmation and the other the out-of-stock message;
     - a price change shows on the store, while an old order keeps its old price;
     - an expired session recovers on its own.
  3. **In your journal:** where the token is kept and sent, and one thing you changed in your agent's work, and why.

### Capstone · A harness of your own
1. **First, one fork on purpose.** You fork one course's tutor into your other course's folder. Predict what it does, then watch it carry the first course's conversation into a folder whose rules say otherwise. It's a lesson about context, and why tutors never start as forks.
2. **Then your own harness.** You build a small harness from scratch for one optional spec of your choice, using what you kept and dropped from your tutor harness.

### Finished means
- From a fresh copy of your repo, every check passes.
- A 15-minute demo to Dominik:
  - the race test live, with the lock removed and put back;
  - an agent placing an order;
  - your eval scores;
  - the two-window test;
  - three questions answered without notes.

**About 13 working days in all.**

---

## Your tutor harness, in short

Your tutor harness lives in one folder, `~/tutor/`, and it's yours.
- **Tutors:** each course gets a tutor. It's a Claude Code session in that course's folder, started for you as a Berth session and filed in Berth's `Tutor/` folder.
- **The harness keeper:** a session started in the harness folder itself. It helps you change the harness, and it lists, starts and files your sessions. Waking, sleeping and closing them stay your calls.

When a tutor does something you don't like, you're the one who fixes it:
1. You guess which rule caused it, and check.
2. You predict what changing it will do.
3. You change it in the narrowest place it fits.
4. You log it, and see whether you were right.

That loop is how you'll come to build and change harnesses with confidence. Start with `~/tutor/README.md`, then `~/tutor/orchestrator/ORCHESTRATOR.md`.
