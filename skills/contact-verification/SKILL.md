---
name: contact-verification
description: Verify safe, official, source-backed contact routes for CircuitScout booking opportunities after fit classification and before outreach drafting.
---

# Contact Verification

CircuitScout uses contact verification to identify the safest, most official, most relevant contact route for a booking opportunity and to decide whether outreach can safely be drafted next.

Core question: what is the safest, most official, most relevant contact route for this opportunity, and how confident are we?

This is an internal verification workflow. It does not require human approval by itself. Any external-facing next action, including social DM, email, contact form submission, Gmail draft creation if connected later, CRM/spreadsheet write, or outreach send, must route through `skills/approval-before-action/SKILL.md`.

Do not implement Gmail, Calendar, Sheets, APIs, scraping, OCR, automation, or outreach writing inside this skill. Use available user-provided evidence, local state, and explicitly requested research outputs only. Mark missing information as `Unknown`.

## When To Use

Use this skill after `skills/fit-classification/SKILL.md` and before outreach drafting when CircuitScout needs to validate a contact route for:

- Clubs, venues, parties, promoters, collectives, showcases, radio shows, festivals, labels, label nights, event series, or agencies.
- A specific opportunity already in `booking-state.md`.
- A contact route found in user notes, official websites, social profiles, event listings, flyers, prior state, or manual research output.
- Duplicate, conflicting, stale, suspicious, or unclear contact candidates.
- A question about whether outreach should be paused because no verified route exists.

Read `booking-state.md` first when it exists, especially `Opportunity Pipeline`, `Contact Register`, `Risk Register`, and `Do-not-contact List`.

## Contact Route Hierarchy

Prefer contact routes in this order:

1. Official booking/contact email from the event, venue, promoter, festival, or collective website.
2. Official contact form on the official website.
3. Official public business email listed on verified social profiles.
4. Publicly listed promoter/booker contact specifically associated with bookings.
5. Public Instagram/social DM route from the official account.
6. Generic info email only if no better route exists.
7. Unknown / needs manual research.

Use the highest safe route that matches the specific opportunity. Do not upgrade a route just because it is convenient.

## Contact Route Types

Use one of these route types:

- `official booking email`
- `official contact form`
- `official general email`
- `promoter/business email`
- `agency/booker email`
- `official social DM`
- `manual research needed`
- `do not use`

## Confidence Levels

Use one confidence level per contact candidate:

- `Verified`: official source confirms the contact route and its relevance.
- `Likely`: public source suggests relevance, but the route is not fully confirmed.
- `Uncertain`: contact may be related, but role, currentness, ownership, or relevance is unclear.
- `Do not use`: contact is private, guessed, suspicious, outdated, unsafe, conflicts with do-not-contact, or should not be used.
- `Unknown`: no usable route found yet.

If confidence is below `Likely`, do not recommend outreach yet. Recommend more research, clarification, or pausing the opportunity.

## Verification Criteria

### Official Source Quality

Evaluate whether the source is controlled by the relevant entity:

- Strong: official event, venue, festival, collective, promoter, agency, or label website; official contact page; official profile linked from the website.
- Moderate: verified or clearly official social profile; event platform listing controlled by the organizer; public business directory linked from official materials.
- Weak: third-party list, old article, scraped directory, reposted flyer, fan page, personal profile, unverified database, or unsourced note.
- Unsafe: leaked contact, guessed address, private personal detail, suspicious domain, impersonation signal, or source that conflicts with do-not-contact.

Preserve the source link for every candidate.

### Purpose And Role Fit

Identify what the contact route is for:

- Booking.
- Artist submissions.
- General information.
- Press.
- Sponsorship.
- Ticketing.
- Venue hire.
- Private events.
- Agency representation.
- Unknown.

Booking-specific routes outrank generic routes. Do not treat press, sponsorship, ticketing, or venue-hire contacts as booking contacts unless the source explicitly says they handle bookings or artist submissions.

### Opportunity Match

Check whether the route belongs to the correct:

- Event, venue, promoter, collective, festival, label night, radio show, or agency.
- City, country, location, and edition.
- Current or upcoming edition rather than an old edition.
- Promoter or parent organization when the same promoter runs multiple events.
- Agency or external booker if the source says bookings are handled externally.

If the same promoter runs multiple events, record the relationship and do not assume the route covers every event unless the source says so.

### Currentness

Assess whether the contact is current:

- Prefer pages or profiles with recent activity, current edition links, or current contact pages.
- Treat old festival editions, old flyers, inactive profiles, dead domains, and outdated directory entries as weak or unsafe.
- If a source has no visible date, mark currentness as an assumption or unknown.

### Duplicates And Conflicts

When multiple contacts appear:

- Record each meaningful candidate separately or summarize weaker duplicates.
- Prefer the higher official-source and purpose-fit route.
- Flag conflicts such as different domains, old vs new addresses, venue vs promoter ownership, or agency vs direct booking routes.
- Do not merge two contacts unless sources clearly show they belong to the same role or organization.

### Agency Or External Booker

If an agency, external booker, resident booker, or programming partner appears involved:

- Identify who controls artist submissions or bookings.
- Record whether the agency route applies to the event, the venue, the promoter, or only a specific artist roster.
- Do not bypass an official agency/booker route with a generic venue route unless the source supports that choice.

### Safety And Pause Rules

Mark a route as `Do not use` or pause the opportunity when:

- The route conflicts with the `Do-not-contact List`.
- The contact is guessed, generated, inferred from a domain, or not publicly listed.
- The contact is private/personal and not publicly listed for booking or business.
- The source appears leaked, scraped, suspicious, impersonated, outdated, or unsafe.
- The route is for press, sponsorship, ticketing, venue hire, private hire, or general info and no booking relevance is shown.
- The contact belongs to a different event, city, edition, organization, or promoter.
- There are unresolved conflicts that could cause reputational harm.

If no `Verified` or `Likely` route exists, recommend more research rather than outreach.

## Hard Rules

- Never guess email addresses.
- Never generate guessed emails from names or domains.
- Never use private or personal emails unless publicly listed for booking or business.
- Never use leaked, scraped, or unverified personal contact details.
- Never contact a do-not-contact entry.
- Preserve source links for every contact.
- Mark unknowns as `Unknown`.
- Separate confirmed facts from assumptions.
- If contact confidence is below `Likely`, do not recommend outreach yet.
- If no verified or likely route exists, recommend more research, not outreach.
- If social DM is recommended, it still requires human approval before any message is sent.
- A proposed contact record may be prepared locally, but do not write to an external CRM/spreadsheet unless approved later.

## Output Format

Use this structure for each contact candidate:

```markdown
## Contact Verification: [Opportunity name]

- Opportunity ID:
- Opportunity name:
- Contact candidate:
- Contact route type:
- Contact value or route description:
- Role/purpose:
- Source link:
- Source type:
- Confidence level:

### Confirmed Facts

-

### Assumptions

-

### Unknowns

-

### Conflicts / Duplicates

-

### Safety Notes

-

### Do-not-contact Check

-

### Recommendation

- Recommended next action:
- Whether outreach drafting can happen next:
- `booking-state.md` updates required:
```

For `Whether outreach drafting can happen next`, use:

- `Yes, draft may be prepared for human review` only when the route is `Verified` or `Likely`, no do-not-contact conflict exists, and no unresolved safety blocker exists.
- `No, verify contact first` when confidence is `Uncertain` or `Unknown`.
- `No, do not use this route` when confidence is `Do not use`.

## Recommended Next Actions

Use one of these action labels when possible:

- `Prepare proposed contact record`.
- `Route to future outreach drafting for human review`.
- `Request manual research for official booking route`.
- `Use official contact form only after approval`.
- `Use official social DM only after approval`.
- `Pause: no verified or likely contact route`.
- `Do not use this contact`.
- `Check do-not-contact conflict with human`.

This skill does not write outreach. Outreach drafting, contact form submission, social DM, email, Gmail draft creation if connected later, CRM/spreadsheet writes, or any external-facing contact action requires `skills/approval-before-action/SKILL.md`.

## Booking-State Integration

When updating `booking-state.md`, store contact verification in `Contact Register` or a linked note:

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

If verification changes whether outreach can be drafted, update the related `Opportunity Pipeline` next action and contact research status. If verification identifies safety, impersonation, privacy, stale-source, or do-not-contact risk, add or update `Risk Register`. If the next step is external-facing or consequential, create an approval-gated proposal through `skills/approval-before-action/SKILL.md`.
