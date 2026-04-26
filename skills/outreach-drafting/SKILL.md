---
name: outreach-drafting
description: Prepare safe, source-backed CircuitScout booking outreach drafts for human review after fit classification and contact verification.
---

# Outreach Drafting

CircuitScout uses outreach drafting to prepare booking emails, follow-ups, and reply text for human review.

Core question: given a qualified opportunity and a verified or likely contact route, what is the best personalized outreach draft to prepare for review?

This is an internal drafting workflow. It does not require human approval by itself when it only creates draft text or updates local `booking-state.md` draft records. Any external-facing next action, including sending, replying, forwarding, creating a Gmail draft if connected later, submitting a form, sending a social DM, writing to a CRM/spreadsheet, or scheduling anything, must route through `skills/approval-before-action/SKILL.md`.

Do not implement Gmail, Calendar, Sheets, APIs, scraping, OCR, automation, actual sending, forwarding, replying, scheduling, or external CRM/spreadsheet writes inside this skill. Mark missing information as `Unknown` or use clear placeholders. Never invent artist credentials, contacts, fees, availability, lineups, support history, relationships, or source evidence.

## When To Use

Use this skill after:

1. `skills/fit-classification/SKILL.md` has classified the opportunity.
2. `skills/contact-verification/SKILL.md` has verified or likely-confirmed a safe contact route.

Use it to prepare:

- Initial booking pitch.
- Short warm intro.
- Follow-up 1.
- Follow-up 2.
- Final soft close.
- Reply draft to inbound interest, if future inbox-triage provides context.
- Asset/EPK follow-up.
- Availability check response draft.

Read `booking-state.md` first when it exists, especially:

- `Artist Profile`
- `Positioning / Sound / Scene Fit`
- `EPK Assets`
- `Target Markets`
- `Booking Goals`
- `Opportunity Pipeline`
- `Contact Register`
- `Draft Outbox`
- `Outreach Log`
- `Follow-up Queue`
- `Inbox / Reply Status`
- `Risk Register`
- `Do-not-contact List`

Also use any user-provided context, constraints, tone preferences, previous outreach history, fit-classification output, and contact-verification output.

## Hard Gate

Drafting may proceed only when all conditions are true:

- Opportunity classification is `A`, `B`, or an explicitly approved `C`/`Monitor` for a specific reason.
- Contact route confidence is `Verified` or `Likely`.
- No do-not-contact conflict exists.
- Required artist facts and assets are present, or missing fields are clearly marked.
- No serious red flags block outreach.

If any condition is not met, do not write the outreach draft. Output a `Not ready to draft` report instead.

### Not Ready To Draft Report

Use this structure when the hard gate fails:

```markdown
## Not Ready To Draft: [Opportunity name]

- Opportunity ID:
- Contact ID:
- Requested draft type:
- Gate status: Not ready

### Missing Or Blocking Requirements

-

### Confirmed Facts Available

-

### Unknowns

-

### Risks / Red Flags

-

### Recommended Next Action

-

### booking-state.md Updates Required

-
```

Do not include subject lines or an email body in a `Not ready to draft` report.

## Tone Rules

Drafts must be:

- Concise.
- Human.
- Specific.
- Respectful.
- Non-cringey.
- Free of fake hype.
- Free of mass-email feel.
- Free of desperate language.
- Free of overclaiming.
- Free of manipulative urgency.
- Aligned with artist positioning.
- Adapted to the event, promoter, scene, location, and contact route.

Use clear, natural language. Prefer a grounded reason for fit over broad praise.

## Personalization Rules

Use confirmed evidence from:

- Event, festival, club, promoter, collective, radio show, or series identity.
- Past, current, or announced lineup.
- Flyer or lineup analysis.
- Scene or culture fit.
- Location and market context.
- The specific reason the artist fits this opportunity.

Never invent:

- Previous relationship.
- Previous support.
- Booking history.
- Press quotes.
- Streaming numbers.
- Fees.
- Availability.
- Travel plans.
- Namedrops.
- Promoter names.
- Lineup facts.
- Contact names.
- Artist credentials.

If a useful detail is missing, either omit it or use a visible placeholder such as `[confirmed EPK link needed]`. Do not make the sentence sound confirmed when it is not.

## EPK And Asset Rules

If a draft references an EPK, mix, release, photo, bio, press kit, video, or other asset, the asset must come from `booking-state.md` or user-provided context.

If the right asset is missing:

- Use a placeholder.
- List it under `Missing fields/placeholders`.
- Recommend filling the asset before approval or sending.

Do not substitute unrelated links, search results, guessed URLs, or invented assets.

## Subject Line Guidance

Create 3-5 subject line options.

Avoid:

- Spammy language.
- Fake urgency.
- Excessive punctuation.
- All caps.
- Clickbait.
- Over-personalized claims that are not sourced.

Prefer subject lines that are direct, modest, and specific, such as:

- Artist name + event/series fit.
- Booking inquiry + artist name.
- Artist name for [event/series/market].

## Draft Type Guidance

### Initial Booking Pitch

Use when introducing the artist to a verified or likely route. Keep it short, include the strongest specific fit reason, and reference only confirmed EPK assets.

### Short Warm Intro

Use when the user wants a lighter first touch, a social DM-adapted message, or a contact route that benefits from brevity. It still requires approval before external use.

### Follow-up 1

Use about 7 days after first outreach by default. Keep it low-pressure, reference the prior message, and add one useful context point or asset if sourced.

### Follow-up 2

Use about 14 days after follow-up 1 by default. Keep it brief and respectful. Do not imply urgency unless the user provided a real timing reason.

### Final Soft Close

Use about 21-30 days after follow-up 2 by default. Close the loop gracefully and leave the door open for a future edition or better timing.

### Reply Draft To Inbound Interest

Use only when reliable inbound context is available. Do not confirm availability, fees, travel, calendar dates, contracts, or acceptance. Route any reply send through `skills/approval-before-action/SKILL.md`.

### Asset / EPK Follow-up

Use when the human or recipient asked for assets, or when a sourced missing asset has now been added. Include only confirmed links.

### Availability Check Response Draft

Use when responding to an availability inquiry. Do not confirm availability unless the user explicitly supplied the exact availability and approved the external reply. Use placeholders such as `[availability to confirm]` when needed.

## Follow-up Cadence Guidance

Default suggested cadence:

- Follow-up 1: 7 days after first outreach.
- Follow-up 2: 14 days after follow-up 1.
- Final soft close: 21-30 days after follow-up 2.

Then stop unless there is a real new reason to reconnect, such as a new edition, updated asset, relevant release, local routing opportunity, or human-provided context.

Follow-up planning is internal. Sending or creating external drafts requires `skills/approval-before-action/SKILL.md`.

## Output Format

Use this structure for each prepared draft:

```markdown
## Outreach Draft: DRF-###

- Draft ID:
- Opportunity ID:
- Contact ID:
- Draft type:
- Intended recipient/contact route:

### Subject Line Options

1.
2.
3.

- Recommended subject line:

### Email Draft


### Shorter Version


### Warmer Version


### Follow-up Variant If Useful


### Personalization Evidence Used

-

### Confirmed Facts Used

-

### Assumptions Avoided

-

### Missing Fields / Placeholders

-

### Risk Notes

-

### Approval Required Before Any External Action

- Yes. This draft is internal only. Sending, replying, forwarding, creating a Gmail draft, submitting a form, sending a DM, or writing externally requires `skills/approval-before-action/SKILL.md`.

### Recommended Next Action

-

### booking-state.md Updates Required

-
```

Keep the email draft easy to review and edit. Do not bury important placeholders.

## Booking-State Integration

Use `skills/booking-state/SKILL.md` when updating `booking-state.md`.

Prepared drafts belong in `Draft Outbox`, not `Outreach Log`.

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

Use draft statuses such as `Pending review`, `Needs revision`, `Approved for external action`, `Rejected`, `Replaced`, or `Archived`.

Drafts must not be marked as sent unless the human confirms they were sent manually or a future approved connector completes the send. When outreach is actually sent or externally executed, create or update the `Outreach Log` as a separate record.

If the draft recommends an external next action, create or update an `Approval Queue` entry only through `skills/approval-before-action/SKILL.md`.

## Safety Checklist

Before finalizing a draft, verify:

- The opportunity classification satisfies the hard gate.
- The contact route confidence is `Verified` or `Likely`.
- Do-not-contact status does not block outreach.
- The draft does not claim a prior relationship unless sourced.
- The draft does not claim availability, fees, travel plans, support history, booking history, press, metrics, or lineup facts unless sourced.
- Every asset link comes from `booking-state.md` or user-provided context.
- Missing facts are marked as placeholders or omitted.
- The recommended next action routes any external execution through `skills/approval-before-action/SKILL.md`.

