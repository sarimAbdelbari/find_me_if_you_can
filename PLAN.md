# Plan — Find Me If You Can (working title)

## One-liner

Android-first anti-theft tooling: **recover and protect** a stolen phone using **PIN-backed lock**, optional **remote triggers via SMS** when data is off, and **richer tracking when online**.

## Problem

Phone theft / burglary: once the device is gone, the owner needs **ways to locate**, **limit misuse**, and **use cellular fallback** when internet is disabled.

## Guiding principles

1. **Honest limits** — SIM removed, factory reset, airplane mode, or power off ends guarantees; the product should say so clearly.
2. **Owner-only control** — secret passphrase + trusted numbers; no anonymous remote triggers.
3. **Legitimate anti-theft posture** — transparent install/setup; avoid patterns associated with spyware or ransomware.

## Scope (current)

| In scope | Out of scope (for now) |
|----------|-------------------------|
| Android app | iOS |
| PIN-backed lock behavior | Promising impossible recovery when phone is wiped/off |
| SMS as trigger channel (Sprint 2+) | |

## Architecture direction (conceptual)

- **Device lock / boot behavior** — Sprint 1 (Android APIs and UX for lock-after-boot).
- **SMS receiver + trusted sender + secret** — Sprint 2.
- Later: location replies, enabling location/mobile data where OS allows, optional eSIM guidance in onboarding copy.

## Risks and constraints

- **Google Play policies** restrict abusive device admin / lock misuse; implementation must follow **documented anti-theft** patterns.
- **OEM differences** — power menu, lock screen, and background limits vary by manufacturer.
- **Dual connectivity** — physical SIM + eSIM can improve odds but doesn’t remove all failure modes.

## Related docs

- `chating.md` — informal brainstorm and threads.
- `Sprints.md` — sprint goals and acceptance criteria.
