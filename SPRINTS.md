# Sprints

Execution order and **definition of done** for each slice. Android only unless noted.

---

## Sprint 1 — Lock on boot, unlock with PIN

**Goal:** When the user turns the device on (completes boot), the app ensures the phone is **usable only after the correct PIN** (aligned with the device’s secure lock screen / app-defined unlock flow — exact mechanism pinned during implementation).

**Intent:** Establish the **baseline security posture** before adding remote SMS triggers.

### Acceptance criteria (draft)

- [ ] After boot, user cannot access the device without completing the required PIN/unlock step configured by the app flow.
- [ ] Wrong PIN behavior is defined (retry limits, lockout policy — align with Android norms and UX safety).
- [ ] User can set or change PIN inside the app (or clearly documented integration with system screen lock — decision recorded in repo when implemented).
- [ ] Basic onboarding: explain why boot lock matters for anti-theft.

### Notes

- Clarify during implementation: **custom full-screen lock** vs **deferring to system lock screen** after `BOOT_COMPLETED` — both are valid; pick one consistent story for Sprint 2 SMS triggers.

---

## Sprint 2 — Trigger via SMS

**Goal:** A defined **incoming SMS** (from **trusted numbers** only, with **secret phrase** if applicable) triggers app behavior — starting with the smallest safe action (e.g. acknowledge, log event, or lock — exact command set to list here before coding).

**Depends on:** Sprint 1 stable enough that SMS handler can run in background policy on target Android versions.

### Acceptance criteria (draft)

- [ ] User configures **trusted phone number(s)** in the app.
- [ ] User configures **secret** (passphrase) for validation.
- [ ] Incoming SMS from non-trusted numbers does **not** trigger sensitive actions.
- [ ] Wrong secret does not trigger actions (and optionally rate-limits — TBD).
- [ ] Document Android **SMS/receiver permissions** and Play Store disclosure requirements.

### Follow-on (post–Sprint 2, not committed as numbered sprint yet)

- SMS reply with **location snapshot**; enable **location + mobile data** where OS allows.
- **Remote lock** via SMS (same trust + secret model).
- Optional **live location** when data is available.

---

## How we use this file

Update checkboxes and notes as sprints complete. Add Sprint 3+ when the next slice is agreed.
