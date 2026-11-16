---
description: Pick up the next ready task and start working on it
argument-hint: "[optional task id, e.g. 007]"
---

Start work on the next PetTrack task.

1. Read the frontmatter of every file in `tasks/`.
2. Choose the task:
   - If `$ARGUMENTS` names a task id, use that one (warn if its dependencies aren't done).
   - Otherwise, if a task is already `in-progress`, resume it.
   - Otherwise, pick the lowest-id task with `status: todo` whose `depends` are all `done`.
   - If nothing is ready, say which tasks are blocked and by what, then stop.
3. Set its `status` to `in-progress`.
4. Read the task file, `CLAUDE.md`, and any docs it references. Look at the current code
   relevant to the task.
5. Tell me in a few lines: the task, what you'll build, and any **You:** steps I need to do.
   If a **You:** step blocks the work, stop and wait for me.
6. Then implement it, keeping to the conventions in `CLAUDE.md`. Run tests, lint and build as you go.
7. When the "Done when" items are met, tell me how to check it myself and suggest `/finish-task`.
   Don't mark the task done or commit until I run `/finish-task`.
