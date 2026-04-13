# Income Distribution Calculator — Development Tasks

## Tasks

- [x] **HTML skeleton**
  - Acceptance criteria: Valid HTML5 boilerplate; `<meta name="viewport">` for mobile; page title "Income Distribution"; no external dependencies

- [x] **CSS design tokens + base styles**
  - Acceptance criteria: All colours/sizes defined as CSS custom properties on `:root`; dark background; base reset applied; monospace font for numbers

- [x] **Calculator display (income input)**
  - Acceptance criteria: Large yellow-highlighted input field; `€` prefix visible; accepts numbers only; auto-focuses on load; all distribution rows update instantly on every keystroke (no submit button)

- [x] **Calculation engine**
  - Acceptance criteria: Given income `5000`, output is Taxes=€1500, Business Expenses=€150, Business Savings=€500, Mel payout=€250, Retained=€2600; percent rows use `income × (value / 100)`; fixed rows use the raw value; retained = income minus all other rows; retained never goes below €0

- [x] **Distribution row rendering**
  - Acceptance criteria: Each row renders label, type badge (`%` or `€`), value, and right-aligned calculated euro amount; rows are driven by the JS data array; adding/removing items in the array re-renders the list correctly

- [x] **Inline label editing**
  - Acceptance criteria: Clicking a row label makes it editable in-place; pressing Enter or clicking away saves the new label; the change persists on subsequent recalculations

- [x] **Type toggle (% ↔ €)**
  - Acceptance criteria: Clicking the type badge on a non-retained row cycles between `%` (percent) and `€` (fixed); recalculation runs immediately after toggle; retained row shows "auto" badge and is not toggleable

- [x] **Value input per row**
  - Acceptance criteria: Each non-retained row has an editable value field; changing the value instantly recalculates all amounts; retained row has no editable value field

- [x] **Delete row**
  - Acceptance criteria: Each non-retained row has a delete (×) button; clicking it removes the row and immediately recalculates retained; the retained row has no delete button

- [x] **Add row**
  - Acceptance criteria: An "+ Add Row" button appends a new row defaulting to `percent` type with value `0` and label "New Category"; new row is included in retained calculation; new row is fully editable

- [x] **Retained in account row**
  - Acceptance criteria: Always rendered last; label reads "Retained in account"; calculated amount is income minus sum of all other rows; displays €0 (not negative) if deductions exceed income; cannot be deleted or toggled

- [x] **Mobile polish**
  - Acceptance criteria: No horizontal scroll at 375px viewport width; all interactive elements have touch targets ≥ 44px; font sizes remain readable on small screens; layout does not break at any width between 320px–1440px

## Review

All tasks completed in a single `income-distribution.html` file (no dependencies, no build step).

**Architecture:** A `rows[]` array drives all state. `calculate(income)` computes each row's euro amount. `render()` rebuilds the DOM from scratch when structure changes (add/delete/toggle); `updateAmounts()` is a lightweight pass that only rewrites the euro amounts on keystroke — this keeps input focus intact while typing.

**Key decisions:**
- `updateAmounts()` used on income input and value changes (not full re-render) so focus is never interrupted mid-type
- `contentEditable` spans for labels — saves on blur or Enter; cursor is restored to end after any forced re-render
- Type toggle auto-resets value to 10% if switching from fixed and the value is 0 or > 100
- Retained row is always spliced in last; `Add Row` inserts before it
- `Math.max(0, ...)` prevents retained from going negative
- German locale (`de-DE`) used for number formatting to match Euro conventions (e.g. `1.500,00`)
