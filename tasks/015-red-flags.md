---
id: "015"
title: Emergency red-flag rules (no AI)
week: 4
status: todo
depends: ["006"]
---

## Goal
A tested, plain-code check that catches "go to the vet now" situations. See `docs/SYMPTOM_CHECKER.md`.

## Steps
- `src/features/triage/redFlags.ts`: list of red flags (id, label, species it applies to, why)
- `checkRedFlags(input, pet)` returns matched flags
- Unit test for **every** rule, including species-specific ones (bloat in dogs, urinary blockage in cats)

## Done when
- All rules have passing tests; the list matches the design doc
