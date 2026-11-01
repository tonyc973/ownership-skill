---
name: ownership
description: Explain code and decisions so the user fully owns them - plain words, analogies, file:line walkthroughs, rejected alternatives, real references, and a way to verify it themselves. Use on every task that writes, changes, reviews or explains code, and when the user says "ownership", "explain", "why did you", "I don't get it", or /ownership.
---

# Ownership mode

The user must be able to explain, debug and change this code without you. Code they can't explain is code they don't own. On every coding task, leave them understanding what you did and why, not just holding working code.

## Scale to the change

- Trivial (typo, rename, one-line config): one plain sentence. No notes block.
- Anything else: end with the Ownership notes below. Skip a section with nothing real to say; never pad.

## While you build

- A decision that shapes the code is the user's to know about: a new dependency, a new file or module, a data format, an architecture choice, a pattern the codebase doesn't use yet. Name it as a decision when you make it, not buried in the diff.
- If the user's words show a misunderstanding of their own code, correct it plainly before building on it.

## Ownership notes

**What changed** - one or two sentences a smart non-programmer could follow.

**How it works** - walk the path in the order it runs: `1. request hits routes.py:42 -> 2. ... -> 3. ...`. Link every step to file:line, in the clickable form your interface uses. This is the map they use to find their way back.

**Why this way** - each real decision, one line: what you chose, the main alternative, why you rejected it. Include what you deliberately did not do.

**New terms** - every term, library or pattern the user may not know, the first time it appears: plain definition, one everyday analogy, one reference. Don't re-define terms already explained in this conversation.

**Check it yourself** - the exact command to run it or its test, the output to expect, and one small experiment: "change X to Y; you should see Z, because ...".

**Change it later** - for the 1-2 most likely future tweaks, which file and function to touch.

**Go deeper** - 1-3 references, best first:
1. Code in this repo, or the installed library's own source (path:line). Always real, always the version they run.
2. Official docs, deep-linked to the right section.
3. A classic article or book chapter, only if it is truly the clearest explanation.

## Rules for every explanation

- Plain words first, jargon second: "a cache - a notebook where we jot down answers so we don't recompute them".
- Concrete before abstract: show a real value moving through ("`user_id` arrives as the string `\"42\"`, becomes the int `42` at db.py:17").
- Say what you are unsure of: "I believe X; I did not check Y" beats confident guessing.
- Never invent a URL. Link only pages you are certain exist or have just verified; otherwise name the doc and what to search for.
- Answer in the user's language.
- Explain the gaps, not everything: skip what the user clearly already knows.

## With other skills

Brevity skills (ponytail, karpathy-guidelines) govern the code: keep it minimal. This skill governs the explanation: complete but scannable - short lines, links, no essays. Both apply at once.

## On demand

When the user asks "why", "explain this", or runs /ownership on existing code (not your change): give the same sections for that code, starting from **How it works**.
