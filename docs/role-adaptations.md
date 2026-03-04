# Role Adaptations

All tracks use the same domain problem, core rules, and time box.

Choose one primary track based on your role.
If you are unsure, choose the General Software Engineer track.
No starter solution is provided; implement from scratch in your chosen language/framework.

## Frontend Track

### Focus areas

- UI structure and information hierarchy
- Accessibility and keyboard navigation
- Component architecture
- State management and data flow
- User feedback for validation and edge cases

### Minimum deliverables

- A UI that lets a user inspect passage events and resulting daily fee.
- A mock backend contract (local JSON, mock service, MSW, MirageJS, etc.) that follows `DailyTollRequest` and `DailyTollResponse`.
- A short explanation of how the backend should behave.

### What strong submissions show

- Interaction clarity over visual polish.
- Clear component boundaries and maintainable state modeling.

## Backend Track

### Focus areas

- API/function contract design
- Domain modeling and calculation logic
- Validation and error handling
- Test strategy and deterministic behavior
- Performance reasoning for larger input sets

### Minimum deliverables

- A calculation service or API endpoint.
- Rule-complete fee calculation for defined scenarios.
- Tests for happy path, boundaries, and invalid input.

### What strong submissions show

- Correctness and predictable behavior.
- Robustness and maintainable architecture.

## Fullstack Track

### Focus areas

- System boundaries and separation of concerns
- Integration between UI and calculation layer
- End-to-end developer experience
- Pragmatic architecture under time constraints

### Minimum deliverables

- Thin vertical slice: input UI + calculation backend + result view.
- Shared understanding of request/response schema.
- Basic integration tests or documented manual verification.

### What strong submissions show

- Cohesion across layers.
- Practical tradeoffs and sensible scope control.

## General Software Engineer Track

### Focus areas

- Balanced implementation of domain logic, interfaces, and maintainable code.
- Clear decomposition and readability.
- Pragmatic validation and error handling.
- Practical testing for core rules and key edge cases.
- Clear communication of tradeoffs and next steps.

### Minimum deliverables

- A working solution that implements the core rules from the assignment spec.
- A clear input/output contract aligned with `DailyTollRequest` and `DailyTollResponse`.
- Tests for core scenarios and at least one invalid-input path.

### What strong submissions show

- Solid engineering fundamentals with sensible scope choices.
- Clear explanation of assumptions, risks, and improvement path.

## Architect Track

### Focus areas

- Solution architecture and extensibility
- Scalability and operational readiness
- Design tradeoffs and alternatives
- Maintainability and ownership concerns
- Documentation quality

### Minimum deliverables

- Partial implementation is acceptable.
- Required design note describing:
  - architecture and module boundaries
  - data flow
  - risks and mitigations
  - phased rollout or next-step plan

### What strong submissions show

- Decision quality and depth of reasoning.
- Ability to make constraints explicit and defend tradeoffs.

## Consistency Rule Across Tracks

- The assignment is not larger for any track.
- Each track should fit the same time box.
- Candidates are rewarded for clear decisions, not feature count.

## Follow-Up Discussion Expectations

Across all tracks, candidates should be ready to discuss their solution in a physical follow-up meeting.

- Frontend: explain UX choices, component boundaries, and how the UI would scale in complexity.
- Backend: explain domain boundaries, correctness strategy, and scalability/performance tradeoffs.
- Fullstack: explain integration boundaries, end-to-end flow, and evolution path as scope grows.
- General Software Engineer: explain implementation boundaries, why scope decisions were made, and how the solution would evolve toward production.
- Architect: explain architecture evolution, risk management, and operational scalability.
