---
name: artist-profile
description: Capture and maintain CircuitScout's structured, source-aware artist profile before discovery, fit classification, contact verification, or outreach drafting.
---

# Artist Profile

CircuitScout uses the artist profile as the source of truth for booking work.

Core question: what confirmed artist information, positioning, assets, constraints, preferences, and missing fields should CircuitScout use before discovering opportunities, classifying fit, verifying contacts, or drafting booking outreach?

This is an internal profile-building and state-maintenance workflow. It does not require human approval by itself. Any external exposure of private, legal, admin, fee, availability, travel, or negotiation-sensitive details requires `skills/approval-before-action/SKILL.md`.

Do not perform Gmail, Calendar, Sheets, API, scraping, OCR, browser automation, live web research, sending, replying, forwarding, scheduling, labeling, archiving, or external CRM/spreadsheet writes inside this skill. Use only user-provided material, existing local booking state, and explicitly provided source notes. Mark missing information as `Unknown` or `Missing`.

## When To Use

Use this skill before `skills/opportunity-discovery/SKILL.md`, `skills/fit-classification/SKILL.md`, `skills/contact-verification/SKILL.md`, or `skills/outreach-drafting/SKILL.md` when artist context is missing, thin, stale, contradictory, or not separated into confirmed facts, assumptions, unknowns, and missing assets.

Use it to:

- Initialize an artist profile for a booking workflow.
- Convert user notes, EPK material, bios, links, asset folders, and booking preferences into a structured profile.
- Update the profile when the user provides corrections, new assets, constraints, target markets, do-not-contact preferences, or outreach voice guidance.
- Audit whether the artist profile is ready for discovery, fit classification, contact verification, outreach drafting, or serious booking negotiation.
- Identify missing fields and route the workflow back to the correct internal next step.

For first use, a new project may start with the compact `examples/booking-desk/artist-profile-intake.md` template. Use `examples/booking-desk/intake-to-booking-state-transfer.md` to transfer only confirmed fields, clearly labeled assumptions, unknowns, claims needing verification, sensitive/private fields, and missing assets from that intake into `booking-state.md`.

Read `booking-state.md` first when it exists, especially:

- `Artist Profile`
- `Positioning / Sound / Scene Fit`
- `EPK Assets`
- `Target Markets`
- `Booking Goals`
- `Risk Register`
- `Do-not-contact List`
- `Open Questions`

## Source Hygiene Categories

Keep these categories separate in every profile update:

- `User-provided facts`: directly supplied by the user.
- `Source-backed facts`: supported by provided source links, documents, files, EPK material, or existing local state.
- `Assumptions`: plausible working interpretations that are not confirmed.
- `Unknowns`: information not currently available.
- `Outdated fields`: information that may no longer be current.
- `Claims needing verification`: useful claims that should not be used as proof yet.
- `Sensitive/private fields`: legal names, admin contacts, fee ranges, availability, travel constraints, private emails, and other details that should not be exposed externally without user approval.

Do not convert positioning, goals, taste language, or aspirational language into proof. A phrase like "rising artist" is only safe if backed by confirmed evidence; otherwise treat it as positioning or a claim needing verification.

## Profile Status Values

Use one or more status values when useful:

- `Empty`
- `Draft`
- `Usable for discovery`
- `Usable for fit classification`
- `Usable for outreach drafting`
- `Missing critical outreach assets`
- `Needs human review`
- `Outdated`
- `Blocked`

Status guidance:

- `Empty`: no usable artist identity is present.
- `Draft`: core identity exists, but required fields are incomplete or weakly sourced.
- `Usable for discovery`: enough artist identity, sound/scene fit, and target-market direction exists to find candidate opportunities.
- `Usable for fit classification`: enough sound, scene, positioning, geography, goals, and constraints exist to score opportunity fit.
- `Usable for outreach drafting`: enough confirmed identity, positioning, EPK assets, safe claims, and outreach voice exists to prepare review-only drafts.
- `Missing critical outreach assets`: discovery or classification may continue, but outreach should not be drafted or approved until missing assets are resolved.
- `Needs human review`: profile has contradictions, sensitive details, unclear claims, or consequential preferences requiring user confirmation.
- `Outdated`: key fields may no longer be current.
- `Blocked`: missing information prevents the requested workflow stage.

## Fields To Capture

### Artist Identity

Capture:

- Artist/project name.
- Legal/admin name only if the user provides it and it is needed.
- Location/base.
- Project type: `DJ`, `producer`, `live act`, `hybrid`, `label`, `collective`, `other`.
- Short bio.
- Long bio.
- Languages.
- Contact/admin owner if relevant.

Private or admin details should be marked sensitive. Do not expose them externally unless relevant and user-approved.

### Sound / Genre / Scene Fit

Capture:

- Primary genres.
- Secondary genres.
- BPM/energy range if relevant.
- Sonic references.
- Similar artists.
- Labels/scenes associated with the sound.
- Underground/commercial positioning.
- Experimental/accessibility balance.
- Live/DJ format.
- Ideal contexts such as club, festival, art space, radio, support slot, late-night, warm-up, closing, listening room, or hybrid setting.

Separate confirmed sound evidence from interpretive fit notes. If similar artists are user-provided comparisons rather than sourced relationships, label them as user-provided references, not proof.

### Positioning

Capture:

- One-line positioning statement.
- What makes the artist specific.
- Emotional/scene identity.
- Aesthetic language.
- Audience context.
- Do-not-overclaim boundaries.
- Words or claims to avoid.

Positioning can guide tone and fit evaluation, but it must not become unsupported proof in outreach.

### EPK Assets

Capture and track status for:

- Official website.
- EPK link.
- Press kit folder.
- Bio links.
- Press photos.
- Logo.
- Live/DJ videos.
- Mixes.
- Releases.
- SoundCloud, Bandcamp, Spotify, YouTube, Instagram, TikTok, Resident Advisor, and other relevant links.
- Tech rider.
- Hospitality rider.
- Stage plot if relevant.
- Booking contact/admin contact if user-provided.

Use asset status values:

- `confirmed`
- `missing`
- `outdated`
- `needs review`

If outreach would require a missing asset, route back to `skills/artist-profile/SKILL.md` before drafting.

### Proof / Credibility

Capture only confirmed or clearly labeled unverified proof:

- Confirmed releases.
- Confirmed labels.
- Confirmed past bookings.
- Confirmed support slots.
- Confirmed radio/mix features.
- Confirmed press.
- Confirmed awards/grants only if user-provided or source-backed.
- Confirmed audience/social proof only if user-provided or source-backed.
- Claims needing verification.

Never invent artist credentials, relationships, releases, bookings, press, metrics, awards, label affiliations, or audience data.

### Booking Preferences

Capture:

- Target cities/countries.
- Target scenes.
- Target venues/festivals/promoters.
- Anti-targets.
- Preferred event types.
- Minimum expectations if user provides them.
- Fee range only if user provides it.
- Travel constraints.
- Availability constraints.
- Radius/exclusivity constraints if relevant and user-provided.
- Do-not-contact preferences.

If a booking decision depends on fees, availability, travel, legal terms, exclusivity, or radius constraints not present in the profile, mark the decision as `needs human input`.

### Outreach Voice

Capture:

- Tone of voice.
- Words to use.
- Words to avoid.
- Short pitch angle.
- Warmer pitch angle.
- More formal pitch angle.
- Language variants if useful.
- How direct or understated outreach should be.

Outreach voice should keep drafts human, specific, modest, and source-backed. Never use unsupported hype.

### Missing / Blocked Fields

Classify missing fields by workflow need:

- Required for discovery.
- Required for fit classification.
- Required for outreach drafting.
- Required for serious booking negotiation.
- Recommended next internal step.

Use missing-field classifications to route the workflow. Do not fill gaps creatively.

## Readiness Gates

### Discovery Readiness

Discovery can proceed when these are present:

- Artist/project name.
- Basic project type.
- At least one sound, genre, scene, or positioning clue.
- At least one target market, target scene, goal, or source list to investigate.

If these are missing, output `Blocked` or `Draft` and ask for the smallest missing input.

### Fit Classification Readiness

Fit classification can proceed when these are present:

- Artist/project name.
- Sound/genre/scene notes.
- Positioning or ideal context notes.
- Target market or geography preference.
- Key constraints that would make an opportunity out of scope.
- Any known proof or current level indicators, even if modest.

If artist level, logistics, or goals are missing, classify conservatively and mark unknowns.

### Outreach Drafting Readiness

Outreach drafting can proceed only when these are present or clearly marked as placeholders:

- Artist/project name.
- Safe positioning statement.
- Confirmed EPK, music, mix, release, video, bio, or other asset link relevant to the draft.
- Claims safe to use.
- Claims not safe to use.
- Outreach voice notes or default restrained tone.
- Contact verification result of `Verified` or `Likely`.
- No do-not-contact conflict.

If a draft would need a missing EPK link, music link, bio, asset, proof claim, booking constraint, or private detail, output `Missing critical outreach assets` or `Needs human review` and route back to this skill.

### Serious Booking Negotiation Readiness

Serious negotiation requires human input for:

- Fee range or minimum expectations.
- Availability.
- Travel and hospitality constraints.
- Technical requirements.
- Contract, billing, exclusivity, radius, visa, tax, or legal terms.
- Who may speak for the artist.

Do not negotiate, confirm, accept, decline, or commit dates. Route external or consequential actions through `skills/approval-before-action/SKILL.md`.

## Hard Rules

- Never invent artist credentials.
- Never invent links, releases, bookings, fees, labels, press, metrics, relationships, availability, or affiliations.
- Never treat aspirational positioning as confirmed proof.
- Never expose private/legal/admin details unless relevant and user-approved.
- Never use unsupported hype in outreach.
- If key profile fields are missing, mark them as missing instead of filling gaps creatively.
- If an outreach draft would require a missing asset, route back to this skill before drafting.
- If a booking decision depends on fees, availability, travel, or legal terms not present in the profile, mark it as `needs human input`.
- Keep source links and source labels attached to the claims they support.
- Keep private details out of public-facing summaries unless explicitly approved.

## Output Format

Use this structure for profile creation or profile audit:

```markdown
## Artist Profile: ART-###

- Artist profile ID:
- Artist/project name:
- Profile status:
- Last updated:
- Prepared from:

### Confirmed Facts

-

### Assumptions

-

### Unknowns

-

### Missing Assets

-

### Positioning Summary

-

### Sound / Scene Summary

-

### Target Markets

-

### Anti-targets

-

### EPK Asset Checklist

| Asset | Status | Source/link | Notes |
| --- | --- | --- | --- |
| Official website |  |  |  |
| EPK link |  |  |  |
| Press kit folder |  |  |  |
| Bio |  |  |  |
| Press photos |  |  |  |
| Logo |  |  |  |
| Live/DJ videos |  |  |  |
| Mixes |  |  |  |
| Releases |  |  |  |
| Social/music links |  |  |  |
| Tech rider |  |  |  |
| Hospitality rider |  |  |  |
| Stage plot |  |  |  |
| Booking/admin contact |  |  |  |

### Booking Constraints

-

### Outreach Voice Notes

-

### Claims Safe To Use

-

### Claims Not Safe To Use

-

### Missing / Blocked Fields By Workflow

| Workflow need | Missing or blocked fields | Impact |
| --- | --- | --- |
| Required for discovery |  |  |
| Required for fit classification |  |  |
| Required for outreach drafting |  |  |
| Required for serious booking negotiation |  |  |

### Recommended Next Internal Step

-

### booking-state.md Updates Required

-
```

## Booking-State Integration

Use `skills/booking-state/SKILL.md` when updating `booking-state.md`.

Update:

- `Artist Profile` with profile ID, status, identity, source hygiene, confirmed facts, assumptions, unknowns, sensitive fields, and last updated date.
- `Positioning / Sound / Scene Fit` with genre, scene, sonic references, ideal contexts, positioning summary, safe claims, and claims to avoid.
- `EPK Assets` with asset status, links/paths, source, last reviewed date, and missing/outdated/needs-review flags.
- `Target Markets` with target cities, countries, scenes, priority, rationale, anti-targets, and source/preference notes.
- `Booking Goals` with booking preferences, preferred event types, minimum expectations if user-provided, constraints, and status.
- `Open Questions` with missing fields required for discovery, fit classification, outreach drafting, or serious booking negotiation.
- `Risk Register` with unsupported claims, outdated assets, sensitive details, do-not-contact preferences, missing negotiation inputs, contradictory profile facts, or overclaiming risks.

Artist-profile updates are usually editable state, not append-only audit records. If a profile change affects a consequential booking decision, add a `Decision Log` entry explaining the change.

## Integration With Other CircuitScout Skills

- Use `skills/using-circuitscout/SKILL.md` to route artist-profile before discovery, classification, contact verification, or drafting when context is missing or incomplete.
- Use `skills/opportunity-discovery/SKILL.md` only after the profile is at least `Usable for discovery` or the user explicitly provides enough lead context for a limited discovery pass.
- Use `skills/fit-classification/SKILL.md` only after the profile is at least `Usable for fit classification`, or score conservatively and mark missing profile fields.
- Use `skills/contact-verification/SKILL.md` after fit classification; artist-profile informs safety notes, do-not-contact checks, and whether outreach can proceed.
- Use `skills/outreach-drafting/SKILL.md` only after profile readiness supports `Usable for outreach drafting` or missing fields are intentionally carried as visible placeholders.
- Use `skills/approval-before-action/SKILL.md` before exposing private/admin/legal details externally, using booking constraints in negotiation, sending or creating external drafts, committing dates, or changing external systems.

## Safety Checklist

Before finalizing an artist profile, verify:

- Confirmed facts, assumptions, unknowns, outdated fields, claims needing verification, and sensitive/private fields are separated.
- No artist credentials, links, releases, bookings, fees, labels, press, metrics, relationships, availability, or affiliations were invented.
- Aspirational positioning is not treated as proof.
- EPK assets have explicit statuses.
- Missing fields are marked rather than creatively completed.
- Claims safe to use and claims not safe to use are explicit.
- Any workflow blocked by missing assets, fees, availability, travel, legal terms, or private details is marked as blocked or needs human input.
- Any external-facing or consequential next action routes through `skills/approval-before-action/SKILL.md`.
