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

## Remaining / To Consider

- [ ] **Delete row** — now that the ✕ button is gone, there is no way to remove a row. Consider a long-press, swipe, or subtle icon on hover
- [ ] **localStorage persistence** — rows and values reset on refresh; could be useful to save state
- [ ] **Export** — CSV download of current breakdown
- [ ] **Calculation history** — log of past income entries with retained amounts
