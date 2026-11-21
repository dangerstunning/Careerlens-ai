# CareerLens AI — Advanced Career Intelligence Studio

A multi-feature AI career product built for the ApnoAI Task 3 challenge and portfolio demonstrations.

## Features
- Resume upload: PDF, DOCX, TXT (browser-side text extraction)
- Resume ↔ job description analysis with heuristic ATS readiness, job match and confidence scores
- Keyword match/missing keyword map, skill-gap analysis, resume issues and evidence-grounded recommendations
- Impact-oriented bullet rewrites that avoid inventing metrics
- Interview question set with answer frameworks
- Personalized roadmap (30/60/90 days or 6 months) with projects and milestones
- Tailored cover-letter drafting
- English, Tamil and Hindi output options
- Local analysis history (browser localStorage), JSON export, copy report, print-to-PDF
- Responsive interface, light/dark theme
- Structured JSON output, server-side API key, input limits, error handling, injection-resistant instructions

## Stack
HTML/CSS/JavaScript frontend · Vercel Serverless Function · Gemini API (`generateContent`, structured JSON schema)

## Setup
1. Obtain a Gemini API key from Google AI Studio.
2. Never place the key in frontend JavaScript or commit it to Git.
3. In project root, create `.env.local`:
   ```
   GEMINI_API_KEY=your_key_here
   GEMINI_MODEL=gemini-2.5-flash
   ```
4. Install Vercel CLI and run:
   ```bash
   npm install -g vercel
   vercel dev
   ```
5. Open the local URL printed by Vercel.

## Deploy
1. Push this project to a new GitHub repository. `.gitignore` excludes `.env.local`.
2. Import repository into Vercel.
3. Add `GEMINI_API_KEY` under Project → Settings → Environment Variables.
4. Optionally add `GEMINI_MODEL` (default `gemini-2.5-flash`).
5. Redeploy and test all modes with non-sensitive sample data.

## API
`POST /api/analyze` with JSON `mode`:
- `analyze`: `{mode, resume, jd, level, language}`
- `roadmap`: `{mode, skills, target, timeline, language}`
- `interview`: `{mode, background, role, focus, language}`
- `cover_letter`: `{mode, resume, jd, tone, length, language}`

The API returns schema-constrained JSON. Scores are heuristic educational indicators and must not be presented as real ATS output or hiring predictions.

## Suggested 5-case evaluation
See `EVALUATION.md`. Record the actual outputs, your pass/fail assessment, and at least one prompt iteration. Do not claim results before running tests.

## Limitations / privacy
- Analysis calls send submitted text to Gemini via the server API. Avoid uploading identity numbers, sensitive medical/financial information, or unrelated personal data.
- PDF/DOCX text extraction happens in the browser using CDN-hosted libraries; scanned PDFs may not extract text (OCR is not included).
- History is local to the browser and can be cleared by clearing this site's browser storage.
- AI-generated feedback can be inaccurate. Verify every recommendation and never use it as the sole basis for career decisions.
- The project is a scaffold; validate model availability, API quota, and deployment before submission.
# Careerlens-ai
# Careerlens-ai
