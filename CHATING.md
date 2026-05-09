# Chating — brainstorm log

Informal notes from design conversations. Think of this as the scratchpad thread next to formal docs in `PLAN.md` and `Sprints.md`.

---

## Problem we’re solving

Burglary / phone theft: recover or protect the device when it’s no longer in your hands.

---

## Core idea (early shape)

- **SMS as a trigger** when the stolen phone has **no internet** (mobile data/Wi‑Fi off). Owner sends an SMS to their own number → app reacts (e.g. reply with location, enable radios, etc.).
- **When data is available**, support **live location** (or richer updates); SMS path is the **offline fallback**.
- **eSIM** considered as a backup so removing the physical SIM doesn’t instantly kill cellular/SMS (still not bulletproof: airplane mode, wipe, power off, eSIM disabled in settings).

---

## Security / privacy (must-haves)

- **Secret passphrase** set inside the app — not a public trigger.
- **Trusted phone numbers** — only messages from allowlisted senders + correct secret can trigger sensitive actions (location reply, remote lock, etc.).

---

## “Lock the phone down” thread

- Goal: remote **lock** so **nothing works without PIN** — in practice this aligns with **locking to the OS lock screen** (same family as Find My Device lock), not “disable power button forever.”
- Thieves can often **force power off** from hardware; **design for the window while the phone is on**.
- Avoid anything that reads as **ransomware**; recovery must be clearly **owner-initiated** with transparent setup.

---

## Platform

- **Android only** for the foreseeable scope (SMS-triggered behavior and device lock APIs don’t map cleanly to iOS).

---

## Sprint direction (agreed)

1. **Sprint 1:** App that **locks on boot** (when device turns on); **unlock only with PIN** — see `Sprints.md`.
2. **Sprint 2:** **SMS-triggered** behavior — see `Sprints.md`.

We iterate after those land.

---

## Open threads (for later)

- Exact MVP promise wording (honest limits: SIM out, wipe, radio off).
- Whether location goes **SMS-only**, **live after data on**, or both — already sketched; detail when implementing Sprint 2+.
- Optional hardening: rate limits, cooldown after failed secret attempts.
