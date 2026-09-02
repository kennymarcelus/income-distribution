# Paychop — Task Log

## Completed Today

- [x] Light theme UI overhaul (Bruno-inspired) — tokens, card surfaces, type buttons
- [x] Centered layout and header card (max-width 680px, margin auto)
- [x] PAYCHOP branding — dark charcoal header (#1c1c1e), yellow underline on title
- [x] "Total Income" label on yellow income card
- [x] Category dropdown with "Other (custom...)" option — swaps to text input on select
- [x] Swipe-to-delete on mobile rows (reveals red Delete button, 80px reveal)
- [x] Hide × delete button on touch devices (hover: none + pointer: coarse media query)
- [x] Sticky header implementation — .sticky-top + .scroll-area wrappers added
- [x] iOS scroll containment fixes — html height: 100%, body align-items: stretch, .app min-height: 0
- [x] Netlify auto-deploy confirmed active (push to main triggers deploy)

---

## In Progress

- [ ] **Sticky header broken when rows are added on iOS**
  - Root cause identified: flex containment chain (`html → body → .app → .scroll-area`)
  - Fixes applied: `html { height: 100% }`, `body { align-items: stretch }`, `.app { min-height: 0 }`
  - Issue may persist on iOS Safari due to its known `overflow: hidden` quirks on body/html
  - Needs live device testing and further investigation next session

---

## TODO — Next Session

- [ ] Fix sticky header scroll containment on iOS completely
- [ ] App icon design
- [ ] App Store screenshots
- [ ] App Store Connect listing setup
- [ ] IAP (In-App Purchase) implementation
- [ ] Submit to App Store
