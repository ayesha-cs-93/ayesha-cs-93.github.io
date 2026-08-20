# Ayesha Farooq — Portfolio

Live site: https://ayesha-cs-93.github.io/ (custom domain: https://ayeshafarooq.is-a.dev/)

## What it is, and for whom

A single-page personal portfolio for Ayesha Farooq, a CS student and AI/ML intern. It's built for two audiences: recruiters/reviewers scanning for real, verifiable work (FlyRank AI internship, Kaggle competition results, backend projects), and universities/scholarship committees (Türkiye Bursları) who need a fast, credible overview of technical background.

It shows real projects only — each project links to its actual GitHub repo so a visitor can verify the work directly.

## Setup (for a stranger to reproduce)

This is a static site — no build step, no dependencies.

1. Clone the repo:
   ```
   git clone https://github.com/ayesha-cs-93/ayesha-cs-93.github.io.git
   cd ayesha-cs-93.github.io
   ```
2. Open `index.html` directly in a browser, or serve it locally:
   ```
   python -m http.server 8000
   ```
   Then visit `http://localhost:8000`.
3. To deploy: push to the `main` branch of a repo named `<username>.github.io` — GitHub Pages serves it automatically at `https://<username>.github.io/`.

No API keys, no environment variables, no package installs required for the site itself. (The contact form talks to a separate backend — see "Architecture" below — but the site works and displays fully without it.)

## Usage

- Click the sidebar buttons (Home, Projects, Skills, Education, Experience, Achievements, Contact) to switch sections — it's a single HTML page with JS-driven show/hide, not separate page loads.
- URL hash updates on navigation (e.g. `#projects`), so direct links to a section work and refresh-safe.
- Certificate images in Achievements open in a lightbox on click.
- The Contact form submits to a live backend (see below) and shows a status message on send/failure.

## Architecture

```
Browser (index.html: HTML + CSS + vanilla JS, no framework)
   │
   ├── Static content: hero, projects, skills, education, experience, achievements
   │     — hardcoded in HTML, no CMS or database
   │
   └── Contact form → fetch() POST →
         Railway-hosted FastAPI backend
         → Resend API → sends email to owner
```

- **Frontend:** plain HTML/CSS/JS, single file, no build tools. Fonts via Google Fonts (Space Grotesk, Inter, JetBrains Mono). Hosted free on GitHub Pages, custom domain via `is-a.dev`.
- **Contact form backend:** separate FastAPI service deployed on Railway, using the Resend API to send email (Railway blocks outbound SMTP, so Resend's HTTP API is used instead of raw SMTP).
- **Analytics:** GoatCounter (privacy-friendly, no cookies).

## Eval results

This isn't a model-backed project, so there's no accuracy/precision-style eval. What was checked before calling it done:

- **Cross-browser/responsive check:** tested at desktop, tablet, and mobile breakpoints (800px and 480px media query cutoffs) — sidebar collapses to a horizontal nav bar on small screens.
- **Link integrity:** every "→ github.com/..." project link verified to point to a real, public, non-empty repo.
- **Contact form:** submitted a real test message end-to-end (form → Railway backend → Resend → inbox) and confirmed delivery.
- **Content accuracy pass (Aug 2026):** an earlier draft of this site listed a project ("Sehat Sahara — AI health chatbot") that was never actually built. This was caught and removed. This is the one limitation called out on camera in the demo — see below.

## Limitations

- **No CMS/backend for content** — every project, skill, and achievement is hand-edited HTML. Adding a new project means editing the file directly, not filling a form.
- **Contact form has a single point of failure** — if the Railway backend or Resend API is down, the form fails; there's no fallback queue or retry.
- **No automated tests** — correctness has been checked manually (see Eval results), not via a test suite.
- **Content accuracy is manual** — as the Sehat Sahara case showed, nothing currently prevents an inaccurate project description from being added; it relies on manual review before publishing. This is the one limitation named on camera.

## Built with AI

This site's structure, styling (dark theme, teal/terracotta palette, typography choices), and content were drafted with Claude, then reviewed and corrected by hand — including catching and removing the inaccurate Sehat Sahara project entry described above. The contact-form backend (FastAPI on Railway, Resend integration) was also built with Claude's help after Railway's SMTP block required switching approach.
