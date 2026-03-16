# CLAUDE.md — donororbit.com Marketing Site

> **This document governs all content, copy, and code decisions for the donororbit.com static site. All contributors and AI tools operating on this repository must treat these rules as binding.**

---

## 1. Site Purpose

`donororbit.com` is the public marketing and lead generation site for Orbit, an AI-native fundraising intelligence platform for university advancement offices. Its goals are:

1. Communicate Orbit's value proposition clearly and compellingly
2. Build trust with advancement professionals (skeptical, detail-oriented buyers)
3. Capture qualified leads via the contact form (routed to Google Sheets)

---

## 2. Tech Stack

- **Static HTML/CSS/JS** — no build step, no framework, no npm
- **Deployed via GitHub Actions** → GitHub Pages → custom domain `donororbit.com`
- **Contact form** → Google Apps Script Web App → Google Sheets (no-cors POST)
- **CNAME**: `donororbit.com`

---

## 3. Content & Copy Rules

### Em Dash Prohibition (Universal, Non-Negotiable)

**Never use the em dash character (—) in any user-facing content.**

This applies to:
- All website copy, headlines, subheadings, and body text
- Any content generated for use on this site (agent outputs, drafts, suggestions)
- Email content, form confirmation text, or any text a visitor reads

**Code comments are the only exception.** Inline comments in source code may retain em dashes.

**Alternatives:**
- Replace ` — ` with a comma, colon, or restructured sentence
- Replace `Title — Subtitle` patterns with `Title: Subtitle`
- Break long sentences into two shorter ones when appropriate

**Rationale:** Em dashes render inconsistently across email clients and older browsers. Clean punctuation signals professionalism to the advancement office buyers this site targets.

---

### General Copy Standards

- **Tone**: Confident, clear, professional. Not salesy or hyperbolic.
- **Audience**: University advancement officers, major gift officers, annual giving directors, VPs of Advancement. These are sophisticated, skeptical buyers.
- **Avoid**: Buzzwords without substance, vague claims, exclamation points in headlines.
- **Numbers**: Use real specifics where possible (e.g., "150 donors per officer" not "fewer donors").

---

## 4. Design Rules

- **Color palette**: Defined by CSS variables in `index.html` — do not introduce new hex values; extend the existing variable system.
- **Typography**: DM Sans (Google Fonts). Fluid type using `clamp()`.
- **Scroll reveal**: Use `.reveal` + `.reveal.visible` + `IntersectionObserver` pattern already in the file.
- **No external JS frameworks** — vanilla JS only; keep the page fast.

---

## 5. Form & Data Rules

- Contact form fields: First Name, Last Name, Institution, Role, Email
- All submissions POST to `GOOGLE_SCRIPT_URL` constant in the JS
- Always include `source: 'donororbit.com'` and `timestamp` in the payload
- Show success message regardless of fetch outcome (no-cors means response is always opaque)

---

## 6. Deployment

- Pushes to `main` trigger the GitHub Actions deploy workflow automatically
- The workflow uploads the entire repo root as the Pages artifact
- Never commit `.env` files, secrets, or credentials

---

*Maintained by: Orbit Engineering*
*Rule: Review this document before making changes to site copy or structure.*
