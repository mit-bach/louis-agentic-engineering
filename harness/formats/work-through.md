# Format: work-through

**Use it for** building something real in small, checked pieces, where he writes the parts that are his to write.

**Budget:** one build step per lesson. A step ends at a check he can run.

## Three kinds of content, taught three ways

1. **Mechanics are given exactly.** Setup, config and glue are parts where there's nothing to decide and nothing to learn by guessing. Give him:
   - the file;
   - its full content;
   - what each line does, in a sentence;
   - the command to run, with its exact expected output.
2. **Design is decided by him.** When there's a real choice, give him:
   - the options;
   - the facts that decide between them;
   - "write your choice and why in `JOURNAL.md` first".

   The tutor's own view comes after, folded in a `<details>` block below the place where he writes his choice.
3. **His own code is written by him,** in small pieces. For each piece:
   1. **The idea,** explained at the moment he needs it.
   2. **A worked example on a different problem,** so he sees the shape without seeing his answer.
   3. **The exact contract:** the file, the names, the signatures, the behaviour, the exact error text, and one hint.
   4. **An immediate check:** the command, and exactly what passing looks like.

## The line

The course's `CLAUDE.md` names the files that are his. The tutor never writes or edits them, and never shows a full solution. When it reviews his code, it names the problem and where it is, then lets him fix it.

## When the course comes with tested guides

Some courses come with a kit: guides, checks and a contract, already tested. Then:
- the lessons are the kit's guides, served in order, one step at a time;
- the tutor may add a bridge of two or three sentences at the top of a step, tying it to his last journal entry. It never rewrites a guide;
- the tutor's own writing is its reviews, the examiner's questions, and its answers;
- a problem in a guide goes back to whoever wrote the kit. A problem in how the tutor behaves is his to fix in his harness;
- **records are named by step,** not by lesson number. For step 2 of milestone 3:
  - `lessons/M3-2.md` holds the tutor's bridge, its review and the examiner's questions;
  - `replies/M3-2.md` holds what he says in chat, verbatim;
- **his reply for a step is his `JOURNAL.md` entries for it** (in his project), plus anything he says in chat. The next step opens once the journal holds that step's entries;
- the guides arrive tested, so the tutor doesn't re-run their commands. Its own bridges and reviews still get re-read against his words.

## Each step ends the same way

1. **The checks pass,** and the step shows exactly what passing looks like.
2. **One manual check,** step by step.
3. **His journal,** with his decisions, the review's findings and what he did about each, and his answers to the questions.
4. **His predictions,** each written with what actually happened.
5. **A commit,** saying which files `git status` should and shouldn't list.

## If he's stuck

1. The idea again, said differently.
2. The worked example's shape, side by side with his contract.
3. The exact command and output to send to whoever is helping him.

## Before it goes out

Build the step in a scratch copy first, never in his own folders, and run every check and command in it. Every expected output in the lesson is real. When a check should catch a mistake, break the code on purpose and see that it does.

## Checklist

- [ ] It's one build step, ending at a check he can run.
- [ ] Mechanics are given exactly, with real expected output.
- [ ] Every design choice is his, written down before the tutor's view.
- [ ] Each piece of his code has an idea, a worked example on another problem, a contract, and an immediate check.
- [ ] No file that's his is written or shown solved.
- [ ] Everything was built and run in a scratch copy, and the checks catch what they should.
- [ ] Questions: at most 3. Parked is there.
- [ ] The linter passes.
