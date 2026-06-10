# Sterling Capital Advisors — Landing Page

A single-page marketing/landing site for Sterling Capital Advisors, an investment strategy
advisory. Built as one self-contained `index.html` — plain HTML5, CSS3, and vanilla
JavaScript, with no build system, package manager, or dependencies.

![Screenshot of the Sterling Capital Advisors landing page](screenshot.png)

## Live Site

Deployed automatically to GitHub Pages on every push to `main` via
[`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml).

## Running Locally

No build step or server required — just open the file in a browser:

```
start chrome index.html
```

## Structure

Everything lives in [`index.html`](index.html):

- **`<style>`** — theme-driven CSS using `:root` custom properties (`--primary`,
  `--secondary`, `--accent`, `--background`, `--text`, `--light-bg`)
- **Body** — sequential sections: nav, hero, why us, process, testimonials, lead magnet,
  enquiry form, FAQ, final CTA, and footer
- **`<script>`** — sticky navbar, mobile nav toggle, smooth scroll, scroll-reveal
  animations, FAQ accordion, enquiry form validation, and dynamic copyright year

## Enquiry Form

The contact form submits via [FormSubmit](https://formsubmit.co) — no backend required.

## SEO & Other Pages

- [`robots.txt`](robots.txt) and [`sitemap.xml`](sitemap.xml) — crawler directives and sitemap
  for the live site
- [`privacy-policy.html`](privacy-policy.html) — standalone PDPA-compliant privacy policy,
  linked from the footer

See [CLAUDE.md](CLAUDE.md) for detailed architecture and editing conventions.
