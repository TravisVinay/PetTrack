---
id: "019"
title: AI triage edge function
week: 5
status: todo
depends: ["017"]
---

## Goal
Server-side Claude call that returns structured triage. See `docs/SYMPTOM_CHECKER.md`.

## Steps
- Load the `claude-api` skill first for current model IDs and SDK usage
- `supabase/functions/triage`: auth check, per-user rate limit, prompt built from form + context
- Request structured JSON; validate with a schema (e.g. zod); on failure return `call_vet`
- Never return an urgency lower than any matched red flag implies
- **You:** add the Anthropic API key as a Supabase secret (never in the frontend)

## Done when
- Function returns valid results for sample inputs and fails safe on errors
