# Sheeza Ahsan — Full-Stack Developer Portfolio

A premium, fully responsive single-page portfolio built with React, Vite, and Tailwind CSS. Dark theme by default, with a working light theme toggle.

## Run locally

```bash
npm install
npm run dev
```

Open the URL printed by Vite (default: http://localhost:5173).

## Production build

```bash
npm run build
npm run preview
```

The static build is written to `dist/` and can be deployed to Vercel, Netlify, Cloudflare Pages, or any static host.

## Editing content

All content lives in one place: `src/data/site.js`.

- Profile, contact details, and the "Open to opportunities" label (`availability.enabled` / `availability.label`)
- About copy, highlights, and the facts shown in the stat strip
- Skills grouped by category
- Projects (title, description, tech stack, live URL, preview artwork variant)
- Education, certifications, soft skills
- Navigation labels

Component styling and design tokens live in `src/index.css`.

## Contact form behavior

The form validates name, email, and message, then:

1. If `VITE_CONTACT_ENDPOINT` is set, it POSTs JSON to that endpoint (Formspree, Basin, a serverless function, etc.) and only shows success after a successful response.
2. If no endpoint is configured, it opens the visitor's email app with the message prefilled and offers a "Copy message" fallback. It never claims a message was sent when it wasn't.

To enable direct sending, create `.env.local`:

```bash
VITE_CONTACT_ENDPOINT=https://formspree.io/f/your-form-id
```

## CV download

The Download CV links point to `public/Sheeza-Ahsan-CV.pdf`.

The source for that PDF is `scripts/cv.html`. To regenerate it after editing:

```bash
"C:\Program Files\Google\Chrome\Application\chrome.exe" --headless=new --disable-gpu --no-pdf-header-footer --print-to-pdf="public/Sheeza-Ahsan-CV.pdf" "file:///D:/Portfolio/scripts/cv.html"
```

Adjust the browser path for your operating system.

## Project structure

```
index.html                 SEO metadata, fonts, JSON-LD
src/
  App.jsx                  Page composition
  index.css                Design system, themes, layout, animations
  data/site.js             All portfolio content
  hooks/useSite.js         Theme, scrollspy, scroll progress
  lib/contact.js           Validation and mailto builder
  components/              Navbar, Hero, About, Skills, Projects,
                           Education, Contact, Footer, shared UI
public/
  Sheeza-Ahsan-CV.pdf
  og-cover.jpg
  favicon.svg
scripts/
  cv.html                  Print source for the CV PDF
```

