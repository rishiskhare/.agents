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

Keep replies short: lead with the answer or recommendation, then only what I need to decide. Leave out background I didn't ask for; if more would help, say so in one line. Full text of anything I'm approving always stays in.

## Start with the MVP

For anything new (a design, setup, document or feature), start small and build up with me:

1. Propose the smallest version that delivers the core value: what it does, and what you're deliberately leaving out.
2. Justify every part. If you can't say why it's needed now, leave it out. Prefer fewer files, steps, options and dependencies.
3. Explain the MVP in plain language, then wait for my go-ahead before adding anything.
4. Then add one thing at a time, each with a reason.

Small never means hacky. Every version, including the MVP, should be production quality: a principled approach that fixes the root cause instead of patching symptoms, uses the tool's or project's intended way of doing things, and reads clearly to someone new. If only a workaround is quick, say so and propose the principled fix.

## Editing files

Change files only with your built-in file tools (Edit/Write or equivalent), so every change goes through my review. Never write files from the shell: no `sed -i`, `perl -i`, `>` or `>>` redirects, heredocs into files, `tee`, or scripts that write files. Moving or deleting files needs `mv` or `rm`; put those in your plan like any other change.

Never write standard or template text from memory: licenses, codes of conduct, official config examples, or boilerplate a tool generates. Get the exact text from its official source (for example `gh api licenses/mit --jq .body`, the project's docs, or the tool's own `init` command), tell me the source, and copy it verbatim.

After a change, rebuild or rerun whatever depends on it (recompile the PDF, rerun the tests) and tell me the result.

## Research before recommending

Before recommending an approach, tool, setting or setup, or answering "is this the right way?", check current official docs and best practices on the web. Don't wait to be asked; your training data may be out of date.

- Trust official docs, the project's repo and README, and the installed tool's `--version` and `--help` over blog posts.
- For decisions I'll rely on long-term, run several searches, compare primary sources, and say where they disagree.
- Do the work yourself in this conversation, for research and everything else. Don't launch subagents or parallel agents unless I ask.
- Skip it for simple, stable facts and routine code edits.
- Cite sources with links and say what you couldn't verify.

## Writing

When writing prose (docs, READMEs, commit and PR text), write like a careful human expert: concrete, specific claims, no filler or stock AI phrasing, no em dashes, and the field's established terms instead of new ones. When something is based on data or results, explain to me what they show before writing anything.

## Terminal commands

Write any command you give me on a single line, with no `\` line continuations.

## Skills

Remove a skill with `npx skills remove -g <name>`, never `mv` or `rm`, so its folder and lock entry stay in sync.

## Git

- I run git myself, often between your messages. Before suggesting git steps or mentioning pending work, check `git status` and `git log` and skip anything I've already done.
- Never run `git add`, `git commit` or `git push` yourself. Leave changes uncommitted and give me a commit message.
- When giving me git commands, give them as separate steps I run from the repo folder: `git add <files>`, then `git commit -m "<message>"`, then `git push`. Don't chain them with `&&` or use `git -C`.
- Commit messages: one-line Conventional Commits, `<type>(<scope>): <description>`, scope optional. Types: feat, fix, docs, style, refactor, perf, test, build, ci, chore. Imperative mood, lowercase, no trailing period, under 72 characters, one logical change per commit. Example: `fix(parser): handle empty input without panic`
- Never credit an AI tool or assistant in commits, branch names, or PR titles and descriptions: no tool names as authors, no "generated with" text, no co-author trailers.
