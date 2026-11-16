# ♿ Accessibility Review

This checklist is a practical review baseline, not an accessibility conformance claim.

## Perceivable
- [ ] Text contrast meets target ratios.
- [ ] Color is not the only means of conveying score/status.
- [ ] Important icons/images have accessible names.
- [ ] Charts expose a text summary/table.
- [ ] Dynamic status/errors are announced.
- [ ] Map results are available in a non-map list.

## Operable
- [ ] Main navigation keyboard accessible.
- [ ] Focus order follows user tasks.
- [ ] Visible focus indicator exists.
- [ ] Dialogs trap and restore focus correctly.
- [ ] Menus, tabs, selects and accordions follow keyboard expectations.
- [ ] Motion can be reduced.
- [ ] No keyboard traps.

## Understandable
- [ ] Every field has a visible/programmatic label.
- [ ] Required fields and formats are described.
- [ ] Validation points to the affected control.
- [ ] Scores, units, currency and forecast horizon are explicit.
- [ ] Button names make actions clear.

## Robust
- [ ] Semantic landmarks and headings are used.
- [ ] ARIA complements native semantics instead of duplicating them.
- [ ] Loading, toast and result announcements are useful.
- [ ] Radix/shadcn primitives retain expected behavior.

## Feature-specific review

### Location search
- [ ] Suggestions are keyboard reachable.
- [ ] Selection result is announced.
- [ ] Search status is exposed.

### Maps/heatmaps
- [ ] Map is not the only way to discover important results.
- [ ] Text/table alternative exists.
- [ ] Attribution and map controls are accessible.

### Reports/charts
- [ ] Tabs are keyboard-operable.
- [ ] Score values are expressed as text.
- [ ] Chart trends have descriptions.
- [ ] Red/green status has textual meaning.

### Auth forms
- [ ] Password controls have accessible labels.
- [ ] Errors are associated with inputs.
- [ ] Focus moves to relevant errors.
- [ ] Session/loading state is announced.

Use axe checks plus keyboard-only and screen-reader testing. Record browser, OS, assistive technology and defects.
