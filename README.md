# .agents

My global rules for coding agents: one `AGENTS.md` that Claude Code, Codex and Cursor all read.

## Setup

Paste this into Claude Code, Codex or Cursor:

```text
Install the agent rules from https://raw.githubusercontent.com/rishiskhare/.agents/main/AGENTS.md: download them to ~/.agents/AGENTS.md, link ~/.codex/AGENTS.md to that file, and add the line @~/.agents/AGENTS.md to ~/.claude/CLAUDE.md if it isn't there. If I use Cursor, copy the rules to my clipboard for its User Rules. Keep what's already in my files, and show me each change and wait for my yes before making it.
```

This sets up:

| Agent | Reads the rules from |
| --- | --- |
| Claude Code | `~/.claude/CLAUDE.md`, which imports `~/.agents/AGENTS.md` |
| Codex | `~/.codex/AGENTS.md`, a link to `~/.agents/AGENTS.md` |
| Cursor | A pasted copy in User Rules |

To set it up without an agent, copy `AGENTS.md` into those places by hand.

## Check

In each agent, start a new session and ask "What are my global rules? List the section headings." The answer should match the `##` headings in `AGENTS.md`. If Codex doesn't show them, remove `~/.codex/AGENTS.override.md`, which takes priority.

## Update

Paste the setup prompt again. If you cloned this repo to edit the rules, run `git pull` in it instead.

## Remove

Delete `~/.agents/AGENTS.md` and `~/.codex/AGENTS.md`, remove the `@~/.agents/AGENTS.md` line from `~/.claude/CLAUDE.md`, and clear Cursor's User Rules.
