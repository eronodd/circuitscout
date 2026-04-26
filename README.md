# CircuitScout

CircuitScout is a human-directed AI booking desk for electronic music artists.

It helps an artist or artist team research scenes, discover booking opportunities, qualify fit, find official contact paths, draft personalized outreach, track follow-ups, monitor replies, update booking records, and prepare calendar reminders.

CircuitScout is markdown-first: its operating model lives in repo instructions, skills, agents, handoffs, direct mode, auto mode, and shared state. This repository is currently being reframed from Designpowers into CircuitScout, so the foundation identity is CircuitScout while the deeper agents, skills, examples, and paper content still need migration.

## What CircuitScout Is

CircuitScout is a guided research and booking-operations workflow for electronic music outreach.

It can:

- Build and maintain an artist profile for booking research.
- Research markets, scenes, festivals, clubs, promoters, showcases, collectives, radio shows, and event series.
- Discover opportunities and preserve source links.
- Classify fit using explicit criteria.
- Verify official contact paths from public sources.
- Draft personalized outreach for human review.
- Summarize inbox replies and prepare next-step recommendations.
- Maintain follow-up queues, CRM/spreadsheet state, and calendar reminder proposals after approval.
- Run in direct mode, where each handoff waits for human direction.
- Run in auto mode for internal research and preparation, while pausing before external-facing actions.

## What CircuitScout Is Not

CircuitScout is not an autonomous spam machine.

It must not:

- Send emails without explicit human approval.
- Invent artist credentials, press quotes, relationships, support slots, streaming numbers, or availability.
- Guess private contact emails.
- Accept bookings.
- Negotiate final terms alone.
- Confirm fees, holds, travel, hospitality, or billing details alone.
- Commit calendar dates.
- Treat assumptions as confirmed facts.
- Perform scraping, API use, inbox actions, calendar actions, CRM writes, or external automations unless a later approved slice explicitly implements and scopes those actions.

## Core Workflow

```text
Artist profile
-> Market/scene research
-> Opportunity discovery
-> Fit classification
-> Contact verification
-> Outreach draft
-> Human approval
-> Send/log manually or via approved draft
-> Inbox triage
-> Follow-up queue
-> Calendar/CRM update
-> Retrospective
```

## Human Approval Rules

CircuitScout can research, classify, draft, summarize, prepare actions, and maintain tracking state. External-facing actions require explicit human approval every time.

- Never send without human approval.
- Never invent artist credentials.
- Never guess private contact emails.
- Never accept bookings.
- Never negotiate final terms alone.
- Never commit calendar dates.
- Always distinguish confirmed facts from assumptions.
- Always preserve source links.
- Always log outreach and decisions.

## Architecture

CircuitScout keeps the existing markdown-first architecture:

- `CLAUDE.md` and `GEMINI.md` provide top-level activation instructions.
- `.claude-plugin/` and `gemini-extension.json` provide package and extension metadata.
- `hooks/session-start` injects the top-level CircuitScout instructions into new Claude sessions.
- `agents/` will hold specialist roles for research, qualification, contact verification, outreach drafting, inbox triage, tracking, and retrospectives.
- `skills/` will hold workflow instructions that agents and models can read directly.
- Handoffs keep work visible and reviewable between stages.
- Direct mode pauses for human approval at each handoff.
- Auto mode may prepare internal research and drafts, but must still pause before external-facing actions.
- Shared state will track artist profile facts, opportunity records, sources, outreach history, decisions, and next actions.

## Current Migration Status

This repo has been reframed at the foundation layer only.

Updated in this slice:

- Project README and public identity.
- Claude and Gemini activation instructions.
- Package, Claude plugin, marketplace, and Gemini extension metadata.
- Session-start activation hook.

Pending migration:

- Full `agents/` folder content.
- Full `skills/` folder content.
- Examples and walkthroughs.
- Paper and explanatory material.
- Booking-specific shared state templates.
- Fit-classification framework.
- CRM/spreadsheet workflows.
- Gmail, Calendar, Sheets, API, scraping, and automation integrations.

Designpowers-specific files may still exist inside deeper folders until those migration slices happen. They are intentionally not deleted or bulk-renamed in this foundation pass.

## Planned Next Slices

1. Define the CircuitScout shared state model for artist profile, opportunity records, source evidence, outreach log, follow-up queue, and decision history.
2. Migrate the top-level router skill into a CircuitScout workflow router.
3. Replace design agents with booking-desk agents for scene research, opportunity discovery, fit review, contact verification, outreach drafting, inbox triage, CRM updates, and retrospectives.
4. Add fit-classification criteria for electronic music bookings.
5. Add example workflows for festivals, clubs, showcases, radio shows, and collectives.
6. Add integration plans for Gmail, Calendar, Sheets, and CRM workflows with explicit human-approval gates.
7. Review all paper and documentation content for remaining Designpowers language.

## Installation

### Claude Code

```bash
git clone https://github.com/eronodd/circuitscout.git
cd circuitscout
```

The `CLAUDE.md` file and `.claude/settings.json` configure CircuitScout activation for Claude Code sessions.

### Gemini CLI

```bash
git clone https://github.com/eronodd/circuitscout.git
cd circuitscout
gemini
```

Gemini CLI auto-loads `GEMINI.md` from the working directory. The top-level `gemini-extension.json` manifest makes this installable as a Gemini CLI extension once packaging is ready.

## License

MIT License. See `LICENSE` for details.
