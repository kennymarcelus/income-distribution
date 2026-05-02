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

## Phase 5 — Power User Upgrades

- [x] **1. localStorage persistence** — save `rows` + income value to `localStorage` on every change; restore on page load. User's budget survives refresh and is there waiting for them every visit.
- [x] **2. Visual allocation bars** — thin colored bar inside each row showing that row's % share of total income. Instant visual understanding of where money flows.
- [x] **3. Implicit % display for fixed rows** — rows set to fixed € show a small secondary label like `· 30%` so users always know the income share without mental math.
- [x] **4. Monthly ↔ Annual toggle** — a small toggle near the income input. Enter monthly income, flip to see all amounts annualized (×12). Or enter annual and see monthly breakdowns.
- [x] **5. Preset templates** — a "Start from a template" button offering: 50/30/20 (Needs/Wants/Savings), Zero-Based (all rows sum to 100%), Blank. Gives new users a meaningful starting point.

### Priority order
1 → 2 → 3 → 4 → 5 (each is independent; can ship one at a time)

### Review — Phase 5
All five power-user upgrades shipped to `income-distribution.html`:

1. **localStorage persistence** — `saveState()` / `loadState()` round-trip `rows`, `income`, and `viewMode` on every change. Corrupt data fails silently and starts fresh.
2. **Visual allocation bars** — 3px bar absolutely positioned at the bottom of each row; yellow for % rows, green for fixed/retained. Width animates via CSS transition; updates live as income changes.
3. **Implicit % for fixed rows** — `.row-amount` is now a two-span flex column: main amount on top, small muted percentage below (only for fixed rows when income > 0).
4. **Monthly ↔ Annual toggle** — `Mo / Yr` segmented pill top-right. Multiplies all displayed amounts ×12 in Annual mode; bars and implicit % unaffected (ratio-based). Persisted in localStorage.
5. **Preset templates** — `Quick start: [50/30/20] [Zero-Based]` strip above Add Row. 50/30/20 loads 6 pre-configured % rows totalling 100%. Zero-Based loads a single blank row. Both assign fresh IDs and re-render.

---

## Remaining / To Consider

- [ ] **Export** — CSV or plain-text copy of current breakdown
- [ ] **Custom free-text labels** — let users type their own category name instead of dropdown-only
- [ ] **Drag to reorder rows**
