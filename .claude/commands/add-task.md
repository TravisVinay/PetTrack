---
description: Create a new task file
argument-hint: "<what the task is>"
---

Create a new PetTrack task for: $ARGUMENTS

1. Find the highest task id in `tasks/` and use the next number (zero-padded to 3 digits).
2. Ask me only what you can't sensibly infer: which week it belongs to, and what it depends on.
3. Create `tasks/NNN-short-slug.md` in the same format as the existing tasks:
   frontmatter (`id`, `title`, `week`, `status: todo`, `depends`) and `## Goal`, `## Steps`,
   `## Done when` sections. Mark steps that need me with **You:**.
4. Show me the file. Don't commit.
