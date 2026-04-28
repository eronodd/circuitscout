# CircuitScout Booking Desk Examples

These files are templates and fixtures for testing and using CircuitScout's booking workflow. They are not live data, not real outreach, and not connector behavior.

## Recommended First-Use Order

1. `artist-profile-intake.md`
2. `intake-to-booking-state-transfer.md`
3. `booking-state.md`
4. `manual-lead-workflow-example.md` or `limited-prefit-manual-lead-example.md` depending on readiness

## Example Index

| File | Purpose | When to use it | Next likely skill/workflow step |
| --- | --- | --- | --- |
| `booking-state.md` | Canonical shared state template for ongoing CircuitScout projects. | Starting or maintaining a full booking workflow. | Use `skills/booking-state/SKILL.md`. |
| `artist-profile-intake.md` | Compact first-use artist intake. | The user is starting a new artist/project and does not want to fill full booking-state yet. | Use `intake-to-booking-state-transfer.md`. |
| `artist-profile-intake-example.md` | Fictional completed artist intake fixture. | Testing how source hygiene, assumptions, unknowns, and missing fields should look. | Use `intake-to-booking-state-transfer.md`. |
| `intake-to-booking-state-transfer.md` | Checklist for transferring compact intake into canonical booking-state. | A compact intake has been completed and should become canonical project state. | Use `skills/booking-state/SKILL.md`, then `skills/opportunity-discovery/SKILL.md` if ready. |
| `manual-lead-workflow-example.md` | Fixture showing a manual lead flowing through discovery, fit, contact verification, and stop conditions. | Testing the normal manual lead workflow with enough context. | Use `skills/opportunity-discovery/SKILL.md`, then `skills/fit-classification/SKILL.md`. |
| `limited-prefit-manual-lead-example.md` | Fixture showing a narrow/incomplete manual lead that must stop at Limited Pre-Fit Review. | Testing readiness guards and preventing premature scoring/outreach. | Return to `skills/artist-profile/SKILL.md` or booking-state transfer before full `skills/fit-classification/SKILL.md`. |

## Safety Reminders

- Examples are not live data.
- Do not treat fictional contacts, venues, artists, or links as real.
- Do not send outreach from examples.
- Do not perform connector actions from examples.
- Preserve source hygiene.
- Do not produce full fit scores from limited pre-fit examples.
- External actions always require approval-before-action.
