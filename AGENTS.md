# Global agent rules

## Ask before acting

Before any change (creating, editing, moving or deleting files, installing packages, changing config, or running commands with side effects), explain your plan and wait for my explicit "yes". The plan must say:
1. What you'll do: each file and command.
2. Why this approach, and which alternatives you considered.
3. What could go wrong, and how to undo it.

- Approval covers only that exact plan. If it changes, or you need one more file or command, ask again. Silence, or agreement with the overall goal, is not a yes.
- Read-only work needs no permission: reading files, searching, web research, and inspect-only commands like `ls`, `cat` or `git status`.
- If I ask a question or say "explain", "look at" or "tell me", answer in chat and change nothing.
- When unsure whether something counts as a change, ask.

## Self-contained messages

Make every message understandable on its own: plans, permission requests, status updates, and mentions of remaining or skipped work. Include the full text of anything you propose (file content, config, commands, wording), even if you showed it before. Never point back with "as above", "same as before" or bare labels like "Part B" or "option 2".

## Editing files

Change files only with your built-in file tools (Edit/Write or equivalent), so every change goes through my review. Never write files from the shell: no `sed -i`, `perl -i`, `>` or `>>` redirects, heredocs into files, `tee`, or scripts that write files. Moving or deleting files needs `mv` or `rm`; put those in your plan like any other change.

## Research before recommending

Before recommending an approach, tool, setting or setup, or answering "is this the right way?", check current official docs and best practices on the web. Don't wait to be asked; your training data may be out of date.

- Trust official docs, the project's repo and README, and the installed tool's `--version` and `--help` over blog posts.
- For decisions I'll rely on long-term, run several searches, compare primary sources, and say where they disagree.
- Do the research yourself in this conversation. Don't launch subagents or multi-agent research unless I ask.
- Skip it for simple, stable facts and routine code edits.
- Cite sources with links and say what you couldn't verify.

## Terminal commands

Write any command you give me on a single line, with no `\` line continuations.

## Skills

Remove a skill with `npx skills remove -g <name>`, never `mv` or `rm`, so its folder and lock entry stay in sync.

## Git

- Never run `git add`, `git commit` or `git push` yourself. Leave changes uncommitted and give me a commit message.
- Commit messages: one-line Conventional Commits, `<type>(<scope>): <description>`, scope optional. Types: feat, fix, docs, style, refactor, perf, test, build, ci, chore. Imperative mood, lowercase, no trailing period, under 72 characters, one logical change per commit. Example: `fix(parser): handle empty input without panic`
- Never credit an AI tool or assistant in commits, branch names, or PR titles and descriptions: no tool names as authors, no "generated with" text, no co-author trailers.
