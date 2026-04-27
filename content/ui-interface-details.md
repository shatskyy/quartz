---
title: Details That Make Interfaces Feel Better
date: 2026-04-27
tags: [design, concept]
status: evergreen
description: "A collection of micro-level UI/UX decisions — feedback, motion, typography, hover states — that separate functional interfaces from polished ones."
---

# Details That Make Interfaces Feel Better

Small, considered details are what separate interfaces that merely *work* from interfaces that feel *right*. This note collects the micro-level decisions that compound into a polished experience.

Source: [Details that make interfaces feel better](https://jakub.kr/writing/details-that-make-interfaces-feel-better) by Jakub

---

## Feedback & Responsiveness

Every user action deserves an immediate acknowledgment. Even if an operation takes time, the interface should respond *instantly* to confirm the input was received.

- Buttons should show a pressed/active state on click, not just on hover.
- Form submissions should disable the submit button and show a loading indicator to prevent double-submits.
- Optimistic UI updates (showing the result before the server confirms) dramatically improve perceived speed.

---

## Motion & Transitions

Animation should communicate, not decorate.

- Use **easing curves** rather than linear transitions — `ease-out` for elements entering, `ease-in` for elements leaving.
- Keep durations short: 150–250ms for micro-interactions, 300–400ms for layout shifts.
- Avoid animating opacity alone; pairing it with a small translate (`translateY(-4px)`) creates a more natural sense of depth.
- Respect `prefers-reduced-motion` — always provide a no-animation fallback.

---

## Typography & Spacing

Consistent rhythm makes layouts feel intentional rather than accidental.

- Use a **spacing scale** (4px, 8px, 16px, 24px…) — mixing arbitrary values creates visual noise.
- Line-height for body text should be ~1.5–1.6; tighter for headings (~1.1–1.2).
- Avoid full-width text blocks on wide viewports — cap line length at ~65–75 characters (`max-width: 65ch`).
- Letter-spacing on all-caps labels (+0.05–0.1em) improves readability without shouting.

---

## Hover & Cursor States

Cursor changes are an underused affordance signal.

- Use `cursor: pointer` for clickable elements; `cursor: grab` / `cursor: grabbing` for drag targets.
- Hover states should subtly preview the action — a delete button turning red on hover sets expectation before commitment.
- Don't only rely on color to communicate hover; pair it with a background fill or underline so it works for color-blind users.

---

## Loading & Empty States

Blank screens and spinners are missed opportunities.

- **Skeleton screens** (grey placeholder shapes matching the expected layout) reduce perceived load time more than generic spinners.
- Empty states should explain *why* there's nothing and offer a clear next action (e.g., "No notes yet — [[quartz-obsidian-wiki-setup|create your first one]]").
- Progress indicators for long operations should show steps or percentage where possible.

---

## Error & Validation

Errors should be helpful, not punishing.

- Validate inline and progressively — don't wait for form submission to tell the user their email is malformed.
- Error messages should say what went wrong *and* how to fix it. "Invalid input" is useless; "Email must include an @ symbol" is actionable.
- Preserve entered data on error — never clear a form because one field failed.

---

## Accessibility Details

Polish and accessibility overlap more than they conflict.

- Focus rings should be visible and styled (not the default `outline: none` anti-pattern). Use `:focus-visible` to show rings only for keyboard navigation.
- Touch targets should be at least 44×44px regardless of the visual size of the element.
- `aria-live` regions let screen readers announce dynamic content changes (toasts, counters, status updates) without requiring focus.

---

## Related

- [[System-Architecture]] — The infrastructure this wiki runs on, itself an example of deliberate design choices.
- [[quartz-obsidian-wiki-setup]] — The PKM philosophy that informs this vault's UX.
