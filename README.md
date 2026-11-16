# PetTrack

A shared pet-care tracker for households. Log feedings, walks and baths with one tap, keep
track of medications and vet appointments, and see everything sync live between everyone who
looks after your pets. When something seems wrong, the symptom checker helps you decide how
urgently your pet needs a vet.

> Status: planning complete, building starts with task 001.

## Features (planned)
- Pet profiles with photos
- One-tap logs: fed, walked, bath, groomed — with who did it and when
- Today view: what's done and what's left
- Medication schedules and doses
- Vet appointments and clinic info
- Shared households with invite links
- "Something's wrong" triage: emergency red-flag check, then AI-assisted urgency guidance

## Docs
- [Five-week plan](docs/PLAN.md)
- [Symptom triage design](docs/SYMPTOM_CHECKER.md)
- [Tasks](tasks/)

## Working with Claude Code
Open this folder in VS Code with the Claude Code extension, then use:

| Command | What it does |
|---|---|
| `/tasks` | Show the task board and progress |
| `/next-task` | Start (or resume) the next ready task |
| `/finish-task` | Verify the current task, mark it done, commit |
| `/add-task <description>` | Add a new task |

*The symptom checker is not a substitute for a veterinarian.*
