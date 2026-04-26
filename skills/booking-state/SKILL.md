---
name: booking-state
description: Maintain CircuitScout booking-state.md as the shared source of truth for artist booking workflows, including facts, assumptions, approvals, outreach, follow-ups, decisions, risks, and handoffs.
---

# Booking State

`booking-state.md` is the source of truth for a CircuitScout booking workflow.

It records the artist profile, booking goals, opportunities, contacts, drafts, approvals, outreach, follow-ups, replies, calendar actions, CRM/spreadsheet actions, risks, decisions, handoffs, open questions, and retrospective notes. It must distinguish confirmed facts from assumptions and preserve source links.

## When To Read

Read `booking-state.md` before:

- Starting or resuming a CircuitScout workflow.
- Researching opportunities, contacts, markets, or scenes for an active artist/project.
- Drafting outreach, replies, follow-ups, approvals, calendar actions, or CRM/spreadsheet actions.
- Updating pipeline status, contact records, approval queues, outreach logs, follow-up queues, inbox status, risks, decisions, or handoffs.
- Making a recommendation that depends on previous booking context.

If no state file exists and the user wants ongoing tracking, initialize one from `examples/booking-desk/booking-state.md`.

## When To Update

Update `booking-state.md` when:

- The user provides or corrects artist profile details, positioning, EPK assets, target markets, goals, constraints, or preferences.
- New opportunities or source links are found.
- A contact route is verified, rejected, or marked uncertain.
- A draft is created or materially revised.
- An approval request is created, approved, rejected, changed, or expired.
- Outreach is sent manually by the user or via a future approved connector.
- A follow-up is due, deferred, completed, or cancelled.
- Inbox replies change the status of an opportunity, contact, draft, follow-up, risk, decision, calendar action, or CRM/spreadsheet action.
- A consequential decision is made.
- A risk, unknown, assumption, or open question is identified or resolved.
- Work is handed off to another agent, skill, or human.
- A retrospective note should be preserved for future booking work.

## Append-Only Audit Behavior

The following sections are audit records:

- `Approval Queue`
- `Outreach Log`
- `Decision Log`
- `Handoff Chain`

For audit records, append new rows or notes instead of rewriting history. If a status changes, update the status/date fields and preserve the original row. If the meaning changed because new information arrived, add a note or decision entry explaining the change.

Do not remove rejected approvals, abandoned drafts, failed contacts, declined opportunities, or risks that affected a decision. Mark their final status instead.

## Facts, Assumptions, Unknowns, And Preferences

Keep these categories separate:

- Confirmed facts: sourced or directly provided information. Include source links or note "user-provided".
- Assumptions: working beliefs that are plausible but not confirmed. Label them as assumptions and revisit them.
- Unknowns: missing information needed for confidence or action. Mark unknowns as `Unknown`, not blank.
- User-provided preferences: explicit preferences, constraints, tone guidance, exclusions, priorities, or dealbreakers from the user.

Never invent contacts, capacities, lineups, fees, audience sizes, artist credentials, or source evidence.

## Required Sections

Every `booking-state.md` file must include:

- `Artist Profile`
- `Positioning / Sound / Scene Fit`
- `EPK Assets`
- `Target Markets`
- `Booking Goals`
- `Opportunity Pipeline`
- `Contact Register`
- `Draft Outbox`
- `Approval Queue`
- `Outreach Log`
- `Follow-up Queue`
- `Inbox / Reply Status`
- `Calendar Actions`
- `CRM / Spreadsheet Actions`
- `Decision Log`
- `Risk Register`
- `Do-not-contact List`
- `Handoff Chain`
- `Open Questions`
- `Retrospective Notes`

Use `examples/booking-desk/booking-state.md` as the canonical template for new projects.

## State Hygiene Rules

- Preserve source links in the same row or bullet as the claim they support.
- Mark unknowns explicitly.
- Use stable IDs for opportunities, contacts, drafts, approvals, outreach, follow-ups, decisions, risks, and handoffs.
- Keep statuses short and consistent, such as `New`, `Researching`, `Needs approval`, `Approved`, `Rejected`, `Sent`, `Waiting`, `Follow-up due`, `Closed`, or `Unknown`.
- Keep external actions in queue sections until the human approves and completes them.
- Record private/personal email concerns in permission/safety notes and require explicit approval before contact.
- Keep do-not-contact entries separate from general contacts.
- Avoid duplicating the same fact across multiple sections unless the second location links back to the source section or ID.
- Do not erase consequential context after a decision changes.

## Approval Queue Guidance

Use `skills/approval-before-action/SKILL.md` before creating, approving, rejecting, blocking, or executing approval-gated actions.

`Approval Queue` entries should support:

- Action ID.
- Proposed action.
- Target.
- Reason.
- Evidence/source.
- Risk level.
- Status.
- Created date.
- Required human decision.
- Approved/rejected date.
- Notes.

Use statuses such as `Needs approval`, `Approved`, `Rejected`, `Needs clarification`, `Expired`, or `Blocked`. Approval must be explicit and action-specific. If approval is unclear, do not execute the action.

## Decision Log Guidance

`Decision Log` entries should record:

- Decision ID.
- Related action ID.
- Decision.
- Human approver.
- Timestamp/date.
- Rationale.
- Resulting state change.

Log approvals before or alongside the approved action. Log rejections, blocked actions, and consequential status changes even when no external action occurs.

## Handoff Format

When handing off booking state, provide:

- State file path and last update date.
- Current workflow stage.
- Key opportunity/contact/draft/approval IDs.
- Confirmed facts.
- Assumptions.
- Unknowns.
- User-provided preferences.
- Pending approval gates.
- Risks.
- Recommended next action.

The handoff should be concise enough for the next agent or human to continue without rereading the full file, but it must point back to the relevant state sections and source links.
