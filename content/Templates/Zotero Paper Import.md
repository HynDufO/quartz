---
aliases: 
- "{{title}}"
tags: [🗃️/📜/🔵]
type: Paper
status: 🔵
date-created: {{exportDate | format("YYYY-MM-DD")}}
date-start: 
date-end:

pages: {{numPages}}
rating: 
---

# 📜 {{title}} - {{date | format("YYYY")}}

> [!cite]+ Metadata
> - `Topics`: 
> - `Date Created`: [[{{exportDate | format("YYYY-MM-DD")}}]]
> - `Citekey`:: {{citekey}}
> - `Author`: {{authors}}
> - `Publisher`: {{publisher}}
> - `Attachments`:: [[]]
> - `Reading Device`:: Zotero
> - `Bibliography`: {{bibliography}}
> - `Published Year`: {{date | format("YYYY")}}
> - `Related`:
{% if abstractNote %}

> [!abstract]+ Abstract
> {{abstractNote}}

{% endif %}
## Main

> [!tip]- Tip
> ![[Highlight Colors Meaning For References#Main]]
> - If the paper is too long, see [[📚 Book Template]] tip.

> [!faq]+ Table of contents
> - ...

## Review

## Reflect
- - [ ] Go through your Main, consider making new notes, Anki cards and life improvements.
- - [ ] Link related papers, notes, arguments, references to the **Related** metadata above.
- - [ ] Assign 🛎️ for reviewing.
