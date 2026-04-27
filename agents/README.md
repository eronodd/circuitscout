# CircuitScout Agent Index

CircuitScout agents are role wrappers for ownership, boundaries, and handoffs. Skills remain the procedural source of truth for how work is performed. Use the agents below to route booking-desk work, then follow the relevant `skills/` playbooks for operating rules, state updates, and approval gates.

## CircuitScout-Native MVP Agents

### `booking-strategist`

- Purpose: Defines booking goals, target markets, routing logic, opportunity priorities, artist constraints, strategic assumptions, and downstream workflow direction.
- Primary skills used: `skills/booking-state/SKILL.md`, `skills/opportunity-discovery/SKILL.md`, `skills/fit-classification/SKILL.md`, `skills/approval-before-action/SKILL.md` when a recommendation becomes external-facing or consequential.
- Main booking-state sections touched: `Artist Profile`, `Positioning / Sound / Scene Fit`, `Target Markets`, `Booking Goals`, `Opportunity Pipeline`, `Decision Log`, `Risk Register`, `Open Questions`, `Handoff Chain`.
- Default next handoff: `opportunity-scout` for lead discovery or `fit-classifier` for existing opportunities that are ready to score.
- Approval boundary: Strategy work is internal, but any relationship, booking status, calendar, contact, or external-system consequence must route through `booking-guardian` / `approval-before-action`.

### `opportunity-scout`

- Purpose: Turns user-provided lead material, scene notes, source links, flyers, lineup text, and similar-artist clues into candidate opportunity records with evidence, unknowns, duplicate checks, and next-step recommendations.
- Primary skills used: `skills/opportunity-discovery/SKILL.md`, `skills/booking-state/SKILL.md`, `skills/fit-classification/SKILL.md` only as handoff target or readiness context.
- Main booking-state sections touched: `Artist Profile`, `Target Markets`, `Opportunity Pipeline`, `Open Questions`, `Handoff Chain`.
- Default next handoff: `fit-classifier`.
- Approval boundary: Internal extraction, summarization, deduplication, and candidate preparation do not require approval. Do not scrape, browse, automate collection, perform OCR, contact anyone, or take external action.

### `fit-classifier`

- Purpose: Applies the 100-point booking fit model and recommends proceed, monitor, reject review, or contact verification while separating confirmed facts from assumptions.
- Primary skills used: `skills/fit-classification/SKILL.md`, `skills/booking-state/SKILL.md`, `skills/approval-before-action/SKILL.md` only if a recommendation becomes external-facing or consequential.
- Main booking-state sections touched: `Opportunity Pipeline`, `Positioning / Sound / Scene Fit`, `Target Markets`, `Risk Register`, `Open Questions`, `Handoff Chain`.
- Default next handoff: `contact-verifier` for qualified opportunities that are ready for contact work.
- Approval boundary: Fit scoring is internal. Status changes with consequential meaning, external actions, calendar commitments, or external-system writes must route through `booking-guardian` / `approval-before-action`.

### `contact-verifier`

- Purpose: Validates the safest official contact route for a qualified opportunity and checks confidence, source type, duplicate/conflict notes, safety issues, and do-not-contact status.
- Primary skills used: `skills/contact-verification/SKILL.md`, `skills/booking-state/SKILL.md`, `skills/approval-before-action/SKILL.md` for any external next action.
- Main booking-state sections touched: `Opportunity Pipeline`, `Contact Register`, `Do-not-contact List`, `Risk Register`, `Open Questions`, `Handoff Chain`.
- Default next handoff: `outreach-drafter` when the route is `Verified` or `Likely` and no blocking conflict exists.
- Approval boundary: Contact verification is internal. Do not guess addresses, use private routes as normal outreach paths, contact anyone, change do-not-contact status, create drafts externally, or write to external systems without explicit action-specific approval.

### `outreach-drafter`

- Purpose: Prepares personalized, source-backed outreach, reply, and follow-up draft text for human review while keeping prepared drafts separate from sent outreach.
- Primary skills used: `skills/outreach-drafting/SKILL.md`, `skills/followup-planning/SKILL.md`, `skills/inbox-triage/SKILL.md` when replying to inbound messages, `skills/booking-state/SKILL.md`, `skills/approval-before-action/SKILL.md` for any external next action.
- Main booking-state sections touched: `Artist Profile`, `EPK Assets`, `Opportunity Pipeline`, `Contact Register`, `Draft Outbox`, `Outreach Log`, `Follow-up Queue`, `Inbox / Reply Status`, `Approval Queue`, `Handoff Chain`.
- Default next handoff: `booking-guardian` / `approval-before-action` when the user wants to send, reply, forward, schedule, create an external draft, or write externally.
- Approval boundary: Local draft preparation is internal. Sending, replying, forwarding, creating Gmail drafts, submitting forms, sending DMs, scheduling, and external writes require explicit action-specific approval.

### `booking-guardian`

- Purpose: Enforces approval gates, auditability, do-not-contact rules, safety review, and prepare-vs-execute separation across CircuitScout workflows.
- Primary skills used: `skills/approval-before-action/SKILL.md`, `skills/booking-state/SKILL.md`, plus relevant workflow skills as review context.
- Main booking-state sections touched: `Approval Queue`, `Decision Log`, `Risk Register`, `Do-not-contact List`, `Outreach Log`, `Calendar Actions`, `CRM / Spreadsheet Actions`, `Handoff Chain`.
- Default next handoff: Human approval, clarification, blocked-action resolution, or return to the prior internal agent after safety review.
- Approval boundary: Owns the approval boundary but cannot approve on the human's behalf. External-facing or consequential actions stay blocked until explicit action-specific approval names the action, target, and relevant draft or state change.

## Default Routing Chain

```text
booking-strategist
-> opportunity-scout
-> fit-classifier
-> contact-verifier
-> outreach-drafter
-> booking-guardian / approval-before-action
```

## Reply / Follow-Up Branch

```text
inbox-triage
-> followup-planning
-> outreach-drafter if reply/follow-up text is needed
-> booking-guardian / approval-before-action
```

## Legacy Boundary

Existing legacy Designpowers agents remain in the repo during migration. They are not the default agents for CircuitScout booking workflows.

Do not use legacy design agents for booking workflow decisions unless a future migration slice explicitly adapts them.

For CircuitScout booking work, prefer the CircuitScout-native MVP agents listed above and the current CircuitScout skills. Approval-before-action remains the mandatory gate for external-facing or consequential actions.
