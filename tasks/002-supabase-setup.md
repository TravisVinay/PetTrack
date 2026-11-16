---
id: "002"
title: Create the Supabase project and connect it
week: 1
status: todo
depends: ["001"]
---

## Goal
The app talks to a Supabase project, with keys kept out of git.

## Steps
- **You:** create a free project at supabase.com (Claude can't create accounts for you)
- Install Supabase CLI and `@supabase/supabase-js`; `supabase init` for local migrations
- `.env.local` with `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`; add `.env.example` (no real values)
- `src/lib/supabase.ts` client

## Done when
- App connects (e.g. a test query succeeds) and `.env.local` is git-ignored
