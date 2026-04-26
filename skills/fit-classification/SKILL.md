---
name: fit-classification
description: Score and classify CircuitScout booking opportunities for electronic music artists before contact research or outreach drafting.
---

# Fit Classification

CircuitScout uses fit classification to decide whether a club, party, promoter, collective, showcase, radio show, or festival is a good booking opportunity for an electronic music artist.

Core question: does this opportunity make artistic, cultural, logistical, strategic, and timing sense for this artist right now?

This is an internal scoring and recommendation workflow. It does not require human approval by itself. Any recommended external-facing or consequential next action must route through `skills/approval-before-action/SKILL.md` before execution.

Do not implement OCR, scraping, APIs, Gmail, Calendar, Sheets, automation, contact verification, or outreach writing inside this skill. Use available user-provided evidence, local state, and explicitly requested research outputs only. Mark missing information as `Unknown`.

## When To Use

Use this skill before contact research, outreach drafting, follow-up planning, or pipeline prioritization when CircuitScout needs to qualify an opportunity.

Use it for:

- Clubs, venues, event series, parties, raves, collectives, promoters, showcases, radio shows, festivals, labels, or cultural programs.
- A single opportunity or a list of opportunities.
- Opportunities discovered from flyers, posters, Instagram posts, RA listings, club listings, lineup announcements, recommendations, user notes, or previous booking-state records.
- Reclassifying an opportunity when new lineup, timing, contact, safety, artist-profile, or source evidence appears.

Read `booking-state.md` first when it exists, especially `Artist Profile`, `Positioning / Sound / Scene Fit`, `EPK Assets`, `Target Markets`, `Booking Goals`, `Opportunity Pipeline`, `Risk Register`, and `Do-not-contact List`.

## Scoring Model

Score each opportunity out of 100 points:

| Category | Points |
| --- | ---: |
| Sonic / genre fit | 25 |
| Scene / culture fit | 20 |
| Artist level fit | 15 |
| Audience fit | 10 |
| Timing / booking window | 10 |
| Geography / logistics | 10 |
| Contact quality | 5 |
| Strategic value | 5 |

Use integers or half-points. If evidence is missing, score conservatively and explain the unknown. Do not fill gaps with invented facts.

## Classification Bands

| Score | Classification |
| --- | --- |
| 85-100 | A / High priority |
| 70-84 | B / Worth pitching |
| 55-69 | C / Monitor or pitch later |
| 40-54 | D / Weak fit |
| 0-39 | Reject |

Classification can be capped or overridden by the rules below. Keep both the numeric score and final classification visible.

## Evaluation Criteria

### Sonic / Genre Fit: 25

Evaluate how naturally the artist's sound belongs with the opportunity.

Consider:

- Genres and subgenres.
- BPM range, energy curve, intensity, and dancefloor function.
- Underground vs commercial alignment.
- Experimental vs accessible positioning.
- Similarity to past, current, or announced lineups.
- Compatibility with the artist's releases, mixes, DJ sets, live set, labels, sonic references, and stated booking goals.

Strong evidence includes recurring lineup overlap, shared labels or scenes, compatible set contexts, and event descriptions that match the artist's actual sound. Weak evidence includes only a broad genre tag, a visual mood match, or a single artist name that is not representative of the event.

### Scene / Culture Fit: 20

Evaluate whether the artist naturally belongs in the opportunity's ecosystem.

Consider:

- Event aesthetic, community, language, values, and recurring themes.
- Visual and copy signals from event posts, listings, websites, and venue materials.
- Underground, queer, rave, club, festival, art, experimental, bass, techno, electro, house, ambient, or hybrid scene context when relevant.
- Whether the artist's positioning feels credible and respectful in that scene.
- Whether the opportunity is a natural cultural fit, a plausible adjacent fit, or a surface-level mismatch.

Do not over-weight aesthetic similarity. If the flyer looks right but the lineup, venue, audience, or copy suggests a different scene, note the contradiction and score based on stronger evidence.

### Artist Level Fit: 15

Evaluate whether the opportunity is realistic for the artist right now.

Consider:

- Venue, festival, radio, or event scale.
- Lineup level and billing patterns.
- Whether the opportunity books emerging artists, local artists, residents, breakthrough names, established touring artists, or headliners.
- The artist's proof, assets, releases, press, booking history, audience, and local relevance.
- Whether the target should be an immediate pitch, long-term target, or monitor item.

If the opportunity is aspirational but unrealistic now, classify it as `Long-term target` rather than immediate pitch, even if the cultural fit is strong.

### Audience Fit: 10

Evaluate whether the likely audience would understand and respond to the artist.

Consider:

- Expected crowd, listening context, and event format.
- Dancefloor compatibility or seated/listening compatibility.
- Local scene compatibility.
- Whether the artist's sound asks too much, too little, or the right amount from that audience.
- Whether similar artists have worked in the same room, series, or market.

### Timing / Booking Window: 10

Evaluate whether the opportunity is open and timely.

Consider:

- Event date or edition timing.
- Announcement stage.
- Whether the lineup appears open, closing, announced, or likely closed.
- Whether booking lead times make a pitch realistic.
- Whether the opportunity should be pitched now or monitored for the next edition.

If the lineup is likely closed, classify as `Monitor for next edition` even when the score is otherwise strong.

### Geography / Logistics: 10

Evaluate whether the location makes sense.

Consider:

- City and country.
- Travel feasibility from the artist's base or existing route.
- Cost vs opportunity value.
- Calendar fit and likely travel time.
- Possibility of combining with nearby dates, target markets, or route-building.
- Visa, distance, and hospitality unknowns when relevant.

### Contact Quality: 5

Evaluate only the quality of the visible or known contact route. Do not invent contacts.

Score examples:

- 5: Official booking email, official form, or verified promoter/venue booking route.
- 3-4: Public business contact that plausibly reaches the right organization but is not clearly booking-specific.
- 1-2: Uncertain contact, generic social route, or secondhand contact requiring verification.
- 0: No verified contact route.

If there is no verified contact route, the opportunity cannot be higher than `B / Worth pitching`. Strong scene fit with no contact route should go to future contact verification instead of outreach.

### Strategic Value: 5

Evaluate upside beyond the single booking.

Consider:

- Credibility for the artist's target scene.
- Network access to promoters, venues, labels, radio hosts, collectives, or festivals.
- Documentation potential.
- Future routing value.
- Relationship value.
- Connection to target markets, scenes, or long-term booking goals.

## Flyer And Lineup Analysis

When flyers, posters, Instagram announcements, RA listings, club listings, lineup images, or event posts are available, use them as evidence without pretending to perform unsupported OCR or scraping.

Method:

1. Extract visible artist names, event names, dates, venues, cities, promoters, collectives, labels, sponsors, and partners from the provided source.
2. Treat unclear or cropped text as `Unclear` or `Unknown` instead of guessing.
3. Research or request research on listed artists when needed to understand genre, scene, level, labels, previous bookings, audience, and positioning.
4. Use lineup context as evidence for sonic fit, scene/culture fit, artist level fit, audience fit, credibility, and timing.
5. Compare the target artist against the event's existing or past lineup.
6. Distinguish confirmed flyer text from inferred conclusions.
7. Preserve image and source links where possible.
8. Avoid over-weighting visual aesthetics if sonic or lineup evidence contradicts it.
9. Flag when flyer aesthetics suggest one scene but the lineup suggests another.

Recommended evidence labels:

- `Confirmed from source`: visible text or directly sourced facts.
- `Inferred`: reasoned conclusion from lineup, venue, copy, or artist context.
- `Unknown`: missing or unreadable information.
- `Needs research`: information that should be researched later before outreach.

## Risk And Red Flags

Identify red flags separately from the score. Serious risk can cap or override the classification.

Watch for:

- Pay-to-play suspicion.
- Unclear promoter, fake event signals, suspicious contact routes, or impersonation risk.
- Bad reputation, unsafe, exploitative, discriminatory, or predatory context.
- Poor fit despite surface-level genre match.
- Spammy outreach risk, especially when there is no official contact route.
- Misleading lineup claims, recycled flyers, impossible dates, or inconsistent location details.
- Conflicts with do-not-contact entries, user preferences, artist values, or booking constraints.

## Override Rules

Apply these after scoring:

- If there is no verified contact route, final classification cannot be higher than `B / Worth pitching`.
- If the lineup is likely closed, classify as `Monitor for next edition`.
- If serious reputation, scam, safety, exploitative, or pay-to-play concerns exist, classify as `Reject` or `D / Weak fit` regardless of score.
- If key information is missing, mark it as `Unknown`; do not invent it.
- If the opportunity is aspirational but unrealistic now, classify as `Long-term target`, not immediate pitch.
- If the opportunity is strong scene fit but bad timing, classify as `Monitor`.
- If the opportunity is good but the artist lacks required assets, classify as `Not ready` and list missing assets.
- If the opportunity is only a surface-level genre match but weak scene/culture fit, cap it at `C / Monitor or pitch later`.
- If the opportunity has strong scene fit but no contact route, recommend future contact verification instead of outreach.

## Output Format

Use this structure for each opportunity:

```markdown
## Fit Classification: [Opportunity name]

- Opportunity name:
- Opportunity type:
- City / country:
- Source links:
- Flyer / lineup evidence if available:

### Confirmed Facts

- 

### Assumptions

- 

### Unknowns

- 

### Missing Info

- 

### Score Breakdown

| Category | Max | Score | Evidence / rationale |
| --- | ---: | ---: | --- |
| Sonic / genre fit | 25 |  |  |
| Scene / culture fit | 20 |  |  |
| Artist level fit | 15 |  |  |
| Audience fit | 10 |  |  |
| Timing / booking window | 10 |  |  |
| Geography / logistics | 10 |  |  |
| Contact quality | 5 |  |  |
| Strategic value | 5 |  |  |

- Final score:
- Classification:
- Override rules applied:
- Red flags:
- Recommended next action:
- Contact research should happen next:
- Should enter pipeline:
- `booking-state.md` updates required:
```

## Recommended Next Actions

Use one of these action labels when possible:

- `Research missing fit evidence`.
- `Run contact verification`.
- `Route to future outreach drafting`.
- `Monitor next edition`.
- `Long-term target`.
- `Not ready: complete missing assets`.
- `Reject / do not pursue`.
- `Ask user for artist preference or constraint`.

This skill does not write outreach. If a later workflow routes a classified opportunity to outreach drafting, creating Gmail drafts, sending messages, contacting anyone, modifying external systems, or making consequential status changes requires `skills/approval-before-action/SKILL.md`.

## Booking-State Integration

When updating `booking-state.md`, store fit evidence in `Opportunity Pipeline` or a linked note:

- Fit score.
- Fit classification.
- Score breakdown.
- Confirmed facts.
- Assumptions.
- Unknowns.
- Red flags.
- Source links.
- Recommended next action.
- Whether contact research should happen next.

If the classification creates or changes a consequential decision, add a `Decision Log` entry. If it identifies risk that may affect future work, add or update `Risk Register`. If the next step is external-facing or consequential, create an approval-gated proposal through `skills/approval-before-action/SKILL.md`.
