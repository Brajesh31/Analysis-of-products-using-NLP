# ♿ Accessibility standards and review checklist

Accessibility is part of the product quality of the static frontend, the documentation, and any future charts. This guide sets a practical baseline; it does not claim that the current pages have passed a formal accessibility audit.

## 1. Semantic structure

Use landmarks such as header, navigation, main, and footer where appropriate. Keep heading levels in a meaningful hierarchy. Use buttons for actions and links for navigation. Avoid using generic containers when a semantic element communicates the purpose more clearly.

## 2. Keyboard operation

Every interactive element should be reachable and usable with a keyboard. Focus order should follow the visual reading order. Focus indicators must remain visible. Do not create hover-only interactions that cannot be accessed through keyboard or touch.

## 3. Images and icons

Provide descriptive alternative text for informative images. Decorative images should use empty alternative text so screen readers do not announce irrelevant details. Icon-only controls need an accessible name. Do not put essential instructions only inside an image.

## 4. Forms and controls

Associate labels with form controls. Explain required fields and validation errors in text. Ensure errors are not communicated by colour alone. Keep instructions close to the control they describe.

## 5. Colour and typography

Maintain sufficient contrast for text and controls. Avoid relying on colour alone to communicate sentiment, status, or rating. Allow browser zoom and text resizing. Keep line lengths and spacing comfortable for reading.

## 6. Responsive layout

Test the home and listing pages at narrow viewport widths. Content should not require horizontal scrolling except for genuinely two-dimensional data. Images should scale without distortion. Navigation should remain understandable and operable.

## 7. Charts and analytical summaries

Every important chart should have:
- a clear title and purpose;
- labelled axes and units;
- sample size and collection window;
- a text summary of the main pattern;
- a table or accessible alternative when exact values matter;
- labels, patterns, or shapes in addition to colour.

## 8. Manual verification

- [ ] Navigate the page using only a keyboard.
- [ ] Confirm visible focus on every interactive element.
- [ ] Inspect heading order and landmarks.
- [ ] Check informative image alt text.
- [ ] Check form labels and error messages.
- [ ] Test browser zoom and narrow layouts.
- [ ] Inspect contrast with an accessibility tool.
- [ ] Test at least one screen reader/browser combination when feasible.

Record issues honestly. Do not claim WCAG conformance without an appropriate audit.
