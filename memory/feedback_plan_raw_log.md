---
name: plan.html — raw log rule
description: After each answered question in plan.html, always add a collapsible <details> with the user's original unedited voice input as a grey log
type: feedback
---

Under every filled answer in plan.html, add a `<details>` / `<summary>` block with the user's raw, unedited input.

**Why:** User wants to keep the original voice transcript as a log alongside the structured answer. The structured answer can change; the log preserves the source.

**How to apply:**
- Summary label: "Оригінал (голос)"
- Content: user's exact words, inside `<div class="raw">`, no editing
- Always do this when saving a new answer to plan.html
- Also add to plan.md as a `> *Оригінал:* ...` blockquote under the section if maintaining parity
