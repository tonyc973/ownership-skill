# ownership

A Claude Code plugin that makes Claude explain its code and decisions so you **own** the code: you can explain it, debug it and change it without Claude.

## The problem

Claude writes working code you don't fully understand. Asking "explain everything simply, with references" works, but only if you ask in every prompt. A normal skill doesn't fix this either: Claude only loads a skill when it decides the task matches, so "explain well" rarely triggers.

This plugin is **always on**. A `SessionStart` hook loads the rules into every session (including after `/clear` and compaction), so you never have to ask.

## What you get

After any non-trivial change, Claude ends with short **Ownership notes**:

| Section | What it gives you |
|---|---|
| What changed | 1-2 sentences a non-programmer could follow |
| How it works | The path in the order it runs, each step linked to `file:line` |
| Why this way | What was chosen, the main alternative, why it was rejected |
| New terms | Plain definition + everyday analogy + one reference |
| Check it yourself | Command to run, expected output, one small experiment |
| Change it later | Where to touch for the likely next tweaks |
| Go deeper | 1-3 real references: your code or the installed library source first, then official docs |

It scales to the change: a typo fix gets one sentence, not an essay. It must never invent a URL. Big decisions (new dependency, new module, architecture) are named when they are made, not buried in the diff.

Run `/ownership` on any existing code to get the same walkthrough for code Claude didn't write.

## Install

```
/plugin marketplace add tonyc973/ownership-skill
/plugin install ownership@ownership-skill
```

Restart Claude Code. To turn it off: `/plugin disable ownership`.

## With other skills

Works alongside brevity skills like [ponytail](https://github.com/DietrichGebert/ponytail) and [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills): they keep the code minimal, this keeps the explanation complete but scannable.

## Without the plugin

Copy `skills/ownership/` to `~/.claude/skills/`, then add this line to `~/.claude/CLAUDE.md` to keep it always on:

```
@skills/ownership/SKILL.md
```

## License

MIT
