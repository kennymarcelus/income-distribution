# Income Distribution Calculator

A clean, minimal calculator for freelancers to instantly see where their money goes. Type in your income and it splits automatically into taxes, expenses, savings, payouts, and whatever's left over — no buttons, no page reloads.

---

## What it looks like

```
INCOME DISTRIBUTION

  € 5000

  Taxes               %   30    €1.500,00
  Business Expenses   €  150      €150,00
  Business Savings    %   10      €500,00
  Mel payout          €  250      €250,00
  ─────────────────────────────────────────
  Retained in account          €2.600,00

  + Add Row
```

---

## Setup

No installs. No build step. No internet connection required.

1. Download or clone this repository
2. Open `income-distribution.html` in any web browser (Chrome, Firefox, Safari, Edge)

That's it — you're done.

```bash
# If you cloned with git:
git clone https://github.com/kennymarcelus/income-distribution.git
cd income-distribution
open income-distribution.html
```

> On Windows, double-click the file in File Explorer. On Mac, you can also right-click → Open With → your browser.

---

## Features

**Instant calculation**
Type your income and every row updates in real time — no submit button needed.

**Two row types**
- `%` — percentage of your income (e.g. 30% for taxes)
- `€` — a fixed euro amount (e.g. €250 flat fee)

Click the `%` or `€` badge on any row to switch between the two.

**Retained in account**
The bottom row always shows what's left after all deductions. It updates automatically and can never go below €0.

**Fully editable rows**
- Click any category name to rename it
- Change the `%` or `€` value at any time
- Delete a row with the `×` button

**Add custom rows**
Click `+ Add Row` to add a new category. It starts as a percentage row — rename it and set the value you need.

**Mobile friendly**
Works on phones and tablets. All buttons are large enough to tap comfortably.

**Accessible**
Keyboard navigable and compatible with screen readers (WCAG AA).

---

## Default categories

| Category | Type | Value |
|---|---|---|
| Taxes | % | 30 |
| Business Expenses | € fixed | 150 |
| Business Savings | % | 10 |
| Mel payout | € fixed | 250 |
| Retained in account | auto | — |

You can rename, edit, add, or delete any of these (except "Retained in account").

---

## Example usage

**Scenario: You invoiced €5,000 this month**

Enter `5000` in the yellow field. The calculator immediately shows:

| Category | Calculation | Result |
|---|---|---|
| Taxes | 5000 × 30% | €1,500.00 |
| Business Expenses | fixed | €150.00 |
| Business Savings | 5000 × 10% | €500.00 |
| Mel payout | fixed | €250.00 |
| **Retained in account** | 5000 − 2400 | **€2,600.00** |

**Scenario: You want to add a pension contribution**

1. Click `+ Add Row`
2. Click the label "New Category" and type `Pension`
3. Make sure the badge shows `%`, then set the value to `5`
4. All rows recalculate instantly — the retained amount drops accordingly

**Scenario: A row should be a flat fee instead of a percentage**

Click the `%` badge on that row. It switches to `€` and the value is now treated as a fixed euro amount.

---

## File structure

```
income-distribution/
├── income-distribution.html   # The entire app — open this in your browser
├── todos.md                   # Development task checklist
└── README.md                  # This file
```

Everything lives in a single HTML file. There are no external dependencies, no JavaScript frameworks, and no CSS libraries.

---

## Browser support

Works in any modern browser released in the last 3–4 years:

- Chrome / Edge 90+
- Firefox 90+
- Safari 14+
