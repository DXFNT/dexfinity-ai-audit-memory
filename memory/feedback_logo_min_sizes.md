---
name: Dexfinity logo minimum sizes
description: Mandatory minimum heights for Dexfinity logo in all outputs — nav 48px, footer 64px, hero 80px. The "Go Beyond" tagline becomes unreadable below 48px.
type: feedback
---

Dexfinity logo MUST meet these minimum height requirements in all outputs:

- **Nav / header:** min 48px (was 42px, user flagged as too small)
- **Footer:** min 64px (brand anchor, must be prominent)
- **Hero / feature placement:** min 80px
- **Mobile nav:** min 36px
- **Mobile footer:** min 48px
- **Email header:** min 48px

**Why:** The Dexfinity logo includes the "Go Beyond" tagline underneath. At 42px or smaller, the tagline is unreadable — defeats the purpose of brand reinforcement. The logo is the last thing the client sees (footer) and first thing (nav), so it must be clear and professional.

**How to apply:** Every HTML output (audits, landing pages, emails, presentations) must use these minimums. When writing CSS for `.nav-logo` or `.footer-logo`, always set height to at least 48px/64px respectively. Add a comment `/* min Xpx — brand guideline */` to prevent regression.
