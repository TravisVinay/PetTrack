---
id: "003"
title: Design the data model and migrations
week: 1
status: todo
depends: ["002"]
---

## Goal
Database tables with row-level security so people only see their own household's data.

## Tables (starting point; adjust as needed)
- `households` (id, name, created_by, vet clinic name/phone/address)
- `household_members` (household_id, user_id, role: owner|member, display_name)
- `pets` (id, household_id, name, species, breed, sex, birthday, weight_kg, photo_url, notes)
- `care_logs` (id, pet_id, type: fed|walked|bath|groomed|other, logged_by, logged_at, note)
- `medications` (id, pet_id, name, dose, frequency, times_of_day, start_date, end_date, active)
- `medication_doses` (id, medication_id, given_by, given_at)
- `appointments` (id, pet_id, starts_at, clinic, reason, notes)
- `weights` (id, pet_id, weight_kg, measured_at)
- `symptom_checks` (id, pet_id, input jsonb, red_flags text[], result jsonb, urgency, created_by, created_at)

## Steps
- Write migrations in `supabase/migrations/`
- RLS policies: members can read/write rows for their household only
- Generate TypeScript types (`supabase gen types`)
- Document the schema in `docs/DATA_MODEL.md`

## Done when
- Migrations apply cleanly; a user in household A cannot read household B's pets (test it)
