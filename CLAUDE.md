# CircuitScout

This is the CircuitScout booking-desk workflow system for electronic music artists.

CircuitScout helps research scenes and opportunities, qualify fit, verify official contacts, draft outreach, track follow-ups, summarize replies, and maintain booking records. It is human-directed and must preserve source evidence for booking decisions.

## Mandatory: Human Approval Gates

CircuitScout is not an autonomous spam machine.

External-facing actions require explicit human approval every time. Do not send emails, accept bookings, negotiate final terms, confirm availability, commit calendar dates, or update external systems unless the user has clearly approved that specific action.

Always follow these rules:

1. Never send without human approval.
2. Never invent artist credentials.
3. Never guess private contact emails.
4. Never accept bookings.
5. Never negotiate final terms alone.
6. Never commit calendar dates.
7. Always distinguish confirmed facts from assumptions.
8. Always preserve source links.
9. Always log outreach and decisions.

## Core Workflow

Artist profile -> Market/scene research -> Opportunity discovery -> Fit classification -> Contact verification -> Outreach draft -> Human approval -> Send/log manually or via approved draft -> Inbox triage -> Follow-up queue -> Calendar/CRM update -> Retrospective

## Skills

Skills live in `skills/` and are markdown instruction files. The skills folder is still pending deeper migration from the previous Designpowers system, so do not assume those files are final CircuitScout booking skills yet.

For CircuitScout booking work, start with `skills/using-circuitscout/SKILL.md`. Use `skills/booking-state/SKILL.md` whenever a workflow needs to read, initialize, or update shared booking state.

For this migration stage, use the top-level CircuitScout instructions plus the new router and booking-state skills as the source of truth. Preserve the markdown-first workflow model: skill files, visible handoffs, direct mode, auto mode, and shared state.

## Agents

Agents live in `agents/` and are markdown role files. The agents folder is still pending deeper migration, so do not invoke old design-specific agents as if they were booking-desk specialists.

Future CircuitScout agents will cover artist profiling, market research, opportunity discovery, fit review, contact verification, outreach drafting, inbox triage, tracking, and retrospectives.

## Operating Mode

Default to direct mode for any ambiguous or external-facing step. Auto mode may be used only for internal research, summarization, classification, and drafting. Auto mode must pause before any email, booking commitment, negotiation, calendar commitment, or external system update.

## Migration Note

This repo is being reframed from Designpowers into CircuitScout. Foundation identity and packaging are CircuitScout now; deeper agents, skills, examples, and paper content are intentionally left for later migration slices.
