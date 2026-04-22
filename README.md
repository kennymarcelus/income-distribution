# Income Distribution Calculator

A clean, minimal calculator for anyone who wants to see where their money goes. Enter your income or salary and it splits automatically across categories like housing, groceries, savings, and more — no buttons, no page reloads.

---

## What it looks like

```
INCOME DISTRIBUTION

  € 3000

  Groceries    %   15    €450.00
  Transport    €  120    €120.00
  Housing      %   35  €1,050.00
  Other        €   80     €80.00
  ─────────────────────────────────
  Retained in account  €1,300.00

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
Type your income or salary and every row updates in real time — no submit button needed.

**Two row types**
- `%` — percentage of your income (e.g. 35% for housing)
- `€` — a fixed euro amount (e.g. €120 flat transport cost)

Click the `%` or `€` badge on any row to switch between the two.

**Retained in account**
The bottom row always shows what's left after all deductions. It updates automatically and turns red if your allocations exceed your income.

**Preset category dropdown**
Each row has a dropdown with 15 common personal finance categories to choose from: Groceries, Transport, Housing, Utilities, Savings, Taxes, Insurance, Healthcare, Entertainment, Dining Out, Clothing, Education, Subscriptions, Personal Care, and Other.

**Add custom rows**
Click `+ Add Row` to add a new category. Pick a label from the dropdown and set the value you need.

**Delete rows**
Hover over any row and click the `×` button to remove it.

**Mobile friendly**
Works on phones and tablets. All buttons are large enough to tap comfortably.

**Accessible**
Keyboard navigable and compatible with screen readers (WCAG AA).

---

## Default categories

| Category | Type | Value |
|---|---|---|
| Groceries | % | 0 |
| Transport | € fixed | 0 |
| Housing | % | 0 |
| Other | € fixed | 0 |
| Retained in account | auto | — |

All rows start at 0 so you can set your own values. You can add, remove, or change any row except "Retained in account".

---

## Available category labels

When adding or changing a row, choose from:

Groceries · Transport · Housing · Utilities · Savings · Taxes · Insurance · Healthcare · Entertainment · Dining Out · Clothing · Education · Subscriptions · Personal Care · Other

---

## Example usage

**Scenario: Divide a €3,000 monthly salary**

Enter `3000`. Then set up rows to reflect your actual spending:

| Category | Type | Value | Result |
|---|---|---|---|
| Groceries | % | 15 | €450.00 |
| Transport | € | 120 | €120.00 |
| Housing | % | 35 | €1,050.00 |
| Savings | % | 10 | €300.00 |
| **Retained in account** | auto | — | **€1,080.00** |

**Scenario: You spend over your income**

If the total of your rows exceeds your income, the "Retained in account" row turns red and shows "over by €X.XX" so you can see exactly how much you need to cut.

**Scenario: Switch a row from percentage to fixed**

Click the `%` badge on any row. It flips to `€` and the value is now treated as a fixed euro amount rather than a share of your income.

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
