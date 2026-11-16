# ♿ Accessibility statement and project checklist

Accessibility is a quality requirement for the static frontend, documentation, and future analytical visualizations. This file describes the project's intended practices. It does not claim that the current website has completed a formal conformance audit.

## Current scope

The repository contains static HTML/CSS pages under `Frontend/`. Accessibility should be checked in the actual browser rendering, not inferred from source formatting alone. Any future interactive chart or data table should have an accessible alternative.

## Requirements for contributors

- Use semantic HTML landmarks and a logical heading hierarchy.
- Ensure all interactive controls work by keyboard.
- Maintain visible focus indicators.
- Provide descriptive alternative text for informative images.
- Give icon-only controls accessible names.
- Associate form controls with visible labels and clear error messages.
- Maintain sufficient contrast and never use colour as the only signal.
- Support browser zoom and narrow viewports.
- Use descriptive link text.
- Give charts titles, labels, denominators, and text summaries.

## Verification checklist

- [ ] Keyboard-only navigation works.
- [ ] Focus order follows the reading order.
- [ ] Headings and landmarks are meaningful.
- [ ] Images have appropriate alt text.
- [ ] Controls have accessible names and labels.
- [ ] Text and controls have adequate contrast.
- [ ] Layout remains usable at narrow widths and browser zoom.
- [ ] Charts have a textual summary and accessible data alternative.
- [ ] Automated checks are supplemented with manual review.

## Reporting issues

Accessibility issues should include the page, browser, assistive technology where applicable, steps to reproduce, expected behaviour, and actual behaviour. Do not claim WCAG conformance without a suitable audit and evidence.
