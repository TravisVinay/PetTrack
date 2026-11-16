---
id: "009"
title: Live sync between household members
week: 2
status: todo
depends: ["008"]
---

## Goal
When one person logs something, everyone else sees it without refreshing.

## Steps
- Subscribe to Supabase Realtime for the household's care logs (later meds/appointments too)
- Handle reconnects and avoid duplicate entries

## Done when
- Two browsers signed in as two members: a log on one appears on the other within a couple of seconds
