---
id: "011"
title: Medication schedules
week: 3
status: todo
depends: ["010"]
---

## Goal
Track each pet's medications and when the next dose is due.

## Steps
- Add/edit/stop a medication: name, dose, frequency (daily, twice daily, every N days, weekly), times, start/end
- Pure function `nextDoseDue(medication, doses, now)` with thorough unit tests

## Done when
- Meds list per pet shows "next due" correctly; tests cover each frequency type
