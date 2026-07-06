# PawPal+ (Module 2 Project)

You are building **PawPal+**, a Streamlit app that helps a pet owner plan care tasks for their pet.

## Scenario

A busy pet owner needs help staying consistent with pet care. They want an assistant that can:

- Track pet care tasks (walks, feeding, meds, enrichment, grooming, etc.)
- Consider constraints (time available, priority, owner preferences)
- Produce a daily plan and explain why it chose that plan

Your job is to design the system first (UML), then implement the logic in Python, then connect it to the Streamlit UI.

## What you will build

Your final app should:

- Let a user enter basic owner + pet info
- Let a user add/edit tasks (duration + priority at minimum)
- Generate a daily schedule/plan based on constraints and priorities
- Display the plan clearly (and ideally explain the reasoning)
- Include tests for the most important scheduling behaviors

## Getting started

### Setup

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Suggested workflow

1. Read the scenario carefully and identify requirements and edge cases.
2. Draft a UML diagram (classes, attributes, methods, relationships).
3. Convert UML into Python class stubs (no logic yet).
4. Implement scheduling logic in small increments.
5. Add tests to verify key behaviors.
6. Connect your logic to the Streamlit UI in `app.py`.
7. Refine UML so it matches what you actually built.

## 🖥️ Sample Output

Actual terminal output from running `python main.py` (one owner, two pets, five tasks
added out of order — including two at 08:00 to trigger a conflict warning):

```text
====================================================
Today's Schedule for Jordan
  [ ] 08:00  Breakfast  (Biscuit) - daily
  [ ] 08:00  Feed cat  (Mochi) - daily
  [ ] 14:00  Vet appointment  (Biscuit) - once
  [ ] 18:00  Evening walk  (Biscuit) - daily
  [ ] 21:00  Night meds  (Mochi) - daily

Warnings:
  ! Conflict at 08:00: Biscuit's Breakfast, Mochi's Feed cat
====================================================

Biscuit's tasks only:
  - 18:00 Evening walk
  - 08:00 Breakfast
  - 14:00 Vet appointment

Completing Biscuit's Evening walk (daily)...
  -> Auto-created next occurrence for 2026-07-07

Remaining incomplete tasks (time-sorted):
  - 08:00 Breakfast [daily]
  - 08:00 Feed cat [daily]
  - 14:00 Vet appointment [once]
  - 18:00 Evening walk [daily]
  - 21:00 Night meds [daily]
```

## 🧪 Testing PawPal+

```bash
# Run the full test suite:
pytest

# Run with coverage:
pytest --cov
```

Sample test output:

```
# Paste your pytest output here
```

## 📐 Smarter Scheduling

> Fill in once you've implemented scheduling logic.

| Feature | Method(s) | Notes |
|---------|-----------|-------|
| Task sorting | | e.g., by priority, duration |
| Filtering | | e.g., skip tasks if time runs out |
| Conflict handling | | e.g., overlapping time slots |
| Recurring tasks | | e.g., daily vs. weekly |

## 📸 Demo Walkthrough

Describe your app in numbered steps so a reader can follow along without watching a video:

1. <!-- Describe this step -->
2. <!-- Describe this step -->
3. <!-- Describe this step -->
4. <!-- Describe this step -->
5. <!-- Add more steps as needed -->

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or link to a demo video here -->
