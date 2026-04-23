---
name: Gmail signature in every draft
description: Always append Pavol's Gmail signature to every draft, Gmail API doesn't add it automatically
type: feedback
---

Gmail API does not auto-append the user's signature. ALWAYS include it manually at the end of every draft.

**Why:** Drafts created via API look unprofessional without the signature. User expects it to match what Gmail normally generates.

**How to apply:** Read the signature template from `/Users/pavoladamcak/Documents/Claude/Email NL Forward mailing/signature.html` and append it after `<br><br>` at the end of every gmail_create_draft body. This file contains the full HTML table with Calendly link, Dexfinity logo, name, title, phone, website, office locations, social icons, and disclaimer.

Also: NEVER use `<hr>` tags or visible separator lines in email drafts. Use `<br>` spacing only.
