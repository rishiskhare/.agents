# .agents

My global rules for coding agents: one `AGENTS.md` that Claude Code, Codex and Cursor all read. I clone this repo on each machine, so `git pull` updates every agent.

To just try the rules, copy `AGENTS.md` into the files in the table below.

## Setup

Paste this into Claude Code, Codex or Cursor:

```text
Set up the agent rules from https://github.com/rishiskhare/.agents: clone it to ~/.agents, link ~/.codex/AGENTS.md to ~/.agents/AGENTS.md, and add the line @~/.agents/AGENTS.md to ~/.claude/CLAUDE.md. If I use Cursor, copy AGENTS.md to my clipboard for its User Rules. Check what already exists first, keep existing files, and show me each change and wait for my yes before making it.
```

Or run these on macOS or Linux, then paste `AGENTS.md` into Cursor Settings → Rules → User Rules:

```bash
git clone https://github.com/rishiskhare/.agents.git ~/.agents
mkdir -p ~/.codex ~/.claude
ln -s ~/.agents/AGENTS.md ~/.codex/AGENTS.md
printf '\n@~/.agents/AGENTS.md\n' >> ~/.claude/CLAUDE.md
```

On Windows, or if `~/.agents` already exists (`npx skills` installs skills there), use the prompt.

| Agent | Reads the rules from |
| --- | --- |
| Claude Code | `~/.claude/CLAUDE.md`, which imports `~/.agents/AGENTS.md` |
| Codex | `~/.codex/AGENTS.md`, a link to `~/.agents/AGENTS.md` |
| Cursor | A pasted copy in User Rules |

## Check

In each agent, start a new session and ask "What are my global rules? List the section headings." The answer should match the `##` headings in `AGENTS.md`. If Codex doesn't show them, remove `~/.codex/AGENTS.override.md`, which takes priority.

## Update

Run `cd ~/.agents`, then `git pull`, then paste `AGENTS.md` into Cursor again.

## Remove

Delete `~/.codex/AGENTS.md`, remove the `@~/.agents/AGENTS.md` line from `~/.claude/CLAUDE.md`, and clear Cursor's User Rules.
