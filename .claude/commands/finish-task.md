---
description: Verify the current task, mark it done and commit
---

Finish the PetTrack task that is `in-progress` in `tasks/`.

1. Find the `in-progress` task. If there isn't exactly one, tell me and stop.
2. Check each "Done when" item. Run `npm test`, `npm run lint` and `npm run build` if the app
   exists. Report anything that fails and stop; don't mark it done.
3. If everything passes, add a short `## Notes` section to the task file (key decisions,
   anything left over or deferred). If something was deferred, offer to create a task for it
   with `/add-task`.
4. Set `status: done`.
5. Show `git status`, then commit all changes for this task with the message
   `task NNN: <title>` (never commit `.env*` files except `.env.example`).
6. Tell me what's done and what the next ready task is.
