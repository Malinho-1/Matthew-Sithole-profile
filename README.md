# Matthew Sithole — Profile / Mini-Portfolio Page

A one-page semantic HTML5 profile and mini-portfolio site for CIS2103 Web
Technologies. Practical Assignment 1 built the semantic structure; Practical
Assignment 2 adds responsive styling with CSS3 and Tailwind.

## AI-Assisted Content

See [PROMPT_LOG.md](./PROMPT_LOG.md) for the full prompt, the AI's raw output,
my edited final version, and my reflection on the changes.

## Accessibility

**Issue identified:** While reviewing my contact form, I noticed the number
input had no visible label, id or name, so a screen reader user would have no
way of knowing what it was asking for.

**Fix applied:** I replaced it with properly labelled text, email, phone and
message fields, each using a `<label for>` matched to the input's `id`.

Additional accessibility work:
- The `<h1>` uses a dark blue (`#1815cf`) that has strong contrast against the
  light background.
- Every form input has an associated `<label>`.
- Heading levels are properly nested (h1 → h2 → h3, no skipped levels).
- Nav links have visible hover and keyboard-focus styles (`:focus-visible`).

## Responsive Notes

### Breakpoints tested

I tested the page in the browser's device toolbar at **375px (mobile)**,
**768px (tablet)** and **1280px (desktop)**. At each width there is no
horizontal scrollbar, no overlapping text, and all four nav links are visible.

- **375px:** everything stacks in one column; the portrait sits above the
  intro text; the skills show as a 2 × 2 grid; the Send button is full width.
- **768px:** the portrait moves beside the intro text; the page becomes two
  columns (About beside Skills, Project beside Contact); the nav aligns left.
- **1280px:** same two-column layout, with a larger name heading and more
  padding inside each section.

The browser console shows no errors (only the standard Tailwind Play CDN
notice that it is intended for development).

### Mobile-first approach

The base CSS is the phone layout. Two hand-written `min-width` media queries
(`768px` and `1024px`) in `style.css` add to it for larger screens. Tailwind's
`md:` and `lg:` variants in the HTML use the same breakpoints.

### Flexbox vs Grid, and why

- **Flexbox: the navigation** (`.navigation`). A nav is a single row of items,
  so Flexbox fits. It uses `flex-wrap`, `justify-content` (`space-between` on
  mobile, `flex-start` from 768px), `align-items` and `gap`. The header also
  uses Flexbox, through Tailwind utilities.
- **Grid: the page layout** (`.content`). The sections need rows and columns
  together, so it is one `1fr` column on mobile and `repeat(2, 1fr)` with a
  `gap` from 768px.
- **Grid: the skills list** (`#skills ul`). It uses
  `repeat(auto-fit, minmax(120px, 1fr))`, so the columns adjust to the space
  available without needing a media query.

### Tailwind vs my own CSS

- **Tailwind utilities (in `index.html`):**
  - the **header** (flex layout, spacing, rounded portrait, with `md:` and
    `lg:` variants that change the layout and name size), and
  - the **contact form** (grid, input styling, `md:gap-3`, and a button that
    is full width on mobile and `md:w-fit` from tablet up).
- **My own CSS (in `style.css`):** the type and spacing scale (CSS variables),
  the page Grid layout, the Flexbox nav, the section styling, the skills grid,
  the footer, and the custom media queries.
- **Why split it this way:** I used my own CSS for page structure, where I
  wanted to show Grid, Flexbox and media queries written by hand, and Tailwind
  for the header and form, which are built from small repeated pieces. The CSS
  rules for the header and form were removed from `style.css` so the same
  element is never styled in both places.
- **Configuration:** Tailwind's Preflight reset is turned off
  (`corePlugins: { preflight: false }`) so it does not override my base styles.
  The Tailwind colours `brand` (`#0b5394`) and `heading` (`#1815cf`) repeat the
  values in my CSS variables on purpose, so the two systems match.

## Notes

- Built with semantic HTML5, an external stylesheet, and Tailwind (Play CDN).
- No JavaScript form validation, only native HTML5 attributes (`required`,
  `type="email"`, `pattern`, `minlength`).
