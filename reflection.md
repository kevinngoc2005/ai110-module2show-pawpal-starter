# PawPal+ Project Reflection

## 1. System Design

**Three core actions a user can perform:**

1. **Add a pet** to their profile (name + species).
2. **Add a care task** to a specific pet (description, time of day, and how often it recurs).
3. **View today's schedule** across all their pets, sorted by time, with warnings when two tasks collide.

**a. Initial design**

I split the system into four classes, each with a single clear responsibility:

- **`Task`** — represents one care activity (a walk, feeding, medication, etc.). It holds a
  `description`, a `time` in `"HH:MM"` format, a `frequency` (`once` / `daily` / `weekly`), and a
  `completed` flag. It knows how to `mark_complete()` itself and how to produce its
  `next_occurrence()` for recurring tasks.
- **`Pet`** — stores a pet's `name` and `species` and owns a list of `Task` objects. It exposes
  `add_task()`, `list_tasks()`, and `task_count()`. It does *not* know anything about scheduling —
  it is just a container for that pet's tasks.
- **`Owner`** — the top-level entity. Holds the owner's `name` and a list of `Pet` objects, with
  `add_pet()` and `get_all_tasks()` (which flattens tasks across *every* pet so the scheduler can
  work system-wide, not one pet at a time).
- **`Scheduler`** — the "brain." It takes an `Owner` and organizes their tasks: `sort_by_time()`,
  `filter_tasks()` (by pet or completion status), `detect_conflicts()` (same-time collisions), and
  `complete_task()` (which also regenerates recurring tasks). Keeping this logic out of `Pet`/`Owner`
  means the data classes stay simple and all the algorithms live in one place.

**Relationships:** `Owner` **1→\*** `Pet` (an owner has many pets), `Pet` **1→\*** `Task` (a pet has
many tasks), and `Scheduler` **1→1** `Owner` (a scheduler operates on one owner's whole system).

**b. Design changes**

- _(To be filled in during implementation — describe at least one change and why. Candidate: whether
  recurrence lives on `Task.next_occurrence()` or inside `Scheduler.complete_task()`, and how the two
  ended up interacting.)_

---

## 2. Scheduling Logic and Tradeoffs

**a. Constraints and priorities**

- What constraints does your scheduler consider (for example: time, priority, preferences)?
- How did you decide which constraints mattered most?

**b. Tradeoffs**

- Describe one tradeoff your scheduler makes.
- Why is that tradeoff reasonable for this scenario?

---

## 3. AI Collaboration

**a. How you used AI**

- How did you use AI tools during this project (for example: design brainstorming, debugging, refactoring)?
- What kinds of prompts or questions were most helpful?

**b. Judgment and verification**

- Describe one moment where you did not accept an AI suggestion as-is.
- How did you evaluate or verify what the AI suggested?

---

## 4. Testing and Verification

**a. What you tested**

- What behaviors did you test?
- Why were these tests important?

**b. Confidence**

- How confident are you that your scheduler works correctly?
- What edge cases would you test next if you had more time?

---

## 5. Reflection

**a. What went well**

- What part of this project are you most satisfied with?

**b. What you would improve**

- If you had another iteration, what would you improve or redesign?

**c. Key takeaway**

- What is one important thing you learned about designing systems or working with AI on this project?
