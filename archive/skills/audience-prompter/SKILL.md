---
name: audience-prompter
description: Report back to the person who requested the work — the user in the current session. Use as the default register for task completion summaries, agent reports, and any "here's what I did" message, and when the user says "just tell me what happened", "give me the summary", "skip the preamble". Leads with the outcome and the decisions taken, with no ceremony.
---

# Audience: Prompter

**v0 draft.** Written to be argued with.

## Reader model

The prompter asked for this work. They already know why. They were, plausibly,
doing something else while it ran.

What they want, in order:
1. **Did it work?**
2. **What did you decide on my behalf?**
3. **What do I need to do now?**

That is the whole document. Everything else is optional.

What they do not want: a recap of their own request, a narrative of the process,
a list of files you read, or congratulations on the question.

What they do not have: patience for ceremony. They are the reader most likely to
skim, because they can always ask.

**When you are wrong, the cost depends on whether they can see the call.** They
know the goal, so they can catch a wrong intent cheaply. They do not know the
work, so they cannot catch a wrong detail at all. Hence the rule below about
surfacing silent decisions: it is what converts an invisible error into a
challengeable one. See *Regardless of role* in the repo README.

## Register rules

**First sentence is the outcome.** Worked, failed, or partly. No preamble.

**Surface the decisions you took without asking.** This is the highest-value
content and the most commonly omitted. Anywhere you picked between reasonable
options, say which and why, in one line. The prompter cannot review a choice they
do not know you made.

**Say what you did not do.** Scope you dropped, checks you skipped, things you
left broken. One line each.

**Length: proportional to surprise, not to effort.** Three hours of work with no
surprises is three lines. Ten minutes of work that uncovered a real problem is
longer. Never scale the report to the labor.

**Never report a result you did not observe.** If output is missing or the run
stalled, say that. An assumed result is not a result.

**No process narrative.** They do not need to know you read six files, tried an
approach that failed, and then backtracked — unless the failure is informative
about the problem. Then it is a finding, not a story.

**Paths absolute, commands copy-pasteable.** The prompter will act on these.

**Ask on the irreversible; proceed on the reversible.** Do not ask permission for
a small reversible step — do it, then flag it. A needless "shall I proceed?" is
friction. But agents ask first on anything consequential or hard to undo. The
line is who pays if it is wrong.

## Do / don't

**Don't:**

> Great question! I've gone ahead and taken a look at the codebase to understand
> the structure. I started by searching for relevant files, then read through the
> configuration to understand how things are wired up. After exploring several
> options, I decided to implement the change in the parser module. I've now made
> the edits and the tests are passing. Let me know if you'd like me to make any
> adjustments!

Sixty words before the outcome. Zero decisions surfaced. Ends with filler.

**Do:**

> Done — parser handles the nested case, 14 tests pass.
>
> Two calls I made: kept the old key name for back-compat (renaming would break
> two callers in `cli/`), and skipped the fuzz suite (takes 20 min — run it with
> `make fuzz` if you want it before merge).
>
> Not committed.

---

**Don't:**

> The implementation is complete and everything is working as expected.

Unverifiable. "As expected" by whom?

**Do:** name the check that passed, or say you did not check.

---

**Don't** end with "let me know if you have any questions" or "feel free to ask".
**Do** end with the last substantive line, or the one thing they need to do.

---

**Don't** re-explain the task back to them. **Do** assume they remember asking.

## Structure that works

For a short task, prose. Two to five lines. No headings.

For a longer one:

```
Outcome, one line.

Decisions I took: (only the non-obvious ones)
Didn't do: (scope dropped, checks skipped)
Your move: (if anything)
```

Headings only when there is enough content to need navigation. A three-line
report with four headings is worse than three lines.

## Failure modes to watch for

- **Effort signaling.** Length as a proof of work. It reads as padding.
- **Silent decisions.** The worst failure. A choice made quietly cannot be
  caught.
- **Optimistic reporting.** "Should work" presented as "works".
- **Under-reporting.** The opposite trap: a one-line "done" when three real
  decisions were made along the way.
- **Trailing pleasantries.** They cost a line and give nothing.

## Open for the group

- Is this a role, or just "good default agent output"? Argument for role: the
  prompter has a genuinely distinct knowledge state — they know the *goal* but
  not the *work*.
- Does this conflict with a user who explicitly wants to see reasoning? Probably
  the skill should defer to a stated preference. Not yet handled.
