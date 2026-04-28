# Limited Pre-Fit Manual Lead Example

## Purpose

This fixture shows the safe behavior when a user provides a narrow manual lead, but the artist profile is not ready for full fit scoring.

The lead is fictional, user-provided, and example-only. No live research, contact verification, outreach drafting, external automation, or external writes happen here.

## User Input

User-provided manual lead:

```text
Example-only lead for a possible small electronic event called "Night Current: Basement Signals."
The note says it may happen in "Harbor District" at "Room 41."
It looks like a late-night club room or collective showcase, but I only have a post-like note.
Scene clues visible in the note: electro, mutant bass, dub pressure, hardware live set.
Visible names: Sol Venn, Kira Hal, Other Index.
Promoter/collective text visible: Night Current.
Placeholder source note: hxxps://example.invalid/night-current-basement-signals
```

Incomplete artist profile context:

```text
Artist/project name: North Relay
Source label: user-provided example-only context
Basic sound/scene context: incomplete
Target markets: Unknown
Booking goals: Missing
EPK assets: Missing
Safe-to-use claims: Not reviewed
Comparable artists: Unknown
Availability, fees, travel constraints: Unknown
```

## Discovery Output

`skills/opportunity-discovery/SKILL.md` may accept this as a limited manual lead because the user provided enough narrow opportunity context to create one candidate record.

It must not treat the candidate as ready for full scoring, contact verification, outreach drafting, or outreach readiness.

| Field | Example output |
| --- | --- |
| Discovery ID | DSC-LPF-001 |
| Candidate opportunity ID | OPP-LPF-001 |
| Name | Night Current: Basement Signals |
| Opportunity type | recurring party / collective showcase candidate |
| Event / series / organization relationship | Event appears connected to Night Current; relationship unverified |
| City / country | Unknown; user note only says Harbor District |
| Date / edition if known | Unknown |
| Source links | User-provided placeholder note: `hxxps://example.invalid/night-current-basement-signals` |
| Source type | user-provided lead; flyer/post-like note; unknown/unverified |
| Evidence summary | User provided a fictional post-like note with event name, venue-like text, scene clues, visible artist names, and promoter/collective text. |
| Extracted lineup / artists | Sol Venn; Kira Hal; Other Index |
| Venue | Room 41 |
| Promoter / collective | Night Current |
| Genre / scene clues | Electro; mutant bass; dub pressure; hardware live set |
| Market / scene relevance | Cannot assess beyond surface scene clues because target markets and artist positioning are incomplete. |
| Confirmed facts | The user provided the note and marked it example-only. The note text includes the event name, Room 41, Night Current, visible artist names, and scene clues. |
| Assumptions | The lead may describe a small club room or collective showcase. |
| Unknowns | Official source; real city/country; exact date; event status; venue identity; booking decision maker; contact route; submission policy; capacity; fee context; artist target market fit. |
| Duplicate check result | No duplicate found in this example state; check actual `booking-state.md` before adding in a real workflow. |
| Initial priority guess | Unknown |
| Candidate status | Needs source verification; limited manual lead only |
| Risk notes | Manual source is unverified, artist context is incomplete, and the candidate cannot advance to scoring or contact work yet. |
| Recommended next skill | `skills/artist-profile/SKILL.md` or `skills/booking-state/SKILL.md` |
| `booking-state.md` updates required | Add a limited candidate row, mark fit readiness as `Limited pre-fit`, record missing artist context, add open questions, and hand off to artist-profile or booking-state normalization before full scoring. |

## Limited Pre-Fit Output

`skills/fit-classification/SKILL.md` must produce a limited pre-fit review only.

It must not produce a final numeric score, assign `A`, `B`, `C`, `D`, or `Reject`, or route to `skills/contact-verification/SKILL.md`.

```markdown
## Limited Pre-Fit Review: Night Current: Basement Signals

- Opportunity ID: OPP-LPF-001
- What can be assessed:
  - The lead is narrow enough to preserve as a candidate.
  - The note has surface scene clues that may be relevant to electronic booking research.
  - The source evidence is user-provided and unverified.
- What cannot be assessed yet:
  - Sonic fit beyond surface keywords.
  - Scene/culture fit against North Relay.
  - Artist level fit, audience fit, geography/logistics, timing, strategic value, or contact quality.
  - Any final score or A/B/C/D/Reject classification.
- Evidence available:
  - User-provided example-only note.
  - Placeholder source: hxxps://example.invalid/night-current-basement-signals.
  - Visible text naming Night Current, Room 41, Sol Venn, Kira Hal, Other Index, and scene clues.
- Missing artist context:
  - Complete sound/scene positioning.
  - Target markets and booking goals.
  - EPK assets and safe-to-use claims.
  - Comparable artists or level indicators.
  - Availability, travel, fee, and constraint context.
- Missing opportunity evidence:
  - Official source.
  - City/country.
  - Exact date or edition.
  - Venue identity.
  - Booking owner or submission route.
  - Capacity, audience, lineup status, and whether submissions are open.
- Assumptions/unknowns:
  - The lead may be a small club room or collective showcase.
  - Night Current may be the promoter or event series.
  - All opportunity facts remain unverified unless explicitly confirmed by the user or a later approved source-verification slice.
- Risk notes:
  - Do not infer contact details, booking readiness, official affiliation, or artist fit from the note alone.
  - Do not use the placeholder source externally.
- Recommended next internal skill: `skills/artist-profile/SKILL.md`, then `skills/booking-state/SKILL.md`
- `booking-state.md` updates required:
  - Store OPP-LPF-001 as `Limited pre-fit`.
  - Leave fit score blank or `N/A`.
  - Leave fit classification as `Limited Pre-Fit Review`.
  - Add open questions for artist profile readiness and opportunity evidence.
  - Add a handoff back to artist-profile or booking-state normalization.
```

## booking-state Sample Updates

### Opportunity Pipeline

| Discovery ID | Opportunity ID | Name | Type | Event / series / organization relationship | City | Country | Date / edition | Source links | Source type | Evidence summary | Extracted lineup / artists | Venue | Promoter / collective | Genre / scene clues | Duplicate check result | Candidate status | Initial priority guess | Status | Priority | Fit score | Fit classification | Score breakdown | Confirmed facts | Assumptions | Unknowns | Red flags | Next action | Contact research next | Recommended next skill | Owner | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| DSC-LPF-001 | OPP-LPF-001 | Night Current: Basement Signals | recurring party / collective showcase candidate | Event appears connected to Night Current; relationship unverified | Unknown | Unknown | Unknown | User-provided placeholder note: `hxxps://example.invalid/night-current-basement-signals` | user-provided lead; flyer/post-like note; unknown/unverified | Fictional user-provided note includes event name, venue-like text, scene clues, visible artist names, and promoter/collective text. | Sol Venn; Kira Hal; Other Index | Room 41 | Night Current | Electro; mutant bass; dub pressure; hardware live set | No duplicate found in local example state | Needs source verification; limited manual lead only | Unknown | Internal state only; Limited pre-fit | Unknown | N/A | Limited Pre-Fit Review | Not scored; readiness guard blocked full scoring | User provided example-only visible text and incomplete artist profile context | Possible small club room or collective showcase | Complete artist profile; official source; city/country; exact date; booking owner; contact route; capacity; submission policy | Unverified source; incomplete artist profile; no official evidence; no contact route | Complete artist profile and transfer/normalize missing fields in booking-state before full fit scoring | Do not start contact research yet | `skills/artist-profile/SKILL.md`; then `skills/booking-state/SKILL.md` | Codex/OpenAI workflow | Limited pre-fit fixture; no external action |

### Open Questions

| Question ID | Question | Needed for | Owner | Status | Answer/source | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Q-LPF-001 | What is North Relay's complete sound/scene positioning? | Full fit classification | User | Open | Unknown | Required before a 100-point score. |
| Q-LPF-002 | What target markets and booking goals should this opportunity be compared against? | Full fit classification | User | Open | Unknown | Cannot assess geography or strategy without this. |
| Q-LPF-003 | Which artist claims and EPK assets are safe to use internally or externally? | Profile readiness and outreach safety | User | Open | Unknown | Keep missing claims as missing; do not invent proof. |
| Q-LPF-004 | Is there an official source for Night Current: Basement Signals? | Opportunity evidence | User or future approved research workflow | Open | Unknown | Placeholder source is not enough for verification. |
| Q-LPF-005 | What city/country, exact date, venue identity, and booking owner apply to this lead? | Opportunity evidence and future contact verification | User or future approved research workflow | Open | Unknown | Contact verification remains blocked. |

### Risk Register

| Risk ID | Area | Risk | Severity | Status | Mitigation / next action | Owner | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| R-LPF-001 | Fit readiness | Full scoring would require invented artist context and unverified opportunity evidence. | Medium | Open | Keep as `Limited pre-fit`; complete artist-profile and booking-state normalization first. | Codex/OpenAI workflow | Blocks score, classification band, and contact handoff. |

### Handoff Chain

| Handoff ID | Date | From | To | Workflow stage | Summary | Pending approvals | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HND-LPF-001 | Example-only; not dated | User manual intake | `skills/opportunity-discovery/SKILL.md` | Intake to discovery | User supplied a fictional, narrow manual lead and incomplete artist profile context. | None; internal analysis only | Normalize candidate fields and limitations. |
| HND-LPF-002 | Example-only; not dated | `skills/opportunity-discovery/SKILL.md` | `skills/fit-classification/SKILL.md` | Limited discovery to pre-fit review | Candidate OPP-LPF-001 can be preserved, but artist context and source evidence are incomplete. | None; internal analysis only | Produce limited pre-fit only; do not score. |
| HND-LPF-003 | Example-only; not dated | `skills/fit-classification/SKILL.md` | `skills/artist-profile/SKILL.md` | Pre-fit paused for profile readiness | Readiness guard blocked the 100-point score and classification band. | None; no external action proposed | Complete artist context, then normalize into `booking-state.md`. |

## What Happens Next

1. Complete or update the artist profile using `skills/artist-profile/SKILL.md`.
2. Transfer confirmed, user-provided, missing, and unknown fields into canonical state using `skills/booking-state/SKILL.md`.
3. Re-run `skills/fit-classification/SKILL.md` only after readiness is sufficient.
4. Keep contact verification blocked until the opportunity has enough evidence and fit classification explicitly routes there.

No approval request is needed yet because no external-facing action is proposed.

## What Must Not Happen

- Do not produce a final numeric score.
- Do not classify the opportunity as `A`, `B`, `C`, `D`, or `Reject`.
- Do not route to contact verification.
- Do not draft outreach.
- Do not create Gmail drafts.
- Do not send, forward, reply, schedule, label, archive, or contact anyone.
- Do not write to Calendar, Sheets, CRM, APIs, external systems, or external spreadsheets.
- Do not scrape, use OCR, automate a browser, perform live web research, or use connectors.
- Do not invent real artist credentials, links, releases, press, streaming numbers, bookings, fees, dates, labels, affiliations, contacts, audience metrics, lineups, or capacities.
- Do not treat placeholder domains or fictional notes as real evidence.
