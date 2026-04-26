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
- An opportunity receives or changes a fit score, fit classification, score breakdown, red flags, recommended next action, or contact-research recommendation.
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

- `Draft Outbox`
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

## Opportunity Pipeline Guidance

`Opportunity Pipeline` entries should support:

- Opportunity ID.
- Name.
- Type.
- City and country.
- Source links.
- Status.
- Priority.
- Fit score.
- Fit classification.
- Score breakdown.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Red flags.
- Recommended next action.
- Contact research next.
- Owner.
- Notes.

Use `skills/fit-classification/SKILL.md` before contact verification or outreach drafting. Keep score evidence traceable to source links, user-provided context, or clearly labeled assumptions. If a recommended next action is external-facing or consequential, route it through `skills/approval-before-action/SKILL.md`.

## Contact Register Guidance

Use `skills/contact-verification/SKILL.md` after fit classification and before outreach drafting.

`Contact Register` entries should support:

- Contact ID.
- Opportunity ID.
- Name.
- Organization.
- Role.
- Contact route type.
- Contact value/route.
- Source link.
- Source type.
- Confidence.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Duplicate/conflict notes.
- Permission/safety notes.
- Do-not-contact status.
- Last verified date.
- Next action.

Use confidence values from contact verification: `Verified`, `Likely`, `Uncertain`, `Do not use`, or `Unknown`. If confidence is below `Likely`, do not route the opportunity to outreach drafting yet. If the route conflicts with a do-not-contact entry or appears private, guessed, leaked, suspicious, outdated, or unsafe, mark it `Do not use`, record the safety reason, and recommend more research or a human check rather than outreach.

Bounced contacts and redirected contacts should trigger `skills/contact-verification/SKILL.md` before any new outreach. A bounced route should be paused or marked unsafe for the current outreach path. A redirect contact should remain unverified until contact verification confirms source quality, role fit, permission/safety notes, and whether outreach drafting can happen next.

Contact verification may prepare a proposed local contact record without approval. Any external-facing next action, including email, contact form submission, social DM, Gmail draft creation if connected later, CRM/spreadsheet writes, or contact through a private route, must route through `skills/approval-before-action/SKILL.md`.

## Draft Outbox Guidance

Use `skills/outreach-drafting/SKILL.md` after contact verification and before approval-before-action to prepare source-backed outreach drafts for human review.

`Draft Outbox` entries should support:

- Draft ID.
- Opportunity ID.
- Contact ID.
- Draft type.
- Intended recipient/contact route.
- Subject.
- Draft status.
- Created date.
- Source evidence.
- Confirmed facts used.
- Missing fields.
- Risk notes.
- Approval action ID if created later.
- Sent status.
- Sent date.
- Follow-up due date.
- Notes.

Prepared drafts are internal review records. Use statuses such as `Pending review`, `Needs revision`, `Approved for external action`, `Rejected`, `Replaced`, or `Archived`. Do not mark a draft as sent unless the human confirms it was sent manually or a future approved connector completes the send.

Draft Outbox is not Outreach Log. Draft Outbox records prepared text and review status. Outreach Log records sent or externally executed outreach only.

If a draft recommends sending, replying, forwarding, creating a Gmail draft if connected later, using a contact form, sending a social DM, or writing externally, route the proposed action through `skills/approval-before-action/SKILL.md`. Store the resulting approval action ID on the draft only after the approval request exists.

## Outreach Log Guidance

`Outreach Log` records sent or externally executed outreach only. Prepared drafts and planned follow-ups must not be copied into Outreach Log or marked as sent before external action occurs. Use `Follow-up Queue` for planned internal follow-up state.

`Outreach Log` entries should support:

- Outreach ID.
- Opportunity ID.
- Contact ID.
- Channel.
- Subject.
- Draft/source.
- Sent status.
- Sent date.
- Approved by human.
- Follow-up due date.
- Notes.

## Follow-up Queue Guidance

Use `skills/followup-planning/SKILL.md` after reviewing `Outreach Log` and `Inbox / Reply Status`, and before approval-before-action for any external follow-up action.

`Follow-up Queue` records planned internal follow-up state. It is not the `Outreach Log`; prepared follow-up drafts must not be marked as sent unless the human confirms they were sent manually or a future approved connector completes the send.

`Follow-up Queue` entries should support:

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

Use statuses such as `Not ready`, `Planned`, `Due`, `Pending review`, `Needs approval`, `Approved for external action`, `Sent`, `Paused`, `Stopped`, or `Cancelled`.

Follow-up planning may proceed only when there is a real prior outreach event in `Outreach Log` or the user explicitly says they sent the outreach manually, the contact route is still `Verified` or `Likely`, no do-not-contact conflict exists, the opportunity status does not block follow-up, reply status does not make follow-up inappropriate, and cadence limits have not been exceeded.

Negative replies, do-not-contact requests, bounces, hostile replies, no-budget replies, closed lineups, spam, or irrelevant replies should pause or stop follow-ups. Asset requests, positive interest, availability checks, and more-information requests may create an internal reply-draft task, not an automatic send. If a reply exists, run `skills/inbox-triage/SKILL.md` before follow-up planning and use the triage result to decide whether follow-up remains appropriate.

If follow-up planning recommends sending, replying, forwarding, creating a Gmail draft if connected later, using a contact form, sending a social DM, creating a calendar reminder, scheduling anything, or writing externally, route the proposed action through `skills/approval-before-action/SKILL.md`. Store the resulting approval action ID only after the approval request exists.

## Inbox / Reply Status Guidance

Use `skills/inbox-triage/SKILL.md` when the user provides an inbound booking-related message, excerpt, or summary, or when a future approved connector provides a message summary. Inbox triage is internal and does not require approval when it only classifies the message, extracts confirmed facts, identifies risks, recommends local state updates, and chooses the next internal step.

`Inbox / Reply Status` entries should support:

- Triage ID.
- Opportunity ID.
- Contact ID.
- Outreach ID.
- Message source.
- Message date.
- Sender / organization.
- Reply category.
- Summary.
- Requested action.
- Deadline / timing sensitivity.
- Risk level.
- State impact.
- Follow-up impact.
- Do-not-contact impact.
- Recommended next internal step.
- Approval action ID if created later.
- Notes.

Use reply categories from inbox triage, such as `Positive interest`, `Request for more information`, `Request for EPK/assets`, `Availability check`, `Fee/budget discussion`, `Offer or tentative offer`, `Confirmed booking request`, `Rejection / not a fit`, `No budget`, `Lineup already closed`, `Redirect to another contact`, `Out of office / automated response`, `Bounce / failed delivery`, `Unsubscribe / do not contact request`, `Negative or hostile reply`, `Needs human decision`, `Urgent / time-sensitive`, `Ambiguous / needs clarification`, or `Spam / irrelevant`.

Do not treat an inbound reply as permission to accept a booking, confirm availability, negotiate terms, contact a redirect, update external systems, or mark an opportunity as `Booked`. Any external or consequential action must route through `skills/approval-before-action/SKILL.md`.

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
