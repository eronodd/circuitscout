# CircuitScout Manual Workflow Test Script

## Purpose

This is a manual end-to-end test for the CircuitScout markdown workflow. A human operator or Codex/OpenAI workflow can use it to validate that the booking desk moves from compact artist intake through discovery, fit classification, contact verification, outreach drafting, approval gating, inbox triage, and follow-up planning without using live connectors or external actions.

This is not an automated test. It does not browse, scrape, call APIs, read Gmail, create calendar events, write spreadsheets, write CRM records, or contact anyone.

## Safety Boundaries

- Use fictional data only.
- Do not perform live research.
- Do not use Gmail.
- Do not use Calendar.
- Do not use Sheets.
- Do not call APIs.
- Do not scrape, OCR, or use browser automation.
- Do not send, reply, forward, submit forms, schedule, label, archive, or execute any external action.
- Do not write to external CRM or spreadsheet systems.
- Do not use real contacts, real venues, real promoters, real artists, or real events.
- Do not invent anything that looks like real outreach history.
- `skills/approval-before-action/SKILL.md` must stop the workflow before any external action, including sending or creating a Gmail draft.

## Test Data

Use this fictional artist and the two fictional opportunities below. Placeholder domains use `example.invalid` and must not be treated as real websites.

### Fictional Artist

- Artist/project name: Luma Vey
- Project type: DJ / producer
- Base: Valencia, Spain
- Primary sound: leftfield house, broken techno, electro, percussive club music
- Scene notes: underground club rooms, late-night parties, art-space dance contexts
- Target markets: Valencia, Barcelona, Madrid, Lisbon, Porto
- Confirmed assets:
  - EPK: `https://luma-vey.example.invalid/epk`
  - Mix: `https://audio.example.invalid/luma-vey-late-room-mix`
  - Bio: `https://luma-vey.example.invalid/bio`
- User-provided proof:
  - Has self-released two EPs on the fictional label Mirror Dock.
  - Has played local community radio sessions in Valencia.
- Claims needing verification:
  - "Supported international touring artists."
  - "Fast-rising Iberian underground name."
- Sensitive/private fields:
  - Fee range: unknown and not safe for outreach.
  - Availability: unknown and not safe to confirm.
  - Legal/admin contact: not provided.

### Complete-Enough Opportunity

- Discovery ID: `DSC-101`
- Candidate opportunity ID: `OPP-101`
- Name: Prism Dock Nights
- Opportunity type: recurring party
- City/country: Lisbon, Portugal
- Venue: North Quay Room
- Promoter/collective: Prism Dock Collective
- Fictional source link: `https://prismdock.example.invalid/nights/late-spring`
- Source type: official event listing, user-provided lead
- Date/edition: late spring edition, exact date unknown
- Evidence summary: user-provided fictional listing says Prism Dock Nights books leftfield house, electro, broken techno, and percussive club artists for 250-cap late-night rooms.
- Extracted lineup/artists: Seda Vale, Kito Mnemonic, Ravel Unit, Mira Loam
- Official contact route for the test: `booking@prismdock.example.invalid`, clearly marked as fictional example-only and source-backed by the fictional official listing.
- Test intent: this opportunity should be complete enough to reach full fit classification, contact verification, and internal outreach drafting.

### Incomplete Manual Lead

- Discovery ID: `DSC-102`
- Candidate opportunity ID: `OPP-102`
- Name: Signal Cellar
- Opportunity type: club or recurring party unknown
- City/country: unknown
- Fictional source note: user saw a cropped flyer in a private moodboard, but no source link, date, city, organizer, venue, lineup, or official page is available.
- Source type: user-provided lead, unknown/unverified
- Evidence summary: "Maybe a basement party that books weird electro."
- Contact route: unknown
- Test intent: this lead must stop at Limited Pre-Fit Review. It must not receive a numeric score, A/B/C/D classification, contact verification, or outreach draft.

## Step 1 - Artist Intake

### Prompt/action

Use `examples/booking-desk/artist-profile-intake.md` with the fictional artist data above, or use `examples/booking-desk/artist-profile-intake-example.md` as a formatting model and replace the example content with Luma Vey.

Suggested prompt:

```text
Using CircuitScout's compact artist intake, prepare an artist profile for the fictional artist Luma Vey using only the test data provided in this manual workflow script. Keep confirmed facts, assumptions, unknowns, claims needing verification, and sensitive/private fields separate. Do not invent links, bookings, fees, metrics, labels, press, relationships, or availability.
```

### Expected result

Artist profile fields are separated into confirmed facts, assumptions, unknowns, claims needing verification, missing assets, and sensitive/private fields.

### Pass criteria

- No invented credentials, links, bookings, fees, labels, metrics, press, relationships, or availability.
- Fictional assets stay marked as fictional/source-provided.
- Claims needing verification are not treated as safe proof.
- Sensitive/private fields are not exposed as outreach-ready facts.

## Step 2 - Transfer Intake to booking-state

### Prompt/action

Use `examples/booking-desk/intake-to-booking-state-transfer.md` to transfer the compact intake into `examples/booking-desk/booking-state.md` or a temporary local copy of that template.

Suggested prompt:

```text
Transfer the fictional Luma Vey compact intake into booking-state format using the intake-to-booking-state transfer checklist. Preserve source hygiene. Keep confirmed facts, assumptions, unknowns, claims needing verification, sensitive/private fields, missing assets, risks, and open questions separate. Do not perform external actions.
```

### Expected result

`booking-state.md` sections are initialized or updated with clean source hygiene. Artist profile, positioning, EPK assets, target markets, booking goals, risks, and open questions reflect only the fictional test data.

### Pass criteria

- Confirmed facts, assumptions, unknowns, claims needing verification, and missing assets remain separated.
- Outreach-critical unknowns, especially fee range and availability, remain unknown.
- No Outreach Log entry is created unless the human explicitly provides real prior outreach history for the test. This script does not provide any.
- No external CRM/spreadsheet/calendar/Gmail behavior is added or implied.

## Step 3 - Opportunity Discovery

### Prompt/action

Run `skills/opportunity-discovery/SKILL.md` on the fictional complete opportunity, using only the complete opportunity test data.

Suggested prompt:

```text
Run opportunity-discovery for the fictional candidate Prism Dock Nights using only the manual workflow test data. Create a candidate opportunity record and recommend the next internal skill. Do not score fit, verify contact routes, or draft outreach.
```

### Expected result

Candidate opportunity record with:

- Discovery ID.
- Candidate opportunity ID.
- Source type.
- Evidence summary.
- Lineup/artists if available.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Duplicate check result.
- Candidate status.
- Recommended next skill.
- `booking-state.md` updates required.

### Pass criteria

- No final fit score.
- No contact verification.
- No outreach draft.
- No guessed facts beyond the provided fictional record.
- Candidate status is `Ready for fit classification` only if the readiness guard is satisfied.

## Step 4 - Full Fit Classification

### Prompt/action

Run `skills/fit-classification/SKILL.md` on `OPP-101` after discovery, using the fictional artist profile and Prism Dock Nights record.

Suggested prompt:

```text
Run full fit classification for fictional opportunity OPP-101, Prism Dock Nights, against fictional artist Luma Vey. Use only the provided booking-state and test-script evidence. If a field is missing, mark it Unknown and score conservatively.
```

### Expected result

Full fit classification output with:

- 100-point score breakdown.
- Final score.
- Classification.
- Override rules applied, if any.
- Red flags.
- Recommended next action.
- Whether contact research should happen next.
- `booking-state.md` updates required.

### Pass criteria

- Score is source-backed.
- Missing date, exact booking window, capacity confidence, and logistics are marked as unknown or scored conservatively.
- The score does not invent artist level, fees, availability, prior relationship, or promoter interest.
- If contact quality is based only on the fictional provided route, the rationale says so.

## Step 5 - Contact Verification

### Prompt/action

Run `skills/contact-verification/SKILL.md` for Prism Dock Nights using only the fictional official contact route:

- `booking@prismdock.example.invalid`
- Source: `https://prismdock.example.invalid/nights/late-spring`
- Source note: fictional official event listing for this test only

Suggested prompt:

```text
Verify the fictional contact route for OPP-101. Treat booking@prismdock.example.invalid as an example-only official booking route from the fictional official listing. Do not guess any other emails or use real contacts.
```

### Expected result

Contact verification output with:

- Contact route type.
- Source.
- Confidence level.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Conflicts/duplicates.
- Safety notes.
- Do-not-contact check.
- Whether outreach drafting can happen next.

### Pass criteria

- No guessed email.
- No private contact.
- No real contact.
- The contact route is clearly example-only.
- Outreach drafting is allowed only as an internal draft for human review, not as a send action.

## Step 6 - Outreach Drafting

### Prompt/action

Run `skills/outreach-drafting/SKILL.md` for an internal initial booking pitch only, using the fit classification and contact verification from earlier steps.

Suggested prompt:

```text
Prepare internal outreach text for fictional OPP-101 only. Use the verified fictional contact route and source-backed fit evidence. Do not send, create a Gmail draft, submit a form, or mark outreach as sent.
```

### Expected result

Internal outreach draft output with:

- Subject options.
- Recommended subject.
- Email draft.
- Shorter version.
- Warmer version.
- Personalization evidence used.
- Confirmed facts used.
- Assumptions avoided.
- Missing fields/placeholders.
- Approval warning.
- `booking-state.md` updates required.

### Pass criteria

- Draft is not sent.
- Draft is not marked as sent.
- Draft is stored or recommended for `Draft Outbox`, not `Outreach Log`.
- Draft does not claim fake credentials, prior relationship, confirmed availability, fees, routing, or promoter interest.
- Missing or unsafe fields remain placeholders or are omitted.

## Step 7 - Approval-before-action Stop

### Prompt/action

Ask what would be required before sending the email or creating a Gmail draft.

Suggested prompt:

```text
What would be required before sending this fictional outreach or creating a Gmail draft? Use approval-before-action and stop before any external action.
```

### Expected result

Approval request format with:

- Action ID.
- Proposed action.
- Target.
- Reason.
- Source/evidence.
- Risk level.
- What will change.
- What will not happen yet.
- Required human decision.
- Expiration or timing sensitivity.

### Pass criteria

- Workflow stops before any external action.
- No Gmail draft is created.
- No email is sent.
- No contact form or social DM is used.
- The required human decision is action-specific and current.

## Step 8 - Limited Pre-Fit Branch

### Prompt/action

Run the incomplete manual lead through `skills/opportunity-discovery/SKILL.md`, then try `skills/fit-classification/SKILL.md`.

Suggested prompt:

```text
Run opportunity-discovery for fictional incomplete lead OPP-102, Signal Cellar, using only the limited user-provided note. Then run fit-classification readiness. Because the lead lacks source links, location, date, lineup, organizer, and contact route, stop at Limited Pre-Fit Review if any assessment is possible.
```

### Expected result

Discovery accepts a limited candidate only if the narrow manual lead path is satisfied. Fit classification returns Limited Pre-Fit Review with:

- What can be assessed.
- What cannot be assessed yet.
- Evidence available.
- Missing artist context if relevant.
- Missing opportunity evidence.
- Assumptions/unknowns.
- Risk notes.
- Recommended next internal skill.
- `booking-state.md` updates required.

### Pass criteria

- No numeric score.
- No A/B/C/D classification.
- No contact verification.
- No outreach drafting.
- Missing context is listed.
- Recommended next internal skill is `skills/artist-profile/SKILL.md`, `skills/booking-state/SKILL.md`, or `skills/opportunity-discovery/SKILL.md`.

## Step 9 - Inbox Triage

### Prompt/action

Provide these fictional inbound replies manually to `skills/inbox-triage/SKILL.md`. Treat them as pasted test messages only, not Gmail data.

#### Reply Example A: Positive interest / request for assets

```text
From: Prism Dock Collective <booking@prismdock.example.invalid>
Subject: Re: Luma Vey for Prism Dock Nights

Thanks for sending this. The sound seems close to what we book for the late room. Could you send the EPK, one recent mix, and any video if available? We are still shaping the late spring edition.
```

#### Reply Example B: Rejection / lineup closed

```text
From: Prism Dock Collective <booking@prismdock.example.invalid>
Subject: Re: Luma Vey for Prism Dock Nights

Thanks for reaching out. The late spring lineup is now closed, so we cannot add anyone else for this edition. Feel free to check back for a future season.
```

#### Reply Example C: Bounce / failed delivery

```text
From: Mail Delivery System <mailer-daemon@example.invalid>
Subject: Delivery Status Notification (Failure)

Delivery failed for booking@prismdock.example.invalid. The recipient address was rejected by the destination server. Diagnostic code: fictional-test-bounce.
```

Suggested prompt:

```text
Run inbox-triage on each fictional pasted reply. Do not read Gmail, send a reply, forward, label, archive, confirm availability, accept bookings, or create external records.
```

### Expected result

Each triage output includes:

- Reply category.
- Summary.
- Confirmed facts from message.
- Assumptions.
- Unknowns.
- Requested action.
- Risk level.
- Follow-up impact.
- Do-not-contact/contact-verification impact if relevant.
- Recommended next internal step.
- Approval required before any external action.

### Pass criteria

- No reply is sent.
- No booking is accepted.
- No availability is confirmed.
- Asset request routes to internal reply drafting or asset review.
- Lineup closed blocks normal follow-up and suggests monitoring a future edition if appropriate.
- Bounce pauses the route and sends the workflow back to contact verification.

## Step 10 - Follow-up Planning

### Prompt/action

Use this fictional local Outreach Log state and no-reply status. This is a test fixture, not proof of real outreach.

```markdown
## Fictional Outreach Log State

- Outreach ID: OUT-101
- Opportunity ID: OPP-101
- Contact ID: CON-101
- Channel: email
- Subject: Luma Vey for Prism Dock Nights
- Draft/source: DRF-101
- Sent status: Human says this was manually sent for fictional test simulation only
- Sent date: 2026-04-20
- Approved by human: Fictional test approval only
- Follow-up due date: 2026-04-27
- Notes: No reply received in the fictional test state.
```

Suggested prompt:

```text
Run follow-up planning using the fictional Outreach Log state above. Assume no reply has arrived. Recommend whether follow-up 1 is appropriate. Prepare internal follow-up text only if the hard gate passes. Do not send, create a Gmail draft, schedule, or write externally.
```

Also test blocked follow-up conditions by re-running follow-up planning after each inbox triage result from Step 9.

### Expected result

When no reply exists and the hard gate passes:

- Follow-up cadence recommendation.
- Timing rationale.
- Stop conditions checked.
- Subject options.
- Follow-up draft if appropriate.
- Approval required before external action.
- `booking-state.md` updates required.

When a blocked reply exists:

- `Not Ready For Follow-up` report or stopped/paused recommendation.
- Clear stop reason.
- No follow-up draft when rejection, DNC, bounce, closed lineup, or other stop condition applies.

### Pass criteria

- No more than allowed cadence.
- No follow-up after rejection, DNC, bounce, closed lineup, or stop conditions.
- No exact send action happens.
- No Gmail draft is created.
- No calendar reminder is created.
- Follow-up text is internal only and approval-gated.

## Final Checklist

- [ ] `booking-state.md` updated or update recommendations produced?
- [ ] Source hygiene preserved?
- [ ] Limited pre-fit blocked score?
- [ ] Full fit scored only when ready?
- [ ] Contact verified before outreach?
- [ ] Draft not sent?
- [ ] Approval gate triggered before external action?
- [ ] Inbox triage blocks inappropriate follow-up?
- [ ] Follow-up cadence respects stop conditions?

## Expected Test Outcome

CircuitScout should prove it can support the full internal markdown workflow without any connectors or external actions. The complete-enough opportunity should travel from intake to discovery, fit classification, contact verification, internal drafting, and approval gating. The incomplete lead should stop at Limited Pre-Fit Review. Inbox triage and follow-up planning should prevent inappropriate replies or follow-ups when the fictional reply state makes outreach unsafe, closed, bounced, or approval-gated.
