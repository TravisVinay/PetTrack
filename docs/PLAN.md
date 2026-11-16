# PetTrack — Five-Week Plan

A shared pet-care tracker for households: who fed the dog, when the last bath was,
which meds are due, upcoming vet appointments, and a "something is wrong" symptom
triage that tells you how urgent it is.

## Core idea

Pet care is shared between people (roommates, partners, family, pet sitters).
When one person taps **Fed**, everyone in the household sees it instantly.
Everything is organized around a **household**: several members, several pets.

## Stack

| Layer | Choice | Why |
|---|---|---|
| Frontend | React + TypeScript + Vite, installable PWA | Works on any phone, no app store |
| Styling | Tailwind CSS | Fast mobile-first layouts |
| Backend | Supabase (Postgres, Auth, Realtime, Storage, Edge Functions) | Accounts, live sync, photos, server code in one place |
| AI triage | Claude API, called **only** from a Supabase Edge Function | API key never reaches the browser |
| Tests | Vitest (+ Testing Library) | Fast, works with Vite |
| Hosting | Vercel | Free, deploys on every push |

## Schedule

| Week | Theme | Tasks |
|---|---|---|
| 1 | Foundation | 001–006: scaffold, Supabase, data model, sign-in, households, pet profiles |
| 2 | Daily care | 007–010: quick-log buttons, Today view, live sync, first deploy |
| 3 | Health records | 011–014: medication schedules, doses, vet appointments, household invites |
| 4 | Safety + testing | 015–018: emergency red-flag check, emergency screen, symptom form, real user testing |
| 5 | AI triage + polish | 019–025: triage function, results, triage evals, reminders, history, polish, write-up |

Task details live in [`tasks/`](../tasks). Use `/next-task` in Claude Code to pick up the next one.

## Must-have vs. stretch

**Must-have:** pet profiles, quick logs, Today view, live sync, medications, appointments,
invites, emergency red-flag check.

**Stretch (cut first if time runs short):** AI triage results (019–021), reminders (022),
history charts (023), pet-sitter mode, document uploads.

If week 5 runs short, the rule-based emergency check alone still ships as a useful feature,
and AI triage becomes the "next step" in the write-up.

## Measuring success (for the portfolio write-up)

- Number of households and members using it
- Logs per day, meds marked given, appointments added
- Quotes and issues from testers (task 018)
- Triage test-case pass rate (task 021)
