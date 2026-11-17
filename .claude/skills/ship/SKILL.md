---
name: ship
description: Prepare the current edits for commit — format, check, summarise, commit. Never pushes.
disable-model-invocation: true
---

Prepare my current changes for a commit:

1. Run the pre-commit checklist in CLAUDE.md (prettier formatting and any other
   checks listed there). Fix anything that fails.
2. Check the site still builds, using the build command in CLAUDE.md.
3. Show `git status` and a short summary of what changed, file by file.
4. Flag anything that looks unintended: stray files, changes to `_config.yml`,
   workflow files, or the CV/bibliography that I didn't ask for.
5. Propose a one-line commit message and wait for my OK.
6. After I confirm, provide the full `git commit` command to run, including the message. Do not commit or push anything yourself.
