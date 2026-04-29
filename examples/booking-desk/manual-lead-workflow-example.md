# Manual Lead Workflow Example

This fixture shows how a user-provided manual lead can move through CircuitScout from intake to the next internal step. It uses a fictional lead only. The source note is provided by the user, not live researched.

## 1. User Input

User-provided source note:

```text
I saw a flyer-style post/link note for "Signal Bloom: Courtyard Frequencies" in Porto, Portugal.
Venue listed as "Atrium 9" and rough date says "late May 2026 / spring edition."
It looks like a small club night or collective event, not a large festival.
Scene clues: leftfield house, broken beat, dubby techno, ambient room, local live hardware set.
Visible lineup names on the note: Mara Vale, Jun Risco, Pale Circuit, Nia Quell.
Promoter/collective text visible: Signal Bloom.
User note only, no live research performed: hxxps://example.invalid/signal-bloom-courtyard-frequencies
```

Fictional artist context already present in local booking state:

```text
Artist/project name: Echo Radius
Project type: DJ / live hybrid
Base: Lisbon, Portugal
Sound/scene context: leftfield house, broken beat, dubby techno, textural club tools, ambient-adjacent live hardware passages
Target markets: Portugal and nearby Iberian club/collective circuits
Booking goals: small club nights, collective events, and intimate electronic rooms in spring/summer 2026
Artist level: emerging regional artist with a complete basic EPK, one live/DJ video, and a current mix link
Travel/logistics: Portugal weekend dates are plausible, but exact availability and fee constraints are unknown
Safe-to-use claims: only user-provided profile facts above; no invented press, metrics, labels, or past bookings
```

## 2. opportunity-discovery Output

| Field | Example output |
| --- | --- |
| Discovery ID | DSC-ML-001 |
| Candidate opportunity ID | OPP-ML-001 |
| Name | Signal Bloom: Courtyard Frequencies |
| Opportunity type | Club night / collective event candidate |
| City / country | Porto, Portugal |
| Date / edition if known | Late May 2026 / spring edition, exact date unknown |
| Source links or user-provided source note | User-provided flyer/link-like note: `hxxps://example.invalid/signal-bloom-courtyard-frequencies` |
| Source type | User-provided manual lead; unverified note |
| Evidence summary | User provided an event name, city, venue text, rough edition/date, visible lineup, promoter/collective text, and scene clues from a flyer-style note. No live source validation has been performed. |
| Extracted lineup/artists | Mara Vale; Jun Risco; Pale Circuit; Nia Quell |
| Venue | Atrium 9 |
| Promoter/collective | Signal Bloom |
| Genre/scene clues | Leftfield house; broken beat; dubby techno; ambient room; local live hardware set |
| Confirmed facts | The user provided the note and visible text. The note says Porto, Atrium 9, Signal Bloom, and the listed artist names. |
| Assumptions | The opportunity may be a small club night or collective event. The event may be relevant for a leftfield electronic artist. |
| Unknowns | Official event page; exact date; capacity; booking policy; whether Signal Bloom is accepting artist submissions; official contact route; whether the venue or collective owns booking decisions. |
| Duplicate check result | No duplicate found in the local example state; check actual `booking-state.md` before adding in a real workflow. |
| Initial priority guess | Medium |
| Candidate status | New candidate; needs official-source verification |
| Risk notes | Manual source is unverified. Do not infer real contact details, active booking availability, or official affiliation from the note alone. |
| Recommended next skill | `skills/fit-classification/SKILL.md` |
| `booking-state.md` updates required | Add a row to Opportunity Pipeline with candidate status, source note, extracted evidence, unknowns, and next skill. Add open questions for official source, exact date, and contact route. Add handoff from opportunity-discovery to fit-classification. |

## 3. fit-classification Output

Readiness guard result:

| Field | Example output |
| --- | --- |
| Fit readiness status | Ready for fit classification |
| Missing readiness notes | None blocking full scoring. Official source, exact date, lineup status, and contact route still need verification before outreach. |

Example 100-point score breakdown:

| Category | Max | Score | Rationale |
| --- | ---: | ---: | --- |
| Sonic / genre fit | 25 | 21 | Scene clues match Echo Radius's leftfield house, broken beat, dubby techno, and ambient-adjacent hardware context. |
| Scene / culture fit | 20 | 16 | A small collective-style electronic night appears culturally plausible, but the flyer-style note is unverified and the named artists are not source-checked. |
| Artist level fit | 15 | 10 | The opportunity appears reachable for an emerging regional artist, but capacity, billing patterns, and fee expectations are unknown. |
| Audience fit | 10 | 7 | The likely room seems compatible with Echo Radius's club and live-hardware positioning, but audience size and context are unknown. |
| Timing / booking window | 10 | 4 | Late May 2026 may be actionable, but the exact date, lineup status, and booking window are unknown. |
| Geography / logistics | 10 | 8 | Porto is plausible from a Lisbon base and fits the Portugal/Iberian target region, but availability and fee constraints are unknown. |
| Contact quality | 5 | 0 | No verified contact route exists in this fixture. |
| Strategic value | 5 | 4 | A credible Porto collective night could support regional route-building if verified. |

| Field | Example output |
| --- | --- |
| Final score | 70 / 100 |
| Classification | B / Worth pitching |
| Override rules applied | No verified contact route caps the classification at B / Worth pitching. Do not route to outreach until contact verification succeeds. |
| Confirmed facts | User provided event name, city, venue text, rough edition/date, scene clues, visible lineup, and promoter/collective text. |
| Assumptions | Echo Radius's fictional booking-state context is current. Signal Bloom may be the relevant promoter or curator. The opportunity may fit emerging regional electronic programming. |
| Unknowns | Official event existence; final lineup accuracy; exact date; booking decision maker; official contact route; submission policy; compensation expectations; final artist availability. |
| Red flags | Evidence quality is low until an official source is checked. No verified contact. Exact date unknown. |
| Recommended next action | Run contact verification and official-source verification before any outreach draft. |
| `booking-state.md` updates required | Update Opportunity Pipeline with fit readiness status, missing readiness notes, final score, classification, score breakdown, red flags, and next action. Add handoff from fit-classification to contact-verification. Keep status as internal research only. |

## 4. contact-verification Output

This example demonstrates the safe stop when no verified contact exists.

| Field | Example output |
| --- | --- |
| Opportunity ID | OPP-ML-001 |
| Contact status | Unknown |
| Contact route | No verified official contact route found in this fixture. |
| Confidence level | Low |
| Confirmed facts | The user-provided note names Signal Bloom and Atrium 9. |
| Assumptions | Signal Bloom may be the event promoter, but this is not confirmed from an official source. |
| Unknowns | Official website or social page; public booking email; contact form; venue booking page; promoter role; do-not-contact constraints. |
| Safety notes | Do not invent an email from the promoter or venue name. Do not use private contacts. Do not scrape or guess contact details. Do not draft outreach as if a recipient is verified. |
| Recommended next action | Ask the user for an official source link or run a future approved official-source verification workflow if that capability is explicitly scoped. |
| Can outreach drafting happen next? | No. Outreach drafting should wait until an official contact route is verified or the user explicitly provides a contact route and marks it as approved for internal drafting. |

Alternative example-only contact route, if the user supplies it:

| Field | Example output |
| --- | --- |
| Contact route | Fictional official contact form: `hxxps://example.invalid/signal-bloom/contact` |
| Confidence level | Medium only if the user says this is the official Signal Bloom contact page. |
| Safety notes | Treat as example-only. In a real workflow, preserve the user-provided source note and still require `approval-before-action` before any external action. |

## 5. Stop Point

CircuitScout stops before outreach because the contact status is Unknown.

No external action happens in this fixture:

- No outreach is sent.
- No Gmail draft is created.
- No reply is sent or forwarded.
- No Calendar action is scheduled.
- No Sheets, CRM, API, scraping, OCR, browser automation, or live web research is performed.
- No final booking decision is made.

Any future external action would require `skills/approval-before-action/SKILL.md` and explicit human approval.

## 6. Sample `booking-state.md` Updates

### Opportunity Pipeline

| Discovery ID | Opportunity ID | Name | Type | Event / series / organization relationship | City | Country | Date / edition | Source links | Source type | Evidence summary | Extracted lineup / artists | Venue | Promoter / collective | Genre / scene clues | Duplicate check result | Candidate status | Initial priority guess | Fit readiness status | Missing readiness notes | Status | Priority | Fit score | Fit classification | Score breakdown | Confirmed facts | Assumptions | Unknowns | Red flags | Next action | Contact research next | Recommended next skill | Owner | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---: | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| DSC-ML-001 | OPP-ML-001 | Signal Bloom: Courtyard Frequencies | Club night / collective event candidate | Event appears connected to Signal Bloom; relationship unverified | Porto | Portugal | Late May 2026 / spring edition; exact date unknown | User-provided note: `hxxps://example.invalid/signal-bloom-courtyard-frequencies` | User-provided manual lead | Flyer/link-like note includes event name, city, venue, rough edition/date, lineup, promoter/collective text, and scene clues. | Mara Vale; Jun Risco; Pale Circuit; Nia Quell | Atrium 9 | Signal Bloom | Leftfield house; broken beat; dubby techno; ambient room; local live hardware set | No duplicate found in local example state | Needs official-source verification | Medium | Ready for contact verification | None blocking full scoring; official source, exact date, lineup status, and contact route still need verification before outreach | Internal research only | Medium | 70 | B / Worth pitching | Sonic 21/25; scene 16/20; artist level 10/15; audience 7/10; timing 4/10; geography 8/10; contact quality 0/5; strategic value 4/5 | User provided visible text, source note, and fictional Echo Radius profile context | Small club/collective opportunity; possible fit for Echo Radius; Signal Bloom may be the promoter | Official source; exact date; booking owner; contact route; submission policy; final artist availability | Unverified manual source; no contact; exact date unknown | Run contact verification and official-source verification before any outreach draft | Required before outreach drafting | `skills/contact-verification/SKILL.md` | Codex/OpenAI workflow | Manual fixture row; no external action |

### Contact Register

| Contact ID | Opportunity ID | Name | Organization | Role | Contact route type | Contact value/route | Source link | Source type | Confidence | Confirmed facts | Assumptions | Unknowns | Duplicate/conflict notes | Permission/safety notes | Do-not-contact status | Last verified date | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CON-ML-001 | OPP-ML-001 | Unknown | Signal Bloom / Atrium 9 | Unknown | Manual research needed | Unknown | User-provided note only | User-provided manual lead | Low | Note names Signal Bloom and Atrium 9 | Signal Bloom may be the promoter | Official contact route; booking owner; permission constraints | No duplicate contact found in local example state | Do not invent emails or use private contacts. Stop before outreach. | Unknown | Not verified | Ask user for official source or run future approved official-source verification |

### Open Questions

| Question ID | Question | Needed for | Owner | Status | Answer/source | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Q-ML-001 | What is the official source for Signal Bloom: Courtyard Frequencies? | Evidence verification | User or future approved research workflow | Open | Unknown | User-provided note is not enough for outreach. |
| Q-ML-002 | What is the exact event date and edition? | Fit and availability review | User or future approved research workflow | Open | Unknown | Rough date is late May 2026 / spring edition. |
| Q-ML-003 | What is the official contact route for booking or submissions? | Contact verification | User or future approved research workflow | Open | Unknown | Required before outreach drafting. |
| Q-ML-004 | Is Signal Bloom, Atrium 9, or another entity the booking decision maker? | Contact verification | User or future approved research workflow | Open | Unknown | Avoid contacting the wrong route. |

### Handoff Chain

| Handoff ID | Date | From | To | Workflow stage | Summary | Pending approvals | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HND-ML-001 | 2026-04-27 | User manual intake | `skills/opportunity-discovery/SKILL.md` | Intake to discovery | User supplied a fictional flyer/link-like note for a possible Porto club night. | None; internal analysis only | Extract candidate opportunity fields. |
| HND-ML-002 | 2026-04-27 | `skills/opportunity-discovery/SKILL.md` | `skills/fit-classification/SKILL.md` | Discovery to fit | Candidate OPP-ML-001 created with unverified source evidence and unknown official source/contact. | None; internal analysis only | Score fit and identify red flags. |
| HND-ML-003 | 2026-04-27 | `skills/fit-classification/SKILL.md` | `skills/contact-verification/SKILL.md` | Fit to contact verification | Fit is B / Worth pitching, but no outreach readiness exists until contact and official-source verification succeed. | None; internal analysis only | Verify official contact route or ask user for one. |
| HND-ML-004 | 2026-04-27 | `skills/contact-verification/SKILL.md` | Human operator | Stop before outreach | Contact status remains Unknown; outreach drafting should not proceed. | Approval would be required before any future external action. | Ask user for official source/contact route. |

## 7. What Not To Do

- Do not invent real contacts, email addresses, phone numbers, social handles, or private relationships.
- Do not send outreach.
- Do not create a Gmail draft.
- Do not scrape pages, call APIs, use OCR, automate a browser, or perform live web research.
- Do not write to Calendar, Sheets, CRM, or external systems.
- Do not treat assumptions as confirmed facts.
- Do not make a final booking decision.
