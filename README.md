# .agents

My global rules for coding agents: one `AGENTS.md`, shared by Claude Code, Codex and Cursor.

## Setup

**Easiest:** paste this into Claude Code, Codex or Cursor:

```text
Set up my agent rules from https://github.com/rishiskhare/.agents by following its README for my OS. First check what already exists, show me every command, and wait for my yes. Never overwrite or delete a file without asking. When done, run its "Check" step and copy AGENTS.md to my clipboard for Cursor.
```

**By hand:** run the command for your OS, then paste `AGENTS.md` into Cursor Settings → Rules → User Rules.

macOS / Linux:

```bash
git init -b main ~/.agents && git -C ~/.agents remote add origin https://github.com/rishiskhare/.agents.git && git -C ~/.agents pull origin main && git -C ~/.agents branch -u origin/main && mkdir -p ~/.codex ~/.claude && ln -s ~/.agents/AGENTS.md ~/.codex/AGENTS.md && echo '@../.agents/AGENTS.md' >> ~/.claude/CLAUDE.md
```

Windows (PowerShell; the Codex link needs Developer Mode or an admin shell):

```powershell
git init -b main "$HOME\.agents"; git -C "$HOME\.agents" remote add origin https://github.com/rishiskhare/.agents.git; git -C "$HOME\.agents" pull origin main; git -C "$HOME\.agents" branch -u origin/main; New-Item -ItemType Directory -Force "$HOME\.codex","$HOME\.claude" | Out-Null; cmd /c mklink "$HOME\.codex\AGENTS.md" "$HOME\.agents\AGENTS.md"; Add-Content "$HOME\.claude\CLAUDE.md" '@../.agents/AGENTS.md'
```

| Agent | How it gets the rules |
| --- | --- |
| Claude Code | `~/.claude/CLAUDE.md` imports them with `@../.agents/AGENTS.md` |
| Codex | `~/.codex/AGENTS.md` links to them |
| Cursor | A pasted copy in User Rules |

Existing files in `~/.agents`, like skills from `npx skills`, are kept. In WSL, use the macOS / Linux command.

## Check

In each agent, start a new session and ask "What are my global rules? List the section headings." The answer should match the `##` headings in `AGENTS.md`.

## Update

Run `git -C ~/.agents pull`, then paste `AGENTS.md` into Cursor again.

## Troubleshooting

- **Pull fails because `AGENTS.md` exists:** rename yours, rerun the command, and merge anything you need into the new one.
- **Link fails because `~/.codex/AGENTS.md` exists:** move it aside and rerun. On Windows without Developer Mode, copy the file instead: `Copy-Item "$HOME\.agents\AGENTS.md" "$HOME\.codex\AGENTS.md"`, and copy it again after each update.
- **Codex ignores the rules:** remove `~/.codex/AGENTS.override.md`, which takes priority.

## Remove

Delete `~/.codex/AGENTS.md`, remove the `@../.agents/AGENTS.md` line from `~/.claude/CLAUDE.md`, and clear Cursor's User Rules.
