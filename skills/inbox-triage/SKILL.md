---
name: inbox-triage
description: Classify inbound booking-related replies or message summaries for CircuitScout, identify required internal action, and recommend safe booking-state updates before drafting or follow-up planning.
---

# Inbox Triage

CircuitScout uses inbox triage to understand inbound booking-related messages without taking external action.

Core question: given an inbound reply or message summary, what does it mean, what action is needed, and how should CircuitScout update booking state without sending, replying, confirming, negotiating, scheduling, or writing to external systems?

This is an internal classification and state-preparation workflow. It does not require human approval by itself when it only reviews user-provided message content or a future approved connector summary, classifies the reply, identifies risks, recommends next internal steps, and prepares local `booking-state.md` updates. Any external-facing or consequential action must route through `skills/approval-before-action/SKILL.md`.

Do not implement Gmail, Calendar, Sheets, APIs, scraping, OCR, automation, actual sending, forwarding, replying, scheduling, labeling, archiving, or external CRM/spreadsheet writes inside this skill. Do not connect to, read from, search, send, forward, reply to, label, archive, or modify Gmail. Never invent replies, dates, terms, fees, offers, contacts, message intent, availability, prior communication, or approval.

## When To Use

Use this skill when the user manually provides an inbound booking-related email, message body, excerpt, or summary, or when a future approved connector provides a message summary that needs safe interpretation.

Use it before follow-up planning whenever a reply exists.

Read `booking-state.md` first when it exists, especially:

- `Opportunity Pipeline`
- `Contact Register`
- `Draft Outbox`
- `Approval Queue`
- `Outreach Log`
- `Follow-up Queue`
- `Inbox / Reply Status`
- `Decision Log`
- `Risk Register`
- `Do-not-contact List`

Also use any related Opportunity Pipeline record, Contact Register record, Outreach Log record, Draft Outbox record, Follow-up Queue record, Approval Queue / Decision Log entry, and user-provided context or constraints.

If the message content is not available and only the existence of a reply is known, classify as `Ambiguous / needs clarification` and ask for the message text, excerpt, or reliable summary.

## Required Inputs

Inbox triage can work with partial context, but it must mark missing information as `Unknown` rather than inventing it.

Relevant inputs may include:

- User-provided email/message body, excerpt, or summary.
- Message source, such as user paste, manual summary, email client export, or future approved connector summary.
- Message date, if known.
- Sender/contact identity, if known.
- Related Opportunity Pipeline record, if known.
- Related Contact Register record, if known.
- Related Outreach Log record, if known.
- Related Draft Outbox record, if known.
- Follow-up Queue record, if known.
- Approval Queue / Decision Log records, if relevant.
- User-provided context or constraints.

## Reply Categories

Use one primary reply category and optional secondary flags when needed:

- `Positive interest`
- `Request for more information`
- `Request for EPK/assets`
- `Availability check`
- `Fee/budget discussion`
- `Offer or tentative offer`
- `Confirmed booking request`
- `Rejection / not a fit`
- `No budget`
- `Lineup already closed`
- `Redirect to another contact`
- `Out of office / automated response`
- `Bounce / failed delivery`
- `Unsubscribe / do not contact request`
- `Negative or hostile reply`
- `Needs human decision`
- `Urgent / time-sensitive`
- `Ambiguous / needs clarification`
- `Spam / irrelevant`

If more than one category appears, choose the one with the highest safety impact as primary. For example, a positive message that discusses fees should be `Fee/budget discussion` with a `Positive interest` note, because money requires human decision.

If the message is ambiguous, classify it as `Ambiguous / needs clarification`.

## Extraction Checklist

Extract only what is present in the message, related records, or user-provided context:

- Sender/contact identity.
- Organization/event.
- Related opportunity.
- Reply category.
- Sentiment/tone.
- Requested action.
- Deadline or timing sensitivity.
- Dates mentioned.
- Fee/budget terms mentioned.
- Availability terms.
- Requested assets.
- Redirect contact if provided.
- Do-not-contact instruction.
- Bounce/failure details.
- Uncertainty/missing context.
- Risks.

Separate confirmed facts from assumptions and unknowns. Preserve exact terms when they matter, but do not embellish. If a message implies a next step but does not clearly request one, mark that as an assumption.

## Risk Levels

Use the highest applicable risk level:

- `Low`: Informational reply, no external commitment, no deadline.
- `Medium`: Needs reply, asset request, redirect, or unclear next action.
- `High`: Money, dates, availability, booking offer, negotiation, reputation risk, legal/contractual terms, do-not-contact change, hospitality, travel, contracts, exclusivity, billing, or set time.
- `Blocked`: Unsafe, do-not-contact, spam, hostile, bounced route, impossible to verify, or conflicts with safety rules.

If the message includes dates, fees, hospitality, travel, contracts, exclusivity, billing, set time, or availability, flag as `High` and route the next external or consequential action through `skills/approval-before-action/SKILL.md`.

## Hard Rules

- Never treat an inbound message as permission to accept a booking.
- Never confirm availability.
- Never negotiate fees or terms.
- Never mark a booking as `Booked` without explicit human approval.
- Never add or contact a new redirect contact without verification and approval.
- Never continue follow-ups after a do-not-contact or unsubscribe request.
- Never invent message content or intent.
- If the message is ambiguous, classify as `Ambiguous / needs clarification`.
- If the message contains a do-not-contact request, recommend updating `Do-not-contact List` through `skills/approval-before-action/SKILL.md`.
- If the message is a bounce, pause follow-up and route back to `skills/contact-verification/SKILL.md`.
- If the message requests assets, prepare an internal recommended reply path but do not send.
- If the message includes dates, fees, hospitality, travel, contracts, exclusivity, billing, set time, or availability, flag as `High risk / human decision`.

## Category Handling

### Positive Interest

Identify what the sender is positive about and whether they asked for a reply, assets, availability, dates, or terms. Do not treat interest as a booking confirmation. Recommend internal reply drafting through `skills/outreach-drafting/SKILL.md` when a reply is needed.

### Request For More Information

List the requested information and whether it is already confirmed in `booking-state.md`. If facts are missing, recommend filling them before drafting. Any reply requires approval before external action.

### Request For EPK/assets

List requested assets and compare them to `EPK Assets`. Recommend an internal `Asset / EPK follow-up` draft through `skills/outreach-drafting/SKILL.md`. Do not send assets or create a Gmail draft without approval.

### Availability Check

Flag as `High`. Do not confirm availability. Recommend a human decision and, if appropriate, a reply draft with `[availability to confirm]` placeholders.

### Fee/Budget Discussion

Flag as `High`. Extract stated budget, fee range, currency, payment timing, travel/hospitality mentions, and unknowns. Do not negotiate or imply acceptance.

### Offer Or Tentative Offer

Flag as `High`. Extract dates, venue/event, billing, set time, fee, travel, hospitality, contract, deadline, and conditions if present. Recommend human decision. Do not mark `Booked`.

### Confirmed Booking Request

Flag as `High`. Treat it as a request requiring human approval, not as acceptance. Do not confirm dates, availability, or acceptance. Recommend approval-gated decision handling.

### Rejection / Not A Fit, No Budget, Or Lineup Already Closed

Recommend pausing or stopping follow-ups for this opportunity/contact as appropriate. If the opportunity may be relevant later, recommend `Monitor next edition` rather than another follow-up. Do not mark `Rejected` or `Closed` as a consequential status without approval if the local workflow treats that status as approval-gated.

### Redirect To Another Contact

Extract the redirect contact exactly as provided. Do not add or contact the redirect route without `skills/contact-verification/SKILL.md` and approval for any external action. Pause follow-up to the old route until the redirect is verified.

### Out Of Office / Automated Response

Extract return date, alternate contact, and instructions if present. If an alternate contact is provided, route to contact verification before any outreach. Adjust follow-up timing only as an internal recommendation.

### Bounce / Failed Delivery

Flag as `Blocked`. Extract bounce reason, failed address/route, error code, and delivery status if present. Pause or stop follow-up on that route and route back to `skills/contact-verification/SKILL.md`.

### Unsubscribe / Do Not Contact Request

Flag as `Blocked`. Recommend no further follow-ups. Recommend a do-not-contact update through `skills/approval-before-action/SKILL.md` if the local or external record needs to change. Do not send a reply unless the user explicitly asks and approval is handled.

### Negative Or Hostile Reply

Flag as `Blocked` or `High` depending on severity. Recommend stopping follow-up, recording reputation risk, and asking for human decision before any response.

### Spam / Irrelevant

Flag as `Blocked` when it is unsafe or unrelated. Recommend no booking action and avoid creating follow-up tasks.

## Output Format

Use this structure:

```markdown
## Inbox Triage: TRI-###

- Triage ID:
- Related opportunity ID:
- Related contact ID:
- Related outreach ID:
- Message source:
- Message date if known:
- Sender / organization:
- Reply category:
- Sentiment / tone:
- Summary:

### Confirmed Facts From Message

-

### Assumptions

-

### Unknowns

-

### Requested Action

-

### Deadline / Timing Sensitivity

-

### Dates, Fees, Availability, And Terms Mentioned

-

### Requested Assets

-

### Redirect Contact

-

### Do-not-contact Instruction

-

### Bounce / Failure Details

-

### Risks

- Risk level:
- Risk notes:

### State Updates Recommended

-

### Follow-up Queue Impact

-

### Do-not-contact Impact

-

### Contact-verification Impact

-

### Fit-classification Impact If Relevant

-

### Recommended Next Internal Step

-

### Approval Required Before Any External Action

- Yes. Inbox triage is internal only. Replying, forwarding, creating a Gmail draft, contacting a redirect, updating do-not-contact externally, changing CRM/spreadsheet externally, confirming dates, accepting or declining bookings, or negotiating terms requires `skills/approval-before-action/SKILL.md`.

### booking-state.md Updates Required

-
```

Use `Unknown` for missing fields. Use `None identified` only when the message has been checked and the item is genuinely absent.

## Booking-State Integration

Use `skills/booking-state/SKILL.md` when updating `booking-state.md`.

Store triage results in `Inbox / Reply Status` or a linked note. Entries should support:

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

Update `Follow-up Queue` recommendations when a reply makes follow-up inappropriate:

- Negative replies, do-not-contact requests, bounces, hostile replies, no-budget replies, closed lineups, or irrelevant/spam replies should pause or stop follow-ups.
- Asset requests, positive interest, availability checks, and more-information requests may create a reply-draft task, not an automatic send.
- Bounce replies should pause the current route and route back to contact verification.

Update `Contact Register` recommendations when a reply changes contact confidence:

- Bounced contacts should trigger `skills/contact-verification/SKILL.md` before new outreach.
- Redirected contacts should be treated as unverified until `skills/contact-verification/SKILL.md` checks them.
- Do-not-contact requests should be reflected in permission/safety notes and routed through approval-before-action before any consequential local or external do-not-contact change.

Update `Opportunity Pipeline` only with careful recommendations:

- Positive interest may move the next action toward internal reply drafting.
- Closed lineup may recommend `Monitor next edition`.
- Rejection/no budget may recommend pausing or stopping pursuit.
- Offers, dates, fees, availability, contracts, or booking requests should recommend human decision rather than changing booked/closed status.

Do not mark an opportunity as `Booked`, `Rejected`, `Do Not Contact`, or `Closed` without explicit human approval if that status change is treated as consequential in the workflow.

## Integration With Other CircuitScout Skills

- Use `skills/outreach-drafting/SKILL.md` after triage when the safe next step is an internal reply draft, asset response draft, or availability-placeholder draft for human review.
- Use `skills/followup-planning/SKILL.md` only after triage when a reply exists and triage says follow-up remains appropriate.
- Use `skills/contact-verification/SKILL.md` when the message bounced, redirects to another contact, raises contact confidence concerns, or identifies an alternate contact.
- Use `skills/fit-classification/SKILL.md` when the reply changes fit evidence, timing, lineup status, opportunity priority, or whether the opportunity should be monitored.
- Use `skills/approval-before-action/SKILL.md` before replying, forwarding, creating a Gmail draft, contacting a redirect, updating do-not-contact externally, writing to CRM/spreadsheet externally, confirming dates, accepting or declining bookings, negotiating terms, or changing a consequential booking status.

## Safety Checklist

Before finalizing triage, verify:

- The message content or summary was user-provided or came from a future approved connector summary.
- No Gmail, Calendar, Sheets, API, scraping, OCR, automation, sending, forwarding, replying, scheduling, labeling, archiving, or external write behavior was performed.
- The reply category is supported by the message content.
- Confirmed facts, assumptions, and unknowns are separated.
- Dates, fees, availability, hospitality, travel, contracts, exclusivity, billing, set time, and deadlines are flagged as high risk when present.
- Do-not-contact and unsubscribe instructions stop follow-up recommendations.
- Bounces route back to contact verification.
- Redirect contacts are not used before verification and approval.
- Any external or consequential next action routes through `skills/approval-before-action/SKILL.md`.
