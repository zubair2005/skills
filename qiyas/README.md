# Qiyas (قياس)

A skill for AI coding agents. When your agent reaches a decision you never spelled out, it looks for an earlier chat, correction or pull request where you already decided something similar. It works out why you decided it, and reuses the decision only if that reason still holds.

It is inspired by qiyas, the method of analogy in usul al-fiqh (the principles of Islamic jurisprudence). Jurists use it for cases the Quran and Sunnah don't directly address: they find a settled case, identify the reason for its ruling, and carry the ruling over when the new case shares that reason.

## What it does

It looks in your `AGENTS.md` or `CLAUDE.md`, memory notes, past Codex and Claude Code chats, and pull requests, reading your own messages and corrections first.

For a decision that matters, it keeps a short evidence record:

1. Asl, the earlier case: link or thread ID, date and circumstances.
2. Hukm, the earlier decision: what you actually chose, corrected, prohibited or approved.
3. ʿIllah, the reason: why that decision fits now, marked as stated by you or inferred.
4. Farʿ, the new case: the current decision and the verified facts.
5. Differences: anything that changed (product, person, environment, timing, reversibility, stakes, authority) and could break the analogy.

When the reason carries over and the choice is safe and reversible, it goes ahead and tells you in one line:

```text
Qiyas: following your 3 Oct decision in "Fix login" (ticket ID in branch names), since this is the same repo.
```

When it can't establish the reason, it asks you one precise question with its recommendation, and keeps working on anything that doesn't depend on the answer.

## Limits it keeps

- An explicit instruction that still fits applies directly, and a newer instruction beats an older one.
- Two independent matching decisions from you can set a working default, but only for safe, reversible choices. Assistant summaries and guesses never count as precedents.
- A past approval to deploy, merge, publish, spend money, change a customer account or delete data never authorizes a new one.
- A restriction carries over to riskier cases: if you blocked merging without tests, it won't deploy without tests either. A permission never stretches that way.
- An instruction tied to an event expires with the event.

## Install

In Codex, ask the built-in installer:

```text
$skill-installer install https://github.com/zubair2005/skills/tree/main/qiyas
```

It lands in `~/.codex/skills/qiyas`. Codex usually picks up new skills on its own; restart it if `qiyas` doesn't appear.

In Claude Code, copy the `qiyas` folder into `~/.claude/skills/`.

Any other agent that supports skills can install it from the link:

```text
Install the AI agent skill at https://github.com/zubair2005/skills/tree/main/qiyas
```

## Recommended usage

Let it run by itself. Codex uses a skill when a request matches its description, and this one is written for vague or dictated requests, repeated questions, and decisions you have settled before.

Call it directly when you want it for sure: type `$qiyas` in Codex or `/qiyas` in Claude Code, followed by your request.

```text
$qiyas start a branch for the login bug
```

If you've asked for the ticket ID in branch names before, it does that again, and it uses the login bug's own ticket instead of reusing an old one.

To make it the default, add this to your `AGENTS.md` (Codex) or `CLAUDE.md` (Claude Code):

```text
Use the qiyas skill whenever understanding my intent or choosing an approach depends on my earlier decisions, corrections or preferences. Start with the closest relevant chats and my original messages, and widen the search only when evidence is missing or conflicts. Check for newer corrections and current facts, and never treat an old approval as permission for a new external action.
```

It works best when the agent can see your history: past chats, memory notes and pull requests.

## About the name

The skill borrows the structure of qiyas for everyday work decisions. It gives no religious rulings, and your preferences carry no religious authority.
