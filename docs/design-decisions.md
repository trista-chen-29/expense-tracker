# Design Decisions

## Focus on Friction Reduction Over Feature Count
The project prioritizes reducing the effort required to log an expense rather than adding many features.
Many existing expense trackers fail because they are too slow or complex for daily use.

Tradeoff: fewer features compared to full finance apps.
Alternative considered: feature-rich tracker with budgets and reports.

---

## User-Specific Categories with Preset Defaults
Categories are scoped per user to allow personalization and accurate modeling of individual spending habits.
To reduce friction during expense entry, each user is initialized with a predefined set of common categories
(e.g., Food, Transport, Rent) at onboarding.

This preserves fast default behavior while allowing users to customize categories over time.

Tradeoff: requires onboarding logic to create default categories per user.
Alternative considered: fully global categories shared across all users.

---

## Quick-Add First Design
A one-line quick-add input is treated as a primary interaction, not an optional shortcut.
This supports fast logging with minimal UI interaction.

Tradeoff: requires custom parsing logic and error handling.
Alternative considered: form-based entry only.

---

## Human-in-the-Loop Inbox
Ambiguous or auto-detected expenses are routed to an Inbox instead of being saved directly.
This prevents incorrect data from entering the system while still enabling fast workflows.

Tradeoff: adds an extra confirmation step in some cases.
Alternative considered: auto-save everything and allow edits later.

---

## Rule-Based Merchant Memory Instead of ML
Merchant-to-category mapping is implemented using simple rule-based memory rather than machine learning.
This provides predictable behavior, easy debugging, and transparency.

Tradeoff: less flexible than ML-based classification.
Alternative considered: ML auto-categorization from the start.
