---
name: Gmail drafts always HTML
description: All Gmail drafts and emails must use contentType text/html, never text/plain
type: feedback
---

Gmail drafts must ALWAYS be created with contentType "text/html", never "text/plain".

**Why:** Plain text drafts break formatting in Mail.app (mailsuite) and look unprofessional. User needs HTML for proper rendering across email clients.

**How to apply:** Every single gmail_create_draft call must include `contentType: "text/html"` and the body must be proper HTML with `<br>` for line breaks, `<b>` for bold, `<ul>/<li>` for lists, `<hr>` for dividers, etc.
