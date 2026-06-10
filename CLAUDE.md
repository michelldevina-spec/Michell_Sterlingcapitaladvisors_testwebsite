# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page marketing/landing site for "Sterling Capital Advisors" (an investment
strategy advisory). The entire site is one self-contained file: [index.html](index.html).
There is no build system, package manager, framework, or test suite — just plain HTML5, CSS3
(in a `<style>` block), and vanilla JavaScript (in a `<script>` block at the end of `<body>`).

## Running / Previewing

- Open `index.html` directly in a browser (e.g. `start chrome index.html` on Windows). No
  server, build step, or install is required.
- There is nothing to lint, build, or test — changes are verified by reloading the page in a
  browser and checking the affected section/breakpoint visually.

## Architecture

Everything lives in `index.html`, organized top-to-bottom as:

1. **`<style>` block** — all CSS, theme-driven via `:root` custom properties (`--primary`,
   `--secondary`, `--accent`, `--background`, `--text`, `--light-bg`). Change the palette by
   editing these variables only; section styles reference them rather than hardcoded colors.
2. **HTML body** — sequential `<section>`s, each with a stable `id` used for in-page nav
   anchors: nav (`#top`), hero, `#why`, `#process`, testimonials, lead magnet
   (`#lead-magnet`), enquiry form (`#contact`), `#faq`, final CTA, and footer.
3. **`<script>` block** — a single IIFE at the bottom of the file containing independent,
   self-initializing features:
   - Sticky navbar (toggles `.scrolled` class on scroll)
   - Mobile nav menu toggle (`.open` class on `#navLinks` / hamburger)
   - Smooth-scroll handling for all in-page anchor links
   - Scroll-reveal animations via `IntersectionObserver` on elements with the `.reveal` class
   - FAQ accordion (expand/collapse via inline `max-height`)
   - Enquiry form validation (name/email/phone regex checks, inline `.error` states on
     `.form-group` elements, success/error banner in `#formMessage`)
   - Dynamic copyright year

## Enquiry Form / Lead Capture

The contact form (`#enquiryForm`) submits via [FormSubmit](https://formsubmit.co) to
`https://formsubmit.co/michelldevina@gmail.com` using hidden fields `_subject`, `_captcha`,
and `_template`. Client-side JS only blocks submission on validation failure (empty/invalid
name, email, or phone) — it does not call any backend. When changing form fields, keep the
`name` attributes intact since FormSubmit uses them as the email table row labels.

## Conventions

- Icons are inline SVGs (no icon library/CDN).
- Avatars in testimonials are CSS-only initials circles (no image assets).
- The hero background image is loaded from Unsplash via a direct URL — replace this URL if
  swapping imagery, no local asset pipeline exists.
- Keep the page mobile-first: base styles target small screens, with `@media (max-width: ...)`
  overrides for larger breakpoints (768px, 900px).
