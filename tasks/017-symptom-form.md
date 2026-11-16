---
id: "017"
title: Symptom input form
week: 4
status: todo
depends: ["015"]
---

## Goal
A guided "Something's wrong" form that's quick to fill in when you're worried.

## Steps
- Entry point on each pet ("Something's wrong")
- Red-flag questions first; then checkbox groups, duration, better/same/worse, eating/drinking/energy, free text
- `buildTriageContext()` (pet details, meds, recent logs, weight trend) with tests
- Until task 019 lands, non-emergency results show "Call your vet for advice"

## Done when
- Form works one-handed on a phone; red flags route to the emergency screen
