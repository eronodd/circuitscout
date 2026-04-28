# Artist Intake To Booking State Transfer Checklist

This fixture shows how to transfer a completed compact `artist-profile-intake.md` into the canonical `booking-state.md` structure. It is for local CircuitScout state preparation only. It does not perform live research, create drafts, send messages, schedule anything, or write to external systems.

Use it to keep first-use intake useful without mixing confirmed facts, assumptions, unknowns, unverified claims, or sensitive/private fields.

## Purpose

The compact intake is a fast way to gather artist context. `booking-state.md` is the durable booking desk state. This checklist bridges the two by showing what can move safely, what must remain blocked or questioned, and what must never be promoted into outreach-ready proof.

The transfer should help a Codex/OpenAI workflow:

- Read a compact intake.
- Label every field before moving it.
- Transfer only safe, useful information.
- Create Open Questions for missing or unclear fields.
- Store risks and unverified claims away from outreach-ready copy.
- Keep aspirational positioning separate from proven credibility.

## When To Use This Transfer Checklist

Use this after `examples/booking-desk/artist-profile-intake.md` has been filled and before treating the artist profile as canonical `booking-state.md`.

Use it when:

- Starting CircuitScout for a new artist.
- Auditing a compact intake before opportunity discovery.
- Deciding whether an artist profile is ready for discovery, fit classification, or outreach drafting.
- Converting a fictional or example intake into sample `booking-state.md` rows.

Do not use it to invent missing artist data, verify real-world claims, perform research, or trigger external actions.

## Step-By-Step Transfer Process

1. Read the completed intake.
2. Mark every field as `confirmed fact`, `assumption`, `unknown`, `claim needing verification`, or `sensitive/private`.
3. Transfer confirmed/user-provided fields into the correct `booking-state.md` sections.
4. Move missing or unclear fields into `Open Questions`.
5. Move risky or unverified claims into `Risk Register` or `Claims needing verification`.
6. Mark outreach readiness conservatively.
7. Do not invent missing assets or proof.
8. Recommend the next internal skill based on readiness:
   - `skills/artist-profile/SKILL.md` if profile identity, sound, assets, proof, preferences, or source hygiene are incomplete.
   - `skills/opportunity-discovery/SKILL.md` if the profile is usable for broad discovery.
   - `skills/fit-classification/SKILL.md` if opportunity context exists and the profile is usable for fit review.
   - `skills/outreach-drafting/SKILL.md` only if outreach-critical assets, safe claims, verified or likely contact context, and no blocking risks exist.

## Mapping Table

| Intake section | Intake field | Destination booking-state.md section | Transfer rule | Source hygiene label | Notes / warnings |
| --- | --- | --- | --- | --- | --- |
| Basic Identity | Artist/project name | Artist Profile | Transfer if present. If missing, stop. | confirmed fact if user-provided | Required before any downstream workflow. |
| Basic Identity | Base city/country | Artist Profile | Transfer as location/base if user-provided. | confirmed fact or unknown | Do not infer travel range from base. |
| Basic Identity | Project type | Artist Profile; Positioning / Sound / Scene Fit | Transfer as project type and live/DJ format if clear. | confirmed fact if user-provided | If unclear, create Open Question. |
| Basic Identity | Languages | Artist Profile; Outreach Voice | Transfer language capability and possible outreach variants. | confirmed fact if user-provided | Do not assume language fluency beyond user note. |
| Basic Identity | Short bio | Artist Profile | Transfer as short bio only if user-provided or source-backed. | confirmed fact or claim needing verification | Keep promotional claims inside the bio bounded. |
| Sound / Scene | Primary genres | Positioning / Sound / Scene Fit | Transfer into primary genres. | confirmed fact if user-provided; assumption if inferred | User taste descriptors are not proof of scene affiliation. |
| Sound / Scene | Secondary genres | Positioning / Sound / Scene Fit | Transfer into secondary genres. | confirmed fact or assumption | Mark inferred genres as assumptions. |
| Sound / Scene | BPM / energy | Positioning / Sound / Scene Fit | Transfer confirmed ranges; otherwise store as assumption. | assumption if inferred | Exact BPM should be Unknown unless provided. |
| Sound / Scene | Sonic references | Positioning / Sound / Scene Fit | Transfer as aesthetic language or sonic references. | confirmed fact if user-provided | References describe sound; they do not prove relationships. |
| Sound / Scene | Similar artists | Positioning / Sound / Scene Fit | Transfer as user-provided references only. | confirmed fact about user comparison; not proof | Never imply association, endorsement, or shared billing. |
| Sound / Scene | Scene/community context | Positioning / Sound / Scene Fit; Open Questions | Transfer confirmed context; question unknown context. | confirmed fact, assumption, or unknown | Do not invent community affiliation. |
| Sound / Scene | Ideal event contexts | Positioning / Sound / Scene Fit; Booking Goals | Transfer confirmed preferences; label inferred contexts. | confirmed fact or assumption | Use for discovery direction, not external proof. |
| Positioning | One-line positioning | Positioning / Sound / Scene Fit; Outreach Voice | Transfer as positioning and pitch guidance if bounded. | confirmed fact if user-provided positioning | Positioning is not proof. |
| Positioning | What makes the artist specific | Positioning / Sound / Scene Fit; Outreach Voice | Transfer as specificity and tone guidance. | confirmed fact if user-provided | Keep subjective language modest. |
| Positioning | Words/claims to avoid | Positioning / Sound / Scene Fit; Outreach Voice; Risk Register if overclaim risk exists | Transfer into claims not safe to use and words to avoid. | confirmed fact / user preference | Treat as hard outreach boundary. |
| Positioning | Claims safe to use | Positioning / Sound / Scene Fit | Transfer only bounded, user-provided, source-backed, or plainly descriptive claims. | confirmed fact or source-backed fact | Do not include unverified proof claims. |
| Links / Assets | Website | EPK Assets; Missing / Blocked Fields; Open Questions if incomplete | Transfer link if provided; mark placeholder or missing status. | confirmed fact if user-provided; needs review if placeholder | Do not validate by browsing in this slice. |
| Links / Assets | EPK | EPK Assets; Missing / Blocked Fields; Open Questions if incomplete | Transfer as EPK link with status. | confirmed fact, needs review, or missing | Required before outreach drafting unless a different approved asset is enough. |
| Links / Assets | Press photos | EPK Assets; Missing / Blocked Fields | Transfer as confirmed, missing, or needs review. | confirmed fact or missing | Missing press photos block many outreach workflows. |
| Links / Assets | Logo | EPK Assets; Missing / Blocked Fields | Transfer status. | confirmed fact or missing | Usually not discovery-critical; can matter for press kits. |
| Links / Assets | Mixes | EPK Assets | Transfer user-provided links with review status. | confirmed fact if user-provided; needs review if placeholder | Do not claim quality, plays, or external validation. |
| Links / Assets | Releases | EPK Assets; Proof / Credibility; Risk Register if unverified | Transfer link as asset; proof only if confirmed. | confirmed fact or claim needing verification | Placeholder release links are not proof. |
| Links / Assets | Videos | EPK Assets; Missing / Blocked Fields | Transfer status. | confirmed fact, missing, or unknown | Live/DJ video may be needed for fit or outreach. |
| Links / Assets | Social links | EPK Assets | Transfer user-provided links with status. | confirmed fact if user-provided; needs review if placeholder | Do not infer audience metrics. |
| Links / Assets | Tech rider | EPK Assets; Booking Constraints; Missing / Blocked Fields | Transfer status; do not expose externally by default. | confirmed fact or sensitive/private if detailed | Needed for negotiation, not early outreach unless requested. |
| Links / Assets | Hospitality rider | EPK Assets; Booking Constraints; Missing / Blocked Fields | Transfer status; do not expose externally by default. | confirmed fact or sensitive/private if detailed | Treat as negotiation-sensitive. |
| Links / Assets | Missing assets | Missing / Blocked Fields; Open Questions | Transfer as explicit blockers. | unknown or missing | Never fill missing assets creatively. |
| Proof / Credibility | Confirmed releases | Proof / Credibility; Artist Profile; EPK Assets if link-based | Transfer only confirmed releases. | confirmed fact or source-backed fact | If not confirmed, move to claims needing verification. |
| Proof / Credibility | Confirmed labels | Proof / Credibility; Artist Profile | Transfer only confirmed labels. | confirmed fact or source-backed fact | Do not invent affiliations. |
| Proof / Credibility | Confirmed past bookings | Proof / Credibility; Artist Profile | Transfer only confirmed bookings. | confirmed fact or source-backed fact | Do not use unverified bookings in outreach. |
| Proof / Credibility | Confirmed support slots | Proof / Credibility | Transfer only confirmed support slots. | confirmed fact or source-backed fact | Support slots are external proof only when verified. |
| Proof / Credibility | Confirmed radio/mix features | Proof / Credibility; EPK Assets if asset-based | Transfer only confirmed features or user-provided asset links. | confirmed fact or source-backed fact | Distinguish a hosted mix asset from a credible third-party feature. |
| Proof / Credibility | Confirmed press | Proof / Credibility; EPK Assets if link-based | Transfer only confirmed press. | confirmed fact or source-backed fact | Never invent quotes or publication names. |
| Proof / Credibility | Claims needing verification | Proof / Credibility; Risk Register; Positioning / Sound / Scene Fit claims not safe to use | Store separately and mark unsafe for outreach. | claim needing verification | Required split: claims safe to use vs claims not safe to use. |
| Booking Preferences | Target cities/countries | Target Markets | Transfer user preferences; mark priority Unknown unless provided. | confirmed fact / user preference | If missing, discovery can proceed only broadly. |
| Booking Preferences | Target scenes | Target Markets; Booking Goals | Transfer as target scenes. | confirmed fact / user preference | Do not infer exact venues from scenes. |
| Booking Preferences | Target venues/festivals/promoters | Target Markets; Booking Goals; Open Questions | Transfer named targets only if user-provided. | confirmed fact / user preference | Verify later before outreach. |
| Booking Preferences | Anti-targets | Anti-targets; Booking Constraints; Risk Register if consequential | Transfer as exclusions. | confirmed fact / user preference | Treat as safety/fit boundary. |
| Booking Preferences | Preferred event types | Booking Goals | Transfer as preferred event types. | confirmed fact / user preference | Use for discovery and fit. |
| Booking Preferences | Travel constraints | Booking Constraints; Risk Register if missing affects outreach/negotiation | Transfer only if user-provided; mark sensitive/private if detailed. | sensitive/private or unknown | Do not use missing travel constraints in negotiation. |
| Booking Preferences | Availability constraints | Booking Constraints; Risk Register if missing affects outreach/negotiation | Transfer only if user-provided; mark sensitive/private if detailed. | sensitive/private or unknown | Do not imply availability. |
| Booking Preferences | Fee range | Booking Constraints; Risk Register if needed and missing | Transfer only if user provided and wants it stored. | sensitive/private | Never include externally without approval. |
| Booking Preferences | Do-not-contact preferences | Do-not-contact List; Booking Constraints; Risk Register if relevant | Transfer confirmed preferences. | sensitive/private / user preference | Do-not-contact entries override outreach. |
| Outreach Voice | Preferred tone | Outreach Voice; Draft Outbox guidance context | Transfer as internal guidance. | confirmed fact / user preference | Does not authorize draft creation. |
| Outreach Voice | Words to use | Outreach Voice | Transfer as guidance. | confirmed fact / user preference | Keep language source-aware. |
| Outreach Voice | Words to avoid | Outreach Voice; Claims not safe to use | Transfer as avoid list. | confirmed fact / user preference | Helps prevent unsupported hype. |
| Outreach Voice | Short pitch angle | Outreach Voice; Draft Outbox guidance context | Transfer as internal pitch angle if safe. | confirmed fact / user preference | Do not use in outreach until assets and claims are ready. |
| Outreach Voice | Warmer pitch angle | Outreach Voice; Draft Outbox guidance context | Transfer as guidance. | confirmed fact / user preference | Keep review-only. |
| Outreach Voice | Formal pitch angle | Outreach Voice; Draft Outbox guidance context | Transfer as guidance. | confirmed fact / user preference | Do not add credentials. |
| Readiness Checklist | Usable for discovery | Artist Profile status; Missing / Blocked Fields | Set conservatively based on required fields. | local state | Discovery needs identity, project type, sound clue, and some target direction. |
| Readiness Checklist | Usable for fit classification | Artist Profile status; Missing / Blocked Fields | Set conservatively; add Open Questions for gaps. | local state | Fit can proceed with caveats if opportunity context exists. |
| Readiness Checklist | Usable for outreach drafting | Artist Profile status; Missing / Blocked Fields | Mark No unless safe assets, safe claims, contact context, and voice exist. | local state | Missing EPK/assets/safe claims should block drafting. |
| Readiness Checklist | Missing critical outreach assets | Missing / Blocked Fields; EPK Assets; Open Questions | Transfer as blockers. | missing / unknown | Never mark outreach-ready when these are unresolved. |
| Readiness Checklist | Needs human review | Artist Profile status; Open Questions; Risk Register | Transfer as status and risk if needed. | local state | Use when claims, private fields, or contradictions need confirmation. |
| Readiness Checklist | Blocked fields | Missing / Blocked Fields; Open Questions | Transfer each blocker. | missing / unknown | Ask smallest useful question. |
| Source Hygiene | User-provided facts | Artist Profile Source Hygiene | Transfer as user-provided facts. | confirmed fact | Keep separate from source-backed facts. |
| Source Hygiene | Source-backed facts | Artist Profile Source Hygiene | Transfer only if actual source material was provided. | source-backed fact | Do not browse or verify in this fixture. |
| Source Hygiene | Assumptions | Artist Profile Source Hygiene; Positioning / Sound / Scene Fit assumptions | Transfer assumptions into assumption columns/rows. | assumption | Never upgrade to confirmed facts. |
| Source Hygiene | Unknowns | Artist Profile Source Hygiene; Open Questions | Transfer unknowns and make questions for critical gaps. | unknown | Unknown is better than invented. |
| Source Hygiene | Sensitive/private fields | Artist Profile Source Hygiene; Booking Constraints; Risk Register if needed | Store only if user-provided and needed; keep out of external-facing sections. | sensitive/private | Legal/admin/contact/fee/availability/travel details require approval before external use. |
| Next Internal Step | Recommended next skill | Handoff Chain; Missing / Blocked Fields | Transfer as the next internal handoff. | local state | Choose based on readiness gates. |
| Next Internal Step | Open questions | Open Questions | Transfer each unresolved question. | unknown / needs human input | Tie questions to profile ID when possible. |
| Next Internal Step | booking-state.md sections to update | Handoff Chain; Decision Log if user made a decision | Transfer as handoff summary; log explicit user decisions if consequential. | local state | Do not create Decision Log entries for invented decisions. |

## Safety Rules

- Never invent missing artist data.
- Never treat assumptions as confirmed facts.
- Never transfer sensitive/private admin data into external-facing sections unless user approved.
- Never mark profile as outreach-ready if EPK/assets/safe claims are missing.
- Never turn aspirational language into proof.
- Never use claims needing verification in outreach.
- Never expose legal/admin/private contact details by default.
- Always preserve the difference between confirmed facts, assumptions, unknowns, and claims needing verification.
- Never add real artist data to this fixture.
- Never create Gmail drafts, Calendar events, Sheets rows, CRM records, API calls, scraped data, OCR output, browser automation, live web research results, sends, forwards, replies, labels, archives, or schedules from this transfer.

## Example Transfer From Fictional Intake

Source fixture: `examples/booking-desk/artist-profile-intake-example.md`.

This example uses the fictional artist `Lumen Vale`. All links are placeholder-only or invalid example links. No private contact details are included.

### Field Labels

| Intake field group | Example label | Transfer handling |
| --- | --- | --- |
| Artist/project name, base, project type, languages | confirmed fact / user-provided | Transfer to `Artist Profile`. |
| Short bio and sound descriptors | confirmed fact about user-provided description | Transfer with source note; do not treat as external proof. |
| BPM / energy and ideal contexts | assumption | Transfer to assumption columns and note exact BPM/context unknown. |
| Similar artists | user-provided references, not proof | Transfer as references only. |
| Placeholder website, EPK, mix, release, social links | user-provided placeholder / needs review | Transfer to `EPK Assets` with `needs review`, not `confirmed`. |
| Press photos, logo, riders, videos | missing or unknown | Transfer to `Missing / Blocked Fields` and `Open Questions`. |
| Fictional release title | claim needing verification | Store in `Proof / Credibility` as unsafe externally and add risk. |
| Target cities/scenes and anti-targets | confirmed user preference | Transfer to `Target Markets`, `Anti-targets`, and `Booking Goals`. |
| Travel, availability, fee, do-not-contact | unknown or sensitive/private | Add Open Questions and risk if needed before outreach or negotiation. |
| Outreach tone and pitch angles | confirmed user preference | Transfer to `Outreach Voice` only; do not create external draft. |

### Resulting Sample `booking-state.md` Updates

These compact rows show the kind of local updates to make. They are not a complete replacement for the canonical template.

#### Artist Profile

| Field | Value | Source / hygiene | Notes |
| --- | --- | --- | --- |
| Artist profile ID | ART-LV-001 | local example state | Fictional example ID |
| Profile status | Usable for discovery; Missing critical outreach assets; Needs human review | local transfer review | Not outreach-ready because assets and proof are unresolved |
| Last updated | 2026-04-29 | local transfer review | Example fixture date |
| Artist/project name | Lumen Vale | user-provided fictional example | Example-only artist |
| Legal/admin name | Unknown | sensitive/private if provided | Do not request unless needed |
| Location/base | Example City, Exampleland | user-provided fictional example | Placeholder location |
| Project type | DJ / producer | user-provided fictional example | Use as format clue |
| Short bio | Fictional electronic project focused on warm broken rhythms, soft-edged techno, and late-night club textures | user-provided fictional example | Descriptive positioning, not proof |
| Languages | English; Spanish | user-provided fictional example | Do not infer fluency beyond intake |

#### Artist Profile Source Hygiene

| Category | Details | Source | Notes |
| --- | --- | --- | --- |
| User-provided facts | Name, base, project type, languages, sound descriptors, target city preferences, anti-targets, outreach tone preferences | `artist-profile-intake-example.md` | Fictional example only |
| Source-backed facts | None | Unknown | No live research or source verification performed |
| Assumptions | Mid-tempo/late-night energy; fit for intimate club nights, listening-room warmups, small leftfield electronic festivals, radio mixes | intake transfer review | Keep out of confirmed facts |
| Unknowns | Real assets, confirmed releases, labels, bookings, press, radio features, audience metrics, availability, travel constraints, official contact owner | intake transfer review | Create Open Questions |
| Claims needing verification | Whether "Night Garden Signals" exists; whether EPK link is current; whether any bookings, radio features, labels, or press can be named | intake transfer review | Not safe for outreach |
| Sensitive/private fields | Fee range, availability, travel constraints, admin contact, do-not-contact preferences | intake transfer review | Missing or unknown; do not expose externally |
| Recommended next internal step | `skills/artist-profile/SKILL.md`, then `skills/opportunity-discovery/SKILL.md` if discovery is desired | local transfer review | Resolve assets before outreach drafting |

#### Positioning / Sound / Scene Fit

| Field | Confirmed facts | Source | Assumptions | Unknowns | Notes |
| --- | --- | --- | --- | --- | --- |
| Primary genres | Leftfield house; broken beat; dubby techno | user-provided fictional example | Unknown | Scene affiliation | User descriptors, not proof of bookings or affiliations |
| Secondary genres | Ambient interludes; low-slung electro | user-provided fictional example | Unknown | Unknown | Keep as sound descriptors |
| BPM / energy range | Unknown | Unknown | Mid-tempo to late-night club energy | Exact BPM | Intake labels this as assumption |
| Sonic references | Hazy pads; loose percussion; subtle dub delays | user-provided fictional example | Unknown | Unknown | Tone references only |
| Similar artists | Artist A; Artist B; Artist C | user-provided comparison placeholders | Unknown | Real comparison basis | Not proof of association |
| Ideal contexts | Unknown | Unknown | Intimate club nights; listening-room warmups; small leftfield electronic festivals; radio mixes | Confirmed event targets | Use for broad discovery only |
| One-line positioning statement | Warm, dub-tinted club music for patient dancefloors | user-provided fictional example | Unknown | External proof | Positioning, not credibility |
| Claims safe to use | Leftfield electronic project; DJ / producer; warm broken rhythms; dubby club textures | user-provided fictional example | Unknown | Unknown | Safe because bounded and descriptive |
| Claims not safe to use | Breakthrough; internationally acclaimed; viral; sold out; legendary; "Night Garden Signals" as confirmed release | intake transfer review | Unknown | Verification status | Store unverified proof separately |

#### EPK Assets

| Asset ID | Asset type | Link/path | Status | Source | Last reviewed | Public-safe? | Needed for | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EPK-LV-001 | Official website | `hxxps://lumenvale.example.invalid` | needs review | user-provided placeholder | 2026-04-29 | No, placeholder only | discovery, fit, outreach | Example-only invalid domain |
| EPK-LV-002 | EPK link | `hxxps://lumenvale.example.invalid/epk` | needs review | user-provided placeholder | 2026-04-29 | No, placeholder only | outreach | Do not mark confirmed |
| EPK-LV-003 | Mix | `hxxps://audio.example.invalid/lumen-vale-mix-01` | needs review | user-provided placeholder | 2026-04-29 | No, placeholder only | fit, outreach | Requires real/current link |
| EPK-LV-004 | Releases | `hxxps://music.example.invalid/lumen-vale/night-garden-signals` | needs verification | user-provided placeholder | 2026-04-29 | No | fit, outreach | Not proof of release |
| EPK-LV-005 | Social link | `hxxps://social.example.invalid/lumenvale` | needs review | user-provided placeholder | 2026-04-29 | No, placeholder only | discovery, fit, outreach | Do not infer metrics |
| EPK-LV-006 | Press photos | Unknown | missing | intake transfer review | 2026-04-29 | Unknown | outreach | Critical outreach asset missing |
| EPK-LV-007 | Tech rider | Unknown | missing | intake transfer review | 2026-04-29 | Unknown | negotiation | Do not invent |
| EPK-LV-008 | Hospitality rider | Unknown | missing | intake transfer review | 2026-04-29 | Unknown | negotiation | Do not invent |

#### Proof / Credibility

| Proof ID | Claim type | Confirmed fact or claim | Source | Safe to use externally? | Needs verification? | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| PRF-LV-001 | Release | "Night Garden Signals" may exist as a fictional example title | `artist-profile-intake-example.md` | No | Yes | Placeholder release link is not proof |
| PRF-LV-002 | Label | Unknown | Unknown | No | Yes | Do not invent labels |
| PRF-LV-003 | Past booking | Unknown | Unknown | No | Yes | Do not invent bookings |
| PRF-LV-004 | Radio/mix feature | Unknown | Unknown | No | Yes | A user-provided mix link is not a third-party feature |
| PRF-LV-005 | Press | Unknown | Unknown | No | Yes | Do not invent press |

#### Target Markets

| Market ID | City/region | Country | Target scene | Priority | Rationale | Source/preference | Unknowns | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MKT-LV-001 | Lisbon | Portugal | Leftfield club nights; small electronic collectives; community radio events | Unknown | User preference | user-provided fictional example | Specific venues/promoters | Broad discovery only |
| MKT-LV-002 | Porto | Portugal | Leftfield club nights; small electronic collectives; community radio events | Unknown | User preference | user-provided fictional example | Specific venues/promoters | Broad discovery only |
| MKT-LV-003 | Madrid | Spain | Leftfield club nights; small electronic collectives; community radio events | Unknown | User preference | user-provided fictional example | Specific venues/promoters | Broad discovery only |
| MKT-LV-004 | Barcelona | Spain | Leftfield club nights; small electronic collectives; community radio events | Unknown | User preference | user-provided fictional example | Specific venues/promoters | Broad discovery only |
| MKT-LV-005 | Berlin | Germany | Leftfield club nights; small electronic collectives; community radio events | Unknown | User preference | user-provided fictional example | Specific venues/promoters | Broad discovery only |

#### Anti-targets

| Anti-target ID | City/region / scene / venue / promoter | Reason | Source/preference | Status | Notes |
| --- | --- | --- | --- | --- | --- |
| ANT-LV-001 | Commercial EDM rooms | Artist/team preference | user-provided fictional example | Active | Avoid in discovery and fit classification |
| ANT-LV-002 | High-volume bottle-service clubs | Artist/team preference | user-provided fictional example | Active | Avoid in discovery and fit classification |

#### Booking Goals

| Goal ID | Goal | Preferred event types | Timeframe | Priority | Success criteria | Constraints | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| GOAL-LV-001 | Find suitable leftfield electronic opportunities in target markets | DJ sets; warm-up slots; late-night smaller rooms; radio guest mixes | Unknown | Unknown | Candidate opportunities match sound/scene and anti-target boundaries | Travel, availability, and fee range unknown | Usable for broad discovery | Do not proceed to negotiation without constraints |

#### Booking Constraints

| Constraint ID | Area | Constraint / preference | Source | Sensitive? | Needed for | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CST-LV-001 | Fee range | Not provided | intake transfer review | Yes | negotiation | Unknown | Do not invent or expose |
| CST-LV-002 | Travel constraints | Unknown | intake transfer review | Yes | fit, negotiation | Unknown | Ask before using in fit or outreach |
| CST-LV-003 | Availability constraints | Unknown | intake transfer review | Yes | fit, negotiation | Unknown | Do not imply availability |
| CST-LV-004 | Do-not-contact preferences | Unknown | intake transfer review | Yes | discovery, contact, outreach | Unknown | Ask before outreach |

#### Outreach Voice

| Field | Guidance | Source | Notes |
| --- | --- | --- | --- |
| Tone of voice | Modest, specific, warm, and source-aware | user-provided fictional example | Internal guidance only |
| Words to use | Textured; patient; dub-tinted; leftfield; warm; careful | user-provided fictional example | Use only in future review drafts |
| Words to avoid | Viral; huge; guaranteed; exclusive; famous; packed | user-provided fictional example | Avoid unsupported hype |
| Short pitch angle | A concise leftfield electronic project with warm broken rhythms and dubby club textures | user-provided fictional example | Not an authorization to draft outreach |
| Warmer pitch angle | A patient, texture-forward project that could fit intimate rooms, radio sessions, and community-led club nights | user-provided fictional example | Keep assumption language visible |
| More formal pitch angle | A DJ / producer project positioned for leftfield electronic programming, with restrained club energy and source-backed materials pending review | user-provided fictional example | Good conservative fallback |

#### Missing / Blocked Fields

| Workflow need | Missing or blocked fields | Impact | Recommended next internal step |
| --- | --- | --- | --- |
| Required for discovery | Real/current assets; exact target priority; specific source lists if desired | Discovery can proceed broadly but should not claim proof | `skills/opportunity-discovery/SKILL.md` after profile review |
| Required for fit classification | Travel constraints; availability constraints; proof level; confirmed target priorities | Fit must be conservative | `skills/artist-profile/SKILL.md` or `skills/fit-classification/SKILL.md` if opportunity context exists |
| Required for outreach drafting | Confirmed EPK/music asset link; press photos or approved asset; safe proof claims; verified/likely contact; do-not-contact check | Outreach drafting is blocked | `skills/artist-profile/SKILL.md` |
| Required for serious booking negotiation | Fee range, availability, travel, tech/hospitality requirements, admin owner | Negotiation is blocked | `skills/approval-before-action/SKILL.md` only after human provides details and approves external use |

#### Open Questions

| Question ID | Question | Needed for | Owner | Status | Answer/source | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Q-LV-001 | Which links are real/current and approved for internal state? | EPK readiness | User | Open | Unknown | Placeholder links are example-only |
| Q-LV-002 | Are there confirmed releases, labels, bookings, radio features, or press that can be safely named? | Proof / credibility | User | Open | Unknown | Keep all proof claims unsafe until verified |
| Q-LV-003 | Are press photos, logo, live/DJ video, tech rider, or hospitality rider available? | Outreach and negotiation readiness | User | Open | Unknown | Missing assets block outreach or negotiation |
| Q-LV-004 | What travel, availability, fee, and do-not-contact constraints should be stored? | Fit, outreach, negotiation | User | Open | Unknown | Treat as sensitive/private if provided |
| Q-LV-005 | Which target markets are highest priority? | Discovery focus | User | Open | Unknown | Current target markets are unprioritized preferences |

#### Risk Register

| Risk ID | Area | Description | Risk level | Mitigation | Owner | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| RSK-LV-001 | Unverified proof | Release title, EPK link, bookings, labels, radio features, and press are not confirmed | High | Keep claims in verification bucket; do not use in outreach | User / future approved verification workflow | Open | Avoid treating placeholder links as proof |
| RSK-LV-002 | Missing outreach assets | Press photos, verified EPK/music links, video, and safe proof claims are missing or not reviewed | High | Route back to artist-profile before outreach drafting | User | Open | Profile is not outreach-ready |
| RSK-LV-003 | Sensitive/private booking constraints | Fee, availability, travel, admin contact, and do-not-contact preferences are missing or sensitive | Medium | Ask user before fit/outreach/negotiation; require approval for external use | User | Open | Do not expose by default |
| RSK-LV-004 | Overclaiming | Aspirational language could be mistaken for credibility | Medium | Use only bounded descriptive claims | Codex/OpenAI workflow | Open | Avoid "breakthrough", "viral", "sold out", and similar language |

#### Handoff Chain

| Handoff ID | Date | From | To | Workflow stage | Summary | Pending approvals | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HND-LV-001 | 2026-04-29 | `examples/booking-desk/artist-profile-intake-example.md` | `skills/artist-profile/SKILL.md` | Intake transfer | Fictional Lumen Vale intake transferred into source-hygienic booking-state fields. | None; internal state only | Resolve missing assets, proof, constraints, and open questions. |
| HND-LV-002 | 2026-04-29 | `skills/artist-profile/SKILL.md` | `skills/opportunity-discovery/SKILL.md` | Profile to discovery, conditional | Profile appears usable for broad discovery only. | None; no external action | Proceed only if user accepts broad discovery with unknown constraints and placeholder assets excluded. |

## Stop Conditions

- If artist name/project type is missing, stop and ask for Basic Identity.
- If sound/scene context is missing, do not proceed to fit classification.
- If EPK/assets are missing, do not proceed to outreach drafting.
- If proof claims are unverified, store them as claims needing verification, not safe claims.
- If booking preferences are missing, discovery can proceed only broadly and should mark target markets as unknown.
- If fee/availability/travel constraints are missing, do not use them in negotiation or outreach.

## Recommended Next Internal Skill After Transfer

Use `skills/artist-profile/SKILL.md` immediately after transfer if any profile fields, assets, proof claims, preferences, constraints, source hygiene, or readiness gates remain incomplete.

Use `skills/opportunity-discovery/SKILL.md` only when the profile has enough confirmed identity, sound/scene context, and target direction for broad discovery.

Use `skills/fit-classification/SKILL.md` only when there is a specific opportunity context and enough profile context to classify fit conservatively.

Use `skills/outreach-drafting/SKILL.md` only after outreach-critical assets, claims safe to use, contact readiness, and do-not-contact checks are clear. This fixture does not meet that gate.
