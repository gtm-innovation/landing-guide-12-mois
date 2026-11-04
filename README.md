# Landing page: « Vos 12 premiers mois en bourse »

Lead magnet landing page for moneyradar.org. Visitors leave their email and get a free PDF guide (12 steps, one per month, for first-time investors).

## Files

- `index.html`: the page, as an **injectable fragment** (same format as our calculators): one `<meta viewport>`, one `<style>`, one root `<div class="mrlm v2">`, one `<script>`. No `<html>`, `<head>` or `<body>`, no fonts loaded, all CSS scoped under `.mrlm.v2`, responsive with `@container`.
- `img/`: the 4 images used by the page, served through jsDelivr (`cdn.jsdelivr.net/gh/gtm-innovation/landing-guide-12-mois@main/img/…`), like `simulateur-acheter-ou-louer`.

## Integration

Same as the `simulateur-*` repos: create the WordPress page and render `index.html` inside it, full width, no sidebar. A push on `main` should then update the live page.

- Proposed URL: `/guide-bourse-12-mois/` (to be confirmed by Simon).
- No header or footer in the fragment: the theme provides them.

## Form

Both forms (hero and final section) POST to the existing Worker `mric-rapport-impots` with `calculator: "guide-12-mois"`. The Worker branch is **already deployed and tested** (04/11/2026):

- subscribes the email in Beehiiv (tag `guide-12-mois`),
- sends a short email through Resend with the two PDF links.

The PDFs live in the WordPress media library (media 63300 and 63301). Nothing else to set up on the WordPress side.
