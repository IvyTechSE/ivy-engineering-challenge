# Assignment Specification

## Objective

Build a toll fee calculator for a city traffic system.

The calculator should return the **total daily toll fee** for a vehicle based on passage timestamps and the fee rules in this document.

This is intentionally scoped as a realistic engineering exercise: clear enough to start quickly, open enough to show design and tradeoff thinking.
No baseline implementation is provided in this repository on purpose.

## Time Box

- Suggested implementation time: **3-5 hours**
- Suggested documentation/prep time: **up to 45 minutes**
- This is a guideline for scope and fairness, not a strict hard cutoff.

Completeness is not required. Clear reasoning and engineering quality are required.

## Follow-Up Discussion (In Person)

The exercise includes a physical follow-up meeting to discuss your solution.

In this discussion, be prepared to:

- Walk through your solution and explain key design decisions.
- Explain tradeoffs and assumptions you made.
- Describe how you would improve the solution with more time.
- Explain how your approach could scale (for example: traffic volume, maintainability, reliability, operability).

Part of the assignment is your ability to communicate technical decisions, not only the submitted code.

## Core Rules

### 1. Fee schedule (SEK)

| Time interval (local time) | Fee |
| --- | --- |
| 06:00-06:29 | 8 |
| 06:30-06:59 | 13 |
| 07:00-07:59 | 18 |
| 08:00-08:29 | 13 |
| 08:30-14:59 | 8 |
| 15:00-15:29 | 13 |
| 15:30-16:59 | 18 |
| 17:00-17:59 | 13 |
| 18:00-18:29 | 8 |
| 18:30-05:59 | 0 |

### 2. One charge per 60-minute window

- Passages are grouped in rolling windows.
- A window starts at the first unprocessed passage.
- Any passage that occurs within 60 minutes from that start belongs to the same window.
- Charge only the highest fee in that window.

### 3. Daily cap

- Maximum total fee per vehicle per calendar day: **60 SEK**.

### 4. Toll-free vehicles

- `Motorbike`
- `Tractor`
- `Emergency`
- `Diplomat`
- `Foreign`
- `Military`

### 5. Toll-free dates

- Saturdays and Sundays.
- Public holidays for this exercise (2013 table):
  - Jan 1
  - Mar 28-29
  - Apr 1, Apr 30
  - May 1, 8, 9
  - Jun 5, 6, 21
  - All dates in Jul
  - Nov 1
  - Dec 24, 25, 26, 31

If you make holiday handling configurable or year-agnostic, document your approach.

## Input and Output Contract

Use this language-agnostic contract as the target.

### Request type

`DailyTollRequest`

- `vehicleType: string`
- `passages: PassageEvent[]`

`PassageEvent`

- `timestamp: string` (ISO-8601, must include timezone offset)

### Response type

`DailyTollResponse`

- `date: string` (`YYYY-MM-DD`)
- `totalFeeSek: number`
- `chargedPassages?: ChargedPassage[]` (optional but recommended)
- `notes?: string[]` (optional assumptions/validation notes)

`ChargedPassage` (optional)

- `windowStart: string`
- `windowEnd: string`
- `appliedFeeSek: number`
- `triggeringTimestamp: string`

Optional API target for backend/fullstack/frontend-mock tracks:

- `POST /toll/calculate`
- Request body: `DailyTollRequest`
- Response body: `DailyTollResponse`

## Validation and Assumptions

Default assumptions for this exercise:

- Timezone for rule evaluation: timestamp timezone (do not assume UTC unless you convert intentionally and document it).
- Calendar day boundary: local calendar day from the evaluated timezone.
- Input ordering: may be unsorted; sort before processing.
- Input may contain invalid records; define your strategy and document it.

Recommended validation behavior:

- Reject malformed timestamps and missing vehicle type with a clear error.
- If passages span multiple dates, either:
  - reject with a clear message, or
  - split by date and return one response per date.

Choose one behavior and document it.

## Deliverables

Required:

- Runnable code in any language.
- `README` in your submission repository with:
  - Selected track (`Frontend`, `Backend`, `Fullstack`, `General Software Engineer`, or `Architect`)
  - Setup and run instructions
  - Assumptions
  - Tradeoffs
  - Improvements and scalability notes for discussion
  - What you would do next with more time
- Tests or a clear test strategy explanation.

Optional but valuable:

- Explanation of architecture choices:
  - Describe your main components/modules and the boundaries between them.
  - Call out at least one key tradeoff and one alternative you considered.
  - Explain how your design could evolve (for example: configurable rules, more traffic, multi-day requests).
- API schema or sequence diagram:
  - Include request/response examples or a lightweight schema (OpenAPI snippet, JSON schema, typed contracts, etc.).
  - If using a sequence diagram, show the core flow: validation -> fee calculation -> response/error mapping.
  - Keep it lightweight; a small diagram or short contract section is enough.
- Observability/error-reporting notes:
  - State what you would log at info/warn/error level and what you would avoid logging.
  - Propose a minimal metric set (for example: request count, latency, error rate, validation failures).
  - Describe how errors are surfaced to callers/users (clear status codes/messages) and how you would debug failures.

## What You May Choose Freely

- Programming language and framework.
- Project structure and naming.
- API shape beyond the minimum contract.
- Storage approach (in-memory is acceptable).
- Test tooling and depth.

## Non-Goals

- Building a full production platform.
- Creating full authentication or deployment pipelines.
- Building a polished, feature-complete end-user product.
