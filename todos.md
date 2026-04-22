# Income Distribution Calculator — Development Tasks

## Phase 1 — Core Build ✅

- [x] HTML skeleton
- [x] CSS design tokens + base styles
- [x] Calculator display (income input)
- [x] Calculation engine
- [x] Distribution row rendering
- [x] Inline label editing
- [x] Type toggle (% ↔ €)
- [x] Value input per row
- [x] Delete row
- [x] Add row
- [x] Retained in account row
- [x] Mobile polish

---

## Phase 2 — Completed 2026-04-13 / 14 ✅

- [x] Rename default rows — Taxes → Groceries, Business Expenses → Transport, Business Savings → Housing
- [x] All row values default to 0 (users fill in their own numbers)
- [x] All amounts show €0.00 when income field is empty
- [x] Category label dropdown — each row has a select menu with 15 preset categories (Groceries, Transport, Housing, Utilities, Savings, Taxes, Insurance, Healthcare, Entertainment, Dining Out, Clothing, Education, Subscriptions, Personal Care, Other)
- [x] New rows added via "+ Add Row" also use the category dropdown
- [x] Removed red ✕ delete buttons
- [x] Dropdown arrow moved closer to label text
- [x] Deployed to Netlify — https://paychop.netlify.app

---

## Phase 3 — Accessibility — Completed 2026-04-22 ✅

- [x] Add `<main>` landmark wrapping the app
- [x] Add `.sr-only` label for income input (`<label for>` pattern)
- [x] Switch `div[role=list]` / `div[role=listitem]` to native `<ul>` / `<li>`
- [x] Remove `aria-atomic="false"` (was causing chatty screen reader announcements)
- [x] Silence `aria-live` during full DOM rebuilds, re-enable after
- [x] Remove redundant `aria-label` on income input (kept `<label for>` instead)
- [x] Hide "auto" type badge on retained row — replaced with empty spacer
- [x] Replace deprecated `document.execCommand('selectAll')` with `.select()`
- [x] Darken focus outline on income input (`#fff` → `#1a1400` for contrast on yellow)
- [x] Add `focus-visible` states for type toggle, value input, and add-row button

---

## Phase 4 — Code Review Fixes ✅

- [x] **Delete row** — add hover-revealed ✕ button per row (replaces dead `onDeleteRow` code)
- [x] **Over-allocation feedback** — show retained amount in red + "over by €X" when allocated > income
- [x] **Clamp negatives** — `Math.max(0, ...)` in `onValueInput` to reject negative values
- [x] **Remove dead code** — `contentEditable` cursor-restore block in `render()` never runs
- [x] **Fix `nextId`** — compute from `Math.max(...rows.map(r => r.id)) + 1` instead of hardcoded `6`
- [x] **Rename `fmt`** — rename to `formatCurrency` throughout

### Review
All six fixes applied to `income-distribution.html`. Delete buttons are hidden by default and revealed on row hover (opacity 0 → 0.55, full on button hover). Over-allocation replaces the retained amount text with "over by €X" in red. Negative value clamping is a one-liner in `onValueInput`. Dead `contentEditable` block removed. `nextId` now derived from state. `fmt` renamed to `formatCurrency` at definition and all three call sites.

---

## Remaining / To Consider

- [ ] **localStorage persistence** — rows and values reset on refresh
- [ ] **Export** — CSV download of current breakdown
- [ ] **Calculation history** — log of past income entries with retained amounts
