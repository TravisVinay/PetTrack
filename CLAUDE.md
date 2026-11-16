# PetTrack

Shared pet-care tracker for households (feeding, baths, meds, vet appointments) plus a
"something is wrong" symptom triage. Built as a five-week class "moonshot" project.

- Plan and stack: `docs/PLAN.md`
- Symptom triage design and safety rules: `docs/SYMPTOM_CHECKER.md`
- Tasks: `tasks/NNN-slug.md`, one file per task

## Stack
React + TypeScript + Vite (PWA), Tailwind CSS, Supabase (Postgres, Auth, Realtime, Storage,
Edge Functions), Vitest, deployed on Vercel. The Claude API is called only from a Supabase
Edge Function.

## Task workflow
Each task file has YAML frontmatter:

```yaml
id: "007"
title: Quick-log buttons
week: 2
status: todo        # todo | in-progress | done
depends: ["006"]
```

- A task is **ready** when its status is `todo` and every task in `depends` is `done`.
- Work on one task at a time. Only one task should be `in-progress`.
- When finishing, tick off the "Done when" items, add a short `## Notes` section to the task
  file (decisions, anything left over), set `status: done`, and commit.
- Steps marked **You:** need the user (creating accounts, adding secrets, recruiting testers).
  Stop and ask them; never create accounts or handle real keys yourself.
- Commands: `/next-task`, `/finish-task`, `/tasks`, `/add-task`.

## Conventions
- Mobile-first: check every screen at phone width.
- Feature code in `src/features/<feature>/`, shared UI in `src/components/`, clients/helpers in `src/lib/`.
- Pure logic (due-date math, red-flag rules, triage context) goes in plain functions with unit tests.
- Never commit secrets. Frontend env vars are `VITE_*` and must only hold public values
  (Supabase URL and anon key). The Anthropic key lives only in Supabase secrets.
- Every table has row-level security scoped to the household.
- Commit messages: `task NNN: short description`.

## Symptom triage safety rules (do not relax)
- The red-flag check is plain code, runs first, and goes straight to the emergency screen.
- AI output can never lower the urgency a red flag set.
- When unsure, choose the more urgent level; never tell the user the pet doesn't need a vet.
- If the AI call fails or its output doesn't validate, show "Call your vet".
- Every result shows: "This isn't a diagnosis. When in doubt, call your vet."
