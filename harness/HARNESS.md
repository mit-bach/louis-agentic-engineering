# Your harness: the map

This is your tutor harness. It's yours to read and change. This page says which file does what, when each moving part runs, and what the words in it mean.

**Reading the rulebook:** `CLAUDE.md` is written to the agent, so in it "you" is the agent and "he" is you, Louis.

## Which file does what

| File | Its job |
|---|---|
| `CLAUDE.md` | The rulebook |
| `HARNESS.md` | This map |
| `RULES-LOG.md` | Every rule change |
| `CHANGES.md` | Harness updates |
| `formats/` | Lesson shapes |
| `student/PROFILE.md` | You, as a learner |
| `courses/` | One folder each |
| `tools/` | Scripts and the hook |
| `.claude/` | Settings and skills |

- **`CLAUDE.md`, the rulebook.** It sets how every agent in this harness behaves. A session started here is your harness keeper, and a session started in a course folder is that course's tutor.
- **`RULES-LOG.md`:** every change to a rule, with your guess at the cause, your prediction, and what actually happened.
- **`CHANGES.md`:** what each harness update from us changes, and why. You decide what to merge.
- **`formats/`:** how a lesson is shaped. `concept.md` covers a topic from zero, and `work-through.md` covers building something in checked pieces.
- **`student/PROFILE.md`:** your preferences, which you write, and habits the tutors notice.
- **`courses/<course>/`:** each course's own rules (its `CLAUDE.md`), its notes, mastery, lessons, and your replies.
- **`tools/`:**
  - `new-course.sh` makes a course folder;
  - `session_state.py` is the startup hook;
  - `lint-lesson.py` checks a lesson;
  - `tx.py` condenses a session's transcript.
- **`.claude/`:** this folder's settings, and the `new-course` skill. Each course folder gets its own `.claude/settings.json` too, made by `new-course`, because Claude Code reads settings only from the folder a session starts in. Without it, a tutor in its course folder never runs the hook.

## When things run

| When | What runs |
|---|---|
| A session starts | The hook |
| After a compaction | The hook |
| You run `new-course` | The skill |
| Before a lesson ships | The linter |

**The hook** runs whenever a tutor session starts, resumes, or comes back from a compaction, from the course folder's own settings. It tells the tutor where its course stands: the "Where we are" note, the newest lesson, and your newest reply. Rules never come from the hook. They're always in the `CLAUDE.md` files.

## Your sessions, in Berth

Berth is the list of every agent session on your Mac, filed in folders, and the way you start, wake, fork and compact them. Your harness uses it like this:
- **Each tutor is a Berth session in its course's folder,** titled with the course's session name and filed in the Berth folder `Tutor/`. `new-course` starts it there. A tutor started anywhere else loads the wrong rules.
- **To continue a course,** wake its session in Berth, or start a new one in the course folder. The files are the memory, so either works.
- **Forks are for experiments,** such as "what would this tutor do at hand-holding 2?", never for starting a tutor. A fork carries its parent's whole conversation into the new session.
- **Compact a session through Berth,** never by pasting `/compact` into it. A pasted `/compact` arrives as an ordinary message, and the session may take the note as its job.
- **A prompt or a message.** A prompt placed in a session's input box is read as you speaking: it starts or redirects the work. A message from another agent runs alongside the work. Use a prompt only when you mean to steer.
- **Sessions are yours to close.** The keeper lists, starts and files them; waking, sleeping and closing are your calls.

## Words you'll meet

- **Harness:** everything around a model that shapes what it does: its rules, tools, hooks, skills, settings and records. This folder is one.
- **Session:** one conversation with Claude Code. It starts in a folder, and that folder decides which `CLAUDE.md` files it loads.
- **Context:** everything the model can see at a given moment: the rules it loaded, what was said, the files it read.
- **Compaction:** when a session gets long, Claude Code replaces the earlier conversation with a summary to make room. A summary loses detail, so the files are the real memory.
- **Hook:** a script Claude Code runs at a set moment, such as when a session starts or before a tool is used. It can add information, or block an action.
- **Skill:** a packaged set of instructions an agent loads when a task matches its description.
- **Transcript:** the full record of a session, saved in `~/.claude/projects/`. `tools/tx.py` makes one readable.
- **Orchestrator:** an agent, or a person, that runs other agents: setting their rules, checking their work, and changing them when they fail. In this harness, that's you, with the harness keeper to help.
- **Berth:** the list of your agent sessions, in folders, and the way you start, wake, fork and compact them.
- **Fork:** a new session that starts with a copy of another session's whole conversation.
- **Slider:** a 0–10 setting in a course's header, for hand-holding, education or exploration. It's the safest knob to turn first.
