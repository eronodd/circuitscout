---
name: approval-before-action
description: Enforce CircuitScout approval gates before external-facing or consequential booking-desk actions, including approval requests, risk levels, state logging, ambiguity handling, and auditability.
---

# Approval Before Action

CircuitScout is a human-directed AI booking desk for electronic music artists. It may research, classify, draft, summarize, prepare actions, and maintain local tracking state, but it must not take external-facing or consequential actions without explicit human approval for the exact action.

Use this skill before any workflow step that could send, contact, commit, negotiate, modify an external system, change a consequential status, or otherwise affect an artist, promoter, venue, festival, club, collective, radio show, agency, calendar, CRM, spreadsheet, private contact route, or do-not-contact record.

## When This Skill Must Be Used

Use this skill when the user asks CircuitScout to:

- Send, reply, forward, contact, follow up, pitch, negotiate, accept, decline, confirm, book, schedule, hold, update, close, reject, mark booked, mark do-not-contact, or change an external system.
- Prepare an action that may later become external-facing, such as an email draft, reply draft, proposed calendar hold, proposed CRM row, or proposed booking decision.
- Interpret ambiguous execution language such as "handle it", "take care of it", "go ahead", "proceed", "send that", "lock it in", or "do the update".
- Make or log a consequential booking decision.
- Use a future connected write/send tool, including Gmail, Calendar, CRM, spreadsheet, API, automation, or similar connector.

If a workflow only reads files, summarizes known information, classifies internal notes, identifies missing information, recommends next steps, or updates local markdown state without external effects, this skill may be used as a quick check but approval is not required.

## Actions That Always Require Explicit Human Approval

Always require explicit human approval before:

- Sending any email.
- Creating a Gmail draft if connected later.
- Replying to an email.
- Forwarding an email.
- Contacting a promoter, venue, festival, club, collective, radio show, agency, or artist.
- Using a private or personal email route.
- Accepting a booking.
- Declining a booking.
- Negotiating fees, travel, hospitality, set time, billing, exclusivity, radius clauses, or contract terms.
- Confirming availability.
- Placing, confirming, or modifying calendar holds.
- Creating, updating, or deleting calendar events if connected later.
- Writing to an external CRM or spreadsheet if connected later.
- Adding or removing someone from the do-not-contact list.
- Marking an opportunity as `Booked`, `Rejected`, `Do Not Contact`, or `Closed`.
- Making any irreversible external change.

Approval must be explicit, action-specific, and current. Do not infer approval from broad instructions, prior approvals, mood, urgency, or Auto Mode.

## Actions Allowed Without Approval

The following actions are allowed without explicit approval when they stay internal and local:

- Reading existing project files.
- Reading `booking-state.md`.
- Summarizing known information.
- Classifying internal notes.
- Preparing a draft for review.
- Preparing a proposed CRM row without writing externally.
- Preparing a proposed calendar hold without creating it externally.
- Identifying missing information.
- Recommending next steps.
- Updating local markdown state if the user has asked for that workflow and no external action is taken.

When preparing something that could later be executed, label it as a proposal or draft and record any required approval gate.

## Prepare Versus Execute

Keep preparation and execution separate:

- "Prepare a draft" means write text for human review. It does not mean send, create a Gmail draft, reply, forward, or contact anyone.
- "Suggest a calendar hold" means propose a date/time and rationale. It does not mean create, confirm, or modify a calendar event or hold.
- "Recommend follow-up" means describe the next step. It does not mean contact them.
- "Prepare a CRM row" means produce a proposed row or local note. It does not mean write to an external CRM or spreadsheet.
- "Classify an opportunity" means assign an internal working label. It does not mean mark it `Booked`, `Rejected`, `Do Not Contact`, or `Closed`.

If the user asks to execute after preparation, create or update an approval request first unless the exact action has already been explicitly approved.

## Risk Levels

Use these risk levels in approval requests and state:

- `Low`: Internal-only note, summary, classification, or draft preparation.
- `Medium`: Proposed external-facing communication or CRM/calendar change not yet executed.
- `High`: Action involving money, dates, negotiation, reputation, private contacts, legal/contractual terms, or do-not-contact changes.
- `Blocked`: Action is unsafe, spammy, unsupported, unverified, or conflicts with a do-not-contact or safety rule.

When multiple levels apply, use the highest applicable level.

## Approval Request Format

Use this format whenever approval is required:

```markdown
## Approval Request: ACT-###

- Action ID: ACT-###
- Proposed action:
- Target:
- Reason:
- Source/evidence:
- Risk level:
- What will change:
- What will not happen yet:
- Required human decision:
- Expiration or timing sensitivity:
```

The required human decision must be concrete, for example: `Approve sending this exact email to booking@example.com`, `Reject this action`, or `Revise before approval`.

Do not bundle unrelated external actions into one approval. Create separate action IDs for separate sends, contacts, calendar changes, CRM writes, do-not-contact changes, booking acceptances, booking declines, or negotiation moves.

## Required Logging Behavior

Use `skills/booking-state/SKILL.md` whenever a workflow needs to read, initialize, or update `booking-state.md`.

Before requesting approval:

- Read the current booking state if one exists.
- Create or update the relevant local proposal, draft, opportunity, contact, calendar action, CRM/spreadsheet action, or risk record.
- Add an `Approval Queue` entry with status `Needs approval`, unless the action is `Blocked`.

When approval is granted:

- Confirm the approval is explicit and action-specific.
- Log the approval in `Approval Queue` and `Decision Log` before or alongside the action.
- Preserve who approved it, the date or timestamp, the action ID, the evidence, and the resulting state change.

When approval is rejected:

- Update the `Approval Queue` status to `Rejected`.
- Add a `Decision Log` entry with the rationale if provided.
- Do not execute the action.

When approval is unclear:

- Mark the approval as `Needs clarification` or leave it `Needs approval`.
- Ask a clarifying question.
- Do not execute the action.

When an action is blocked:

- Mark the action as `Blocked`.
- Explain the specific safety, evidence, do-not-contact, support, or spam concern.
- Add or update a `Risk Register` entry when the concern affects future booking work.
- Do not execute the action.

## Booking-State Updates

Approval Queue entries should include:

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

Decision Log entries should include:

- Decision ID.
- Related action ID.
- Decision.
- Human approver.
- Timestamp/date.
- Rationale.
- Resulting state change.

Use stable IDs such as `ACT-001` and `DEC-001`. Preserve append-only audit history. If an approval changes, update status/date fields and add notes or a decision entry rather than erasing the original context.

## Ambiguous User Instructions

If the user says something ambiguous like "handle it", "take care of it", "go ahead", "proceed", "sort it", or "do the update", do not treat that as approval for an external or consequential action.

Clarify the exact action:

```markdown
I can prepare the next step internally, but I need explicit approval before executing it externally.

Please confirm the exact action you want approved:
- Action ID:
- External action:
- Target:
- Scope:
```

If the user approves one specific action, execute only that action. Do not infer approval for follow-ups, related contacts, future sends, calendar changes, CRM writes, negotiation points, or status changes.

## Blocking Unsafe Or Premature Actions

Block or pause actions when:

- The action conflicts with a do-not-contact entry or safety note.
- The contact route is private/personal and has not been explicitly approved.
- The target, source, or evidence is unverified.
- The action would spam, mass-contact, or bypass appropriate consent.
- The action would misrepresent the artist, availability, relationship, fee, lineup, credentials, or authority.
- The user has not approved the exact external change.
- The tool or connector needed for the action is unsupported or out of scope.
- The action requires Gmail, Calendar, Sheets, APIs, scraping, or automation behavior that has not been implemented in the current workflow.

Offer a safe internal alternative, such as researching official sources, preparing a draft for review, identifying missing information, or creating an approval request.

## Auditability Rules

- Keep source links and user-provided evidence attached to claims and decisions.
- Distinguish confirmed facts, assumptions, and unknowns.
- Record who made each consequential decision when known.
- Preserve rejected, expired, blocked, and revised approvals.
- Never invent approval, contacts, availability, terms, credentials, or source evidence.
- Never silently convert a prepared item into an executed external action.
- Treat external send/write tools as approval-gated even if they become technically available later.
