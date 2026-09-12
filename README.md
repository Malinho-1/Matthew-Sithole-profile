# Matthew Sithole — Profile / Mini-Portfolio Page

A one-page semantic HTML5 profile and mini-portfolio site built for the
CIS2103 Web Technologies Unit II practical assignment.

## AI-Assisted Content

See [PROMPT_LOG.md](./PROMPT_LOG.md) for the full prompt, the AI's raw output,
my edited final version, and my reflection on the changes.

## Accessibility

**Issue found in peer review (Thursday's practical):** My reviewer pointed out
that the number input in my contact form had no visible label, so a screen
reader user wouldn't know what it was asking for.

**Fix applied:** I replaced the unlabeled number input with properly labelled
text, email, phone, and message fields, each using a `<label for>` matched to
the input's `id`.

Additional accessibility work done while polishing the page:
- Changed the `<h1>` name heading from a light blue (`#9ac9f1`) to a darker
  blue (`#0b5394`) for better colour contrast against the light background.
- Every form input now has an associated `<label>`.
- Heading levels are properly nested (h1 → h2 → h3, no skipped levels).

## Notes

- Built with plain HTML5 and external CSS — no JavaScript form validation,
  only native HTML5 attributes (`required`, `type="email"`, `pattern`,
  `minlength`).
- This repository will be extended with responsive CSS3/Tailwind styling in
  the Unit III assignment.
