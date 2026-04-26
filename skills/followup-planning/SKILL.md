---
name: followup-planning
description: Plan safe, non-spammy CircuitScout booking follow-ups after real outreach, using outreach history, reply status, cadence, contact confidence, and approval gates.
---

# Follow-up Planning

CircuitScout uses follow-up planning to decide whether a booking opportunity should receive another follow-up, what type of follow-up is appropriate, and what internal state should change before any external action.

Core question: given a draft/outreach history, reply status, opportunity priority, and contact confidence, what is the appropriate next follow-up action, if any?

This is an internal planning and drafting workflow. It does not require human approval by itself when it only reviews state, recommends next steps, prepares follow-up text, or updates local `booking-state.md` follow-up records. Any external-facing action, including sending, replying, forwarding, creating a Gmail draft if connected later, using a contact form, sending a social DM, creating a calendar reminder, scheduling anything, or writing to an external CRM/spreadsheet, must route through `skills/approval-before-action/SKILL.md`.

Do not implement Gmail, Calendar, Sheets, APIs, scraping, OCR, automation, actual sending, forwarding, replying, scheduling, or external CRM/spreadsheet writes inside this skill. Never invent replies, prior outreach, approvals, dates, contact status, sent history, or reasons to reconnect. Mark missing information as `Unknown`.

## When To Use

Use this skill after outreach has been reviewed and before any approval-gated external follow-up action when CircuitScout needs to:

- Decide whether a follow-up is appropriate.
- Prepare a follow-up draft for human review.
- Determine whether to pause, stop, monitor the next edition, or route back to contact verification.
- Update or create a local `Follow-up Queue` record.
- Explain why a follow-up is blocked or premature.

Read `booking-state.md` first when it exists, especially:

- `Opportunity Pipeline`
- `Contact Register`
- `Draft Outbox`
- `Outreach Log`
- `Follow-up Queue`
- `Inbox / Reply Status`
- `Approval Queue`
- `Decision Log`
- `Risk Register`
- `Do-not-contact List`

Also use user-provided context or constraints, but do not treat user context as sent history unless the user explicitly says they sent the outreach manually.

## Required Inputs

Follow-up planning requires the relevant records from:

- `booking-state.md`.
- `Opportunity Pipeline`.
- `Contact Register`.
- `Draft Outbox`.
- `Outreach Log`.
- `Follow-up Queue`, if it exists.
- `Inbox / Reply Status`, if available.
- `Approval Queue` and `Decision Log`, if relevant.
- User-provided context or constraints.

If any required record is missing, do not fill it in from imagination. Either use a clearly labeled `Unknown` value or output a `Not ready for follow-up` report.

## Hard Gate

Follow-up planning may prepare follow-up text only when all conditions are true:

- There is a real prior outreach event logged in `Outreach Log`, or the user explicitly says they sent the outreach manually.
- The contact route confidence is `Verified` or `Likely`.
- No do-not-contact conflict exists.
- The opportunity is not marked `Booked`, `Closed`, `Rejected`, `Do Not Contact`, or `Blocked`.
- No reply has already made follow-up inappropriate.
- The follow-up count is within the allowed cadence.

If any condition is not met, do not prepare subject lines or follow-up text. Output a `Not ready for follow-up` report.

## Not Ready For Follow-up Report

Use this structure when the hard gate fails:

```markdown
## Not Ready For Follow-up

- Opportunity ID:
- Contact ID if known:
- Reason follow-up is blocked:
- Missing required records:
- Safety issue or cadence issue:
- Recommended internal next step:
- booking-state.md updates required:
```

Keep the report practical and specific. Do not include draft text, subject lines, or send instructions.

## Cadence Rules

Default cadence:

- Follow-up 1: 7 days after first outreach.
- Follow-up 2: 14 days after follow-up 1.
- Final soft close: 21-30 days after follow-up 2.
- Then stop unless there is a real new reason to reconnect.

Follow-up count rules:

- Do not recommend more than 3 follow-ups without a real new reason.
- Stop immediately if the contact replied negatively.
- Stop immediately if the contact asked not to be contacted.
- Stop if the event date has passed unless there is a relationship-building reason.
- Stop if the opportunity is no longer relevant.
- If the lineup is likely closed, recommend `Monitor next edition` instead of another follow-up.
- If the previous email bounced, do not continue with the same route.
- If contact confidence drops below `Likely`, pause and route back to `skills/contact-verification/SKILL.md`.

The recommended send window may be a date range, such as `2026-05-04 to 2026-05-06`, or a relative window, such as `7 days after confirmed send date`, when dates are missing. Do not invent exact dates.

## Follow-up Types

Use one of these follow-up types:

- `Follow-up 1`: gentle check-in.
- `Follow-up 2`: concise reminder with value/context.
- `Final soft close`: respectful close-the-loop.
- `New-reason reconnect`: only if there is a real new release, mix, tour route, support, updated EPK, or event-specific reason.
- `Asset follow-up`: only if the contact requested assets or missing information.
- `Reply follow-up`: only if future inbox-triage provides real inbound context.

Do not classify a message as `New-reason reconnect`, `Asset follow-up`, or `Reply follow-up` unless the reason is supported by `booking-state.md`, user-provided context, or a real inbound reply record.

## Reply Status Rules

Before preparing a follow-up, inspect `Inbox / Reply Status` and any user-provided reply context.

Stop or pause when:

- The recipient declined, rejected, passed, or indicated the opportunity is not relevant.
- The recipient asked not to be contacted.
- The recipient requested a different route or person and that route is not verified yet.
- The reply requires a substantive answer, negotiation, availability confirmation, fee discussion, or date commitment.
- The reply asks for assets that are missing or unconfirmed.
- The reply makes the opportunity inappropriate, closed, or unsafe.

When a reply requires a response draft, do not invent the response. Use only the inbound context and route any external reply through `skills/approval-before-action/SKILL.md`.

## Tone Rules

Follow-ups must be:

- Respectful.
- Brief.
- Specific.
- Low-pressure.
- Non-spammy.
- Free of guilt-tripping.
- Free of fake urgency.
- Free of exaggerated hype.
- Aligned with artist positioning.
- Natural enough not to sound automated.

Avoid using `just following up` as the only content when possible. Add one useful, sourced context point, such as the artist/opportunity fit reason, a confirmed asset, or a real new reason to reconnect.

Never claim:

- A prior relationship unless sourced.
- Availability unless the user explicitly provided it.
- Fees, travel plans, routing, support history, booking history, press, or metrics unless sourced.
- That the recipient requested something unless there is a real reply or user-provided confirmation.

## Output Format

Use this structure when a follow-up is appropriate:

```markdown
## Follow-up Plan: FUP-###

- Follow-up ID:
- Opportunity ID:
- Contact ID:
- Related outreach ID:
- Related draft ID if any:
- Follow-up type:
- Current status:
- Last outreach date:
- Follow-up count:
- Recommended send window:
- Timing rationale:

### Subject Line Options

1.
2.
3.

- Recommended subject line:

### Follow-up Draft


### Shorter Version


### Soft-close Variant If Relevant


### Evidence / Context Used

-

### Blockers Checked

-

### Risk Notes

-

### Approval Required Before Any External Action

- Yes. This plan and draft are internal only. Sending, replying, forwarding, creating a Gmail draft, using a contact form, sending a DM, creating a calendar reminder, scheduling anything, or writing externally requires `skills/approval-before-action/SKILL.md`.

### Recommended Next Action

-

### booking-state.md Updates Required

-
```

Keep the draft easy to review and edit. Use placeholders only for facts that must be supplied before approval or sending.

## Booking-State Integration

Use `skills/booking-state/SKILL.md` when updating `booking-state.md`.

`Outreach Log` records sent or externally executed outreach only. It is the evidence that a follow-up may be considered. Prepared follow-up drafts must not be copied into `Outreach Log` or marked as sent before external action occurs.

`Follow-up Queue` records planned internal follow-up state. It may include:

- Follow-up ID.
- Opportunity ID.
- Contact ID.
- Related outreach ID.
- Related draft ID.
- Follow-up type.
- Status.
- Last outreach date.
- Follow-up count.
- Recommended send window.
- Due date.
- Timing rationale.
- Draft status.
- Approval action ID.
- Sent status.
- Sent date.
- Stop reason.
- Notes.

Use follow-up statuses such as `Not ready`, `Planned`, `Due`, `Pending review`, `Needs approval`, `Approved for external action`, `Sent`, `Paused`, `Stopped`, or `Cancelled`.

Prepared follow-up text may also be recorded in `Draft Outbox` as a follow-up draft when useful. If it is recorded there, link the `Draft ID` from `Follow-up Queue`. Do not mark the draft or follow-up as sent unless the human confirms it was sent manually or a future approved connector completes the send.

If follow-up planning recommends an external action, create or update the `Approval Queue` only through `skills/approval-before-action/SKILL.md`.

## Integration With Other CircuitScout Skills

- Use `skills/fit-classification/SKILL.md` when a follow-up depends on opportunity priority, timing, lineup openness, or whether the opportunity should now be monitored instead.
- Use `skills/contact-verification/SKILL.md` when contact confidence is below `Likely`, a bounce occurred, the contact route changed, a reply redirects to another contact, or any safety concern appears.
- Use `skills/outreach-drafting/SKILL.md` for initial outreach and general draft standards. Follow-up planning may prepare follow-up text only after the hard gate passes.
- Use `skills/approval-before-action/SKILL.md` before sending, replying, forwarding, creating a Gmail draft, using a contact form, sending a social DM, creating a calendar reminder, scheduling anything, or writing externally.

## Safety Checklist

Before finalizing a follow-up plan, verify:

- A real prior outreach event exists in `Outreach Log`, or the user explicitly confirmed manual sending.
- The last outreach date is known or clearly marked as `Unknown`.
- The follow-up count and cadence are within limits.
- Contact confidence is `Verified` or `Likely`.
- No do-not-contact conflict exists.
- Opportunity status does not block follow-up.
- Reply status does not make follow-up inappropriate.
- The event has not passed, unless the plan is a relationship-building note with a real reason.
- The previous outreach did not bounce on the same route.
- Any new reason to reconnect is real and sourced.
- All external execution routes through `skills/approval-before-action/SKILL.md`.
