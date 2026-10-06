# OSMOO UI/UX Specification

## Information architecture
Top-level navigation: Product, Capabilities, Security, Pricing, Skills, Developers, Download, Account.

## Global states
Every async action requires loading, success, recoverable error, terminal error, disabled, and permission-denied states.

## Forms
Use server-side validation as authoritative. Client validation improves UX but never replaces server validation.

## Account UX
Show active sessions, billing state, entitlement state, download compatibility, and security settings.

## Admin UX
No security-by-hidden-route. Admin pages must visibly communicate privilege level, require confirmation for destructive operations, and show audit context.

## Error UX
Never expose internal exceptions. Show actionable user-safe errors and request IDs.

## Accessibility
Semantic landmarks, labels, keyboard focus, logical tab order, reduced-motion mode, contrast, accessible dialogs, and screen-reader announcements.

## Responsive behavior
Desktop-first cinematic layouts must collapse to touch-safe mobile controls without hiding critical account/security actions.

## Loading
Use skeletons only when structure is known. Avoid endless spinners; use timeout/error states.

## Security UX
Explain why an action is blocked instead of silently failing. Sensitive actions should show the target and consequences before confirmation.
