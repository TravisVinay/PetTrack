# "Something Is Wrong" — Symptom Triage Design

This feature answers **"how urgent is this?"**, not "what disease does my pet have?".
A wrong "it's probably fine" can hurt a pet, so every design choice leans cautious.

## Flow

1. **Emergency red-flag check (plain code, no AI)** — runs first, always.
2. **Guided symptom form** — checkboxes and short questions, plus optional free text.
3. **App context** — species, breed, age, weight, current meds, recent logs.
4. **AI triage** — structured input → structured output (urgency, possible causes, what to watch, vet summary).
5. **Save** the check to the pet's history.

## 1. Red flags → immediate emergency screen

If any of these are selected, skip the AI and show the emergency screen right away:

- Trouble breathing, choking
- Collapse, can't stand, unresponsive
- Seizure
- Pale, white, grey or blue gums
- Heavy bleeding that won't stop
- Hit by a car, serious fall or other major trauma
- Dogs: swollen/hard belly with retching that brings nothing up (possible bloat)
- Cats (especially males): straining to urinate with little or nothing coming out
- Ate something possibly toxic: chocolate, xylitol (sugar-free gum/candy), grapes or raisins,
  onions or garlic, lilies (cats), human medications, antifreeze, rat poison
- Eye injury or eye suddenly bulging
- Repeated vomiting or diarrhea with blood
- Signs of severe pain (crying out, won't let you touch an area)

The list lives in one file (`src/features/triage/redFlags.ts`) with unit tests for every rule.

**Emergency screen shows:**
- "Contact a vet now" with a call button for the household's saved clinic
- Advice to find the nearest emergency vet if their clinic is closed
- Poison hotlines (both charge a fee): ASPCA Animal Poison Control, Pet Poison Helpline —
  verify the current numbers before shipping

## 2. Symptom form

- What's happening (checkbox groups: eating, drinking, vomiting, stool, urination, breathing,
  energy, movement/limping, skin/coat, eyes/ears, behavior)
- Since when (under 1 hour / today / 1–3 days / longer)
- Getting better, same or worse
- Eating and drinking normally? Energy level?
- Free text: "anything else?"

## 3. Context pulled from the app

- Species, breed, age, sex, weight (and weight trend)
- Current medications (side effects matter)
- Recent logs, e.g. "skipped 2 logged meals", "weight down 8% in a month"

## 4. AI triage

Called from a Supabase Edge Function (`supabase/functions/triage`). The browser never sees the key.

**Output (validated JSON):**

```json
{
  "urgency": "emergency | vet_24h | call_vet | monitor",
  "possible_causes": [{ "name": "...", "explanation": "plain language" }],
  "watch_for": ["signs that would make this more urgent"],
  "vet_summary": "short summary to show or read to the vet"
}
```

**Rules for the prompt and the code:**
- When unsure, pick the more urgent level.
- Never say the pet doesn't need a vet.
- The AI **cannot lower** an urgency already set by the red-flag check.
- If the call fails or the output doesn't validate, show "Call your vet" — never a blank or a guess.
- Load the `claude-api` skill in Claude Code when implementing, for current model IDs and SDK usage.

## Disclaimers

Every result shows: *"This isn't a diagnosis. When in doubt, call your vet."*

## Testing

- Unit tests for every red-flag rule (task 015)
- 15–20 written scenarios with the expected urgency, run against the triage function (task 021),
  e.g. "male cat, straining in the litter box for 6 hours" → `emergency`
- Bonus: ask a vet or vet tech to review the scenarios and results
