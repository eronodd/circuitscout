---
name: opportunity-discovery
description: Discover, normalize, and record source-backed CircuitScout booking opportunity candidates before fit classification.
---

# Opportunity Discovery

CircuitScout uses opportunity discovery to turn user-provided leads, scene notes, source lists, flyers, lineup text, or manually gathered research notes into safe candidate opportunity records.

Core question: what clubs, parties, festivals, promoters, collectives, showcases, radio shows, label nights, agencies, or event series may be worth evaluating for this artist, and what evidence supports adding them to the pipeline?

This is an internal discovery and state-preparation workflow. It does not require human approval by itself. Any external-facing next action recommended from discovery must route through `skills/approval-before-action/SKILL.md` before execution.

Do not implement Gmail, Calendar, Sheets, APIs, scraping, OCR, browser automation, external automation, actual web research, contact verification, fit scoring, outreach writing, sending, forwarding, replying, scheduling, labeling, archiving, or external CRM/spreadsheet writes inside this skill. Use only user-provided sources, local booking state, and explicitly provided research notes. Mark missing information as `Unknown`.

## When To Use

Use this skill before `skills/fit-classification/SKILL.md` when CircuitScout needs to discover or normalize candidate booking opportunities.

Use it for:

- Manual lead intake from a link, flyer, name, post, email, event, club, festival, promoter, screenshot, or user note.
- Scene mapping across relevant cities, scenes, clubs, parties, collectives, promoters, radio shows, labels, showcases, festivals, or agencies to investigate later.
- Similar-artist route mapping that uses comparable artists as clues for possible venues, festivals, promoters, radio shows, or event series.
- Flyer, poster, screenshot, or lineup-text extraction from user-provided material.
- Source-list review from RA listings, club websites, festival pages, newsletters, Instagram, SoundCloud descriptions, Bandcamp pages, label pages, or personal notes supplied by the user.

Read `booking-state.md` first when it exists, especially:

- `Artist Profile`
- `Positioning / Sound / Scene Fit`
- `Target Markets`
- `Booking Goals`
- `Opportunity Pipeline`
- `Contact Register`
- `Risk Register`
- `Do-not-contact List`
- `Open Questions`

## Required Inputs

Use whatever reliable inputs are available, but do not invent missing data:

- Artist profile from `booking-state.md`.
- Positioning, sound, and scene-fit notes.
- Target markets.
- Booking goals.
- Existing opportunity pipeline.
- Existing contact register when relevant for duplicate checks.
- User-provided leads, links, flyers, screenshots, names, Instagram posts, RA listings, venue pages, festival pages, newsletters, or notes.
- User-provided constraints such as city, country, style, date range, scene, budget, availability, or priority market.

If the lead is too vague to identify a candidate, ask for the minimum missing detail or mark the candidate as `Too vague`.

## Discovery Modes

### Manual Lead Intake

Use when the user provides a link, flyer, name, post, email, event, club, festival, promoter, or screenshot.

Extract structured candidate data from the provided material. Mark missing fields as `Unknown`. Treat user-provided notes as source evidence, but do not treat user assumptions as confirmed facts unless the user explicitly confirms them.

### Scene Mapping

Use when the user wants a map of relevant scenes, cities, clubs, parties, collectives, promoters, radio shows, labels, showcases, or festivals to investigate.

Create candidate records only for items supported by user-provided source evidence or user-provided notes. If the output is only an investigation map, mark candidates as `Needs source verification` unless source evidence is already present.

### Similar-Artist Route Mapping

Use similar artists as clues for possible opportunities.

Distinguish confirmed past bookings, visible lineup evidence, label/radio associations, and user-provided comparisons from assumptions. Do not invent lineups, past support slots, routing history, relationships, or promoter connections. If similar-artist evidence is plausible but unverified, use source type `similar-artist evidence` and candidate status `Needs source verification`.

### Flyer / Lineup Lead Extraction

Use when the user provides flyers, posters, screenshots, or lineup text.

Extract only visible or provided text: artist names, event titles, dates, venues, cities, promoters, collectives, labels, partners, sponsors, and source links. Treat unclear, cropped, stylized, or low-confidence text as `Unclear` or `Unknown`. Send extracted lineup context forward to `skills/fit-classification/SKILL.md`; do not score final fit here.

### Source-List Review

Use when the user provides lists from RA, club websites, festival pages, newsletters, Instagram, SoundCloud descriptions, Bandcamp pages, label pages, or personal notes.

Normalize the supplied list into candidate records. Preserve every source link. Do not scrape, automate collection, expand the list externally, or treat unsupported list entries as confirmed facts.

## Opportunity Types

Use one of these opportunity types:

- `club`
- `recurring party`
- `festival`
- `showcase`
- `promoter`
- `collective`
- `radio show`
- `podcast/mix series`
- `label night`
- `art/music institution`
- `agency/booker`
- `support slot`
- `residency`
- `community event`
- `other / unknown`

## Source Types

Use one or more source types:

- `official website`
- `official event listing`
- `official social post`
- `flyer/poster`
- `user-provided lead`
- `newsletter`
- `ticketing page`
- `RA listing`
- `club listing`
- `festival listing`
- `similar-artist evidence`
- `public article/interview`
- `unknown/unverified`

## Candidate Status Values

Use one status per candidate:

- `New candidate`
- `Needs source verification`
- `Ready for fit classification`
- `Duplicate candidate`
- `Out of scope`
- `Too vague`
- `Archived`

Use `Ready for fit classification` only when there is enough source-backed identity, type, location or context, and evidence for `skills/fit-classification/SKILL.md` to evaluate the opportunity. Use `Needs source verification` when the candidate is plausible but the source is weak, indirect, old, unclear, or incomplete.

## Initial Priority Guess

Use discovery-level priority only:

- `High potential`
- `Medium potential`
- `Low potential`
- `Unknown`
- `Out of scope`

This is not a fit score. Do not assign a numeric score, final classification, or outreach recommendation. Full scoring belongs in `skills/fit-classification/SKILL.md`.

## Duplicate Detection

Before creating a new candidate, check `Opportunity Pipeline` and `Contact Register` for likely duplicates by:

- Name.
- Event series.
- Venue.
- Promoter or collective.
- City.
- Source link.
- Date or edition.
- Obvious alias.

If a duplicate is likely:

- Do not create a new candidate.
- Mark candidate status `Duplicate candidate`.
- Recommend updating the existing record with the new evidence.
- Identify the likely existing opportunity ID or contact ID when known.

If the match is uncertain, keep the candidate separate but record the duplicate concern under `Duplicate check result`.

## Evidence Rules

- Preserve all source links.
- Separate confirmed facts from assumptions.
- Mark unknowns as `Unknown`.
- Do not invent opportunities, dates, lineups, contacts, capacities, fees, locations, source evidence, prior relationships, or artist credentials.
- Do not treat a source as official unless it appears to be controlled by the relevant venue, event, promoter, festival, collective, label, radio show, agency, or ticketing/listing platform.
- Treat user-provided notes as useful context, but label them as `user-provided` unless supported by another source.
- Treat suspicious, exploitative, fake, spammy, pay-to-play, impersonation, unsafe, or inconsistent leads as risk items before fit classification.
- If source evidence is too thin, ask for the minimum missing detail or mark `Too vague`.
- If a lead is outside the artist's stated constraints or booking goals, mark `Out of scope` rather than forcing it into fit classification.

## Hard Boundaries

- Do not score final fit here.
- Do not verify contacts here.
- Do not draft outreach here.
- Do not send, reply, forward, schedule, label, archive, contact anyone, or write externally.
- Do not create Gmail drafts, calendar events, sheets, CRM entries, or external records.
- Do not scrape, browse, automate collection, perform OCR, call APIs, or perform actual web research.
- Do not use inferred contact routes, guessed emails, private contact details, or unsupported relationship claims.
- Do not route to outreach drafting before fit classification and contact verification are complete.

## Output Format

Use this structure for each discovered candidate:

```markdown
## Opportunity Discovery: DSC-###

- Discovery ID:
- Candidate opportunity ID:
- Name:
- Opportunity type:
- Event / series / organization relationship:
- City / country:
- Date / edition if known:
- Source links:
- Source type:
- Evidence summary:
- Extracted lineup / artists:
- Venue:
- Promoter / collective:
- Genre / scene clues:
- Market / scene relevance:

### Confirmed Facts

-

### Assumptions

-

### Unknowns

-

### Duplicate Check Result

-

### Initial Priority Guess

-

### Candidate Status

-

### Risk Notes

-

### Recommended Next Skill

-

### booking-state.md Updates Required

-
```

For `Recommended Next Skill`, use one of:

- `skills/fit-classification/SKILL.md` when the candidate is ready to evaluate.
- `skills/opportunity-discovery/SKILL.md` when more user-provided source evidence or lead cleanup is needed.
- `skills/contact-verification/SKILL.md` only after fit classification has already accepted the opportunity or the user specifically asks to verify an existing contact route.
- `skills/approval-before-action/SKILL.md` when the next proposed action is external-facing or consequential.

## Booking-State Integration

Use `skills/booking-state/SKILL.md` when updating `booking-state.md`.

Store discovery results in `Opportunity Pipeline` or a linked note. Entries should support:

- Discovery ID.
- Opportunity candidate ID.
- Name.
- Opportunity type.
- Event / series / organization relationship.
- City and country.
- Date or edition if known.
- Source links.
- Source type.
- Evidence summary.
- Extracted lineup / artists.
- Venue.
- Promoter / collective.
- Genre / scene clues.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Duplicate check result.
- Initial priority guess.
- Candidate status.
- Risk notes.
- Recommended next skill.

Add open questions for vague leads, missing source links, unclear dates/locations, uncertain source ownership, unresolved duplicate checks, or missing evidence needed before fit classification.

If risk appears suspicious, unsafe, exploitative, spammy, fake, or pay-to-play, add or update `Risk Register` and recommend risk review before fit classification.

Do not update `Contact Register` except to note that an existing contact or organization may be a duplicate reference. Contact route evaluation belongs in `skills/contact-verification/SKILL.md`.

## Integration With Other CircuitScout Skills

- Use `skills/using-circuitscout/SKILL.md` to route discovery before fit classification in the normal workflow.
- Use `skills/booking-state/SKILL.md` to read existing artist context, target markets, pipeline records, contact records, open questions, and risks before creating candidate records.
- Use `skills/fit-classification/SKILL.md` after discovery when a candidate is source-backed enough to evaluate fit.
- Use `skills/contact-verification/SKILL.md` only after fit classification or when checking an already known contact route for a selected opportunity.
- Use `skills/outreach-drafting/SKILL.md` only after fit classification and contact verification have cleared their gates.
- Use `skills/followup-planning/SKILL.md` only after real outreach exists; discovery alone never creates follow-up tasks.
- Use `skills/inbox-triage/SKILL.md` when a user-provided inbound reply or message changes opportunity evidence or reveals a new lead.
- Use `skills/approval-before-action/SKILL.md` before any external-facing or consequential action recommended from discovery.

## Safety Checklist

Before finalizing discovery, verify:

- The candidate is based on user-provided material, local booking state, or explicitly provided research notes.
- No web research, scraping, OCR, browser automation, API calls, Gmail, Calendar, Sheets, sending, replying, forwarding, scheduling, labeling, archiving, or external writes were performed.
- Confirmed facts, assumptions, and unknowns are separated.
- Source links and source types are preserved.
- Duplicate check has been performed against `Opportunity Pipeline` and `Contact Register`.
- Initial priority is lightweight and not a final fit score.
- The recommended next step is fit classification unless the lead is too vague, duplicate, out of scope, unsafe, or still needs source verification.
- Any external-facing or consequential next action routes through `skills/approval-before-action/SKILL.md`.
