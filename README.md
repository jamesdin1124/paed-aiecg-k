# Paediatric AI-ECG Potassium Study — proposal page

Live address: https://jamesdin1124.github.io/paed-aiecg-k/

## What this page is

A one-page summary of a proposed multinational study: external validation and
adaptation of an adult AI-ECG potassium model in children. Pediatric teams
reach it by scanning the QR code on the conference slide (Hong Kong,
9 October 2026). A button on the page leads to a short Google Form survey.
Under each button, a line gives the email address, for anyone who cannot open
Google Forms.

The QR code points to this page, not to the form, so the QR code never has to
change. Only the button link changes.

The page is `index.html`, with inline CSS and a few lines of inline
JavaScript, plus two figure images in `img/` from the same site
(Figure 2 of the adult study, wide and stacked versions). It loads nothing
from other sites (no fonts, scripts, images, logos, analytics or cookies) and is marked `noindex`, so search
engines are asked not to list it. This README is public too: it is served at
`/paed-aiecg-k/README.md`.

## First publication (once)

1. Create a **public** repository named `paed-aiecg-k` under the account
   `jamesdin1124`.
2. Put `index.html`, `.nojekyll` and this `README.md` at the root of the
   default branch (`main`).
3. Settings → Pages → Build and deployment → Source: **Deploy from a branch**;
   Branch: `main`, folder `/ (root)`. Save.
4. Wait at least 10 minutes. GitHub Pages pages are cached for up to
   10 minutes, and a 404 seen before the first push is cached too.
5. On a phone using mobile data (not Wi-Fi), open the live address in a
   private tab. It must show this page, not a 404.
6. Scan the QR code itself (projected slide and printed card) and check that
   it opens this page.

Everything pushed to a public repository stays in its history, even after a
later change. Publish only text that has been approved.

## How to set the survey link

1. Open `index.html`.
2. Near the top, inside the `<script>` block, find this line:

   ```js
   const SURVEY_URL = "";
   ```

3. From the Apps Script execution log, copy the line
   **`1. Published URL`**. It looks like
   `https://docs.google.com/forms/d/e/…/viewform`. A `https://forms.gle/…`
   short link also works. **Never use `2. Edit URL`** (it ends in `/edit`):
   it opens only for you, and everyone else sees a Google permission page.
4. Paste it between the two straight quotes, for example:

   ```js
   const SURVEY_URL = "https://docs.google.com/forms/d/e/1FAIpQLS…/viewform";
   ```

   Edit on a computer if you can. Phone keyboards can turn `"` into curly
   quotes (`“ ”`), which stop the script; the buttons then stay as email
   buttons.
5. Commit and push:

   ```sh
   git add index.html
   git commit -m "Set survey link"
   git push
   ```

6. Do this at least 60 minutes before the talk (cache, see above).
7. Check the live page **in a private window, or on a device that is not
   signed in to the Google account that owns the form**. The owner's own
   browser opens even an Edit URL, so it hides that mistake.
   - The button reads "Take the survey (2–3 minutes)".
   - The line under it reads "If the survey does not open, email …".
   - Tap the button and go on to the first question; no sign-in is asked.
   - Scan the QR code with a phone camera and also from WeChat's scanner.

If `SURVEY_URL` is empty, or is anything other than a form's Published URL
(an Edit URL, an `http://` link, another site), the page ignores it: both
buttons read "Survey opens soon — email us" and open an email to
jamesdin1124@gmail.com, and the browser console says why.

The button label "Take the survey (2–3 minutes)" is in the same `<script>`
block. Change it there, and in the form description, if a timed test on a
phone takes longer than 3 minutes.

## Changing the text

The study summary on this page is copied word for word from the approved
summary that also appears at the top of the Google Form. If the summary
changes, change both, then update the "Last updated" date at the bottom of
`index.html`. Do not add claims or numbers that are not in the approved
summary.

## Figures and links

The three figures are original, hand-written inline SVG drawn for this page
(no journal figure, visual abstract, logo or image file is used):

1. What the model does: 12-lead ECG → AI-ECG model (ECG12Net) → ECG estimate
   of serum potassium, compared with laboratory potassium; below it, the adult
   numbers from the summary (no new numbers).
2. The three steps: Step 1A → Step 1B (only if needed) → Step 2 (later, under
   a separate protocol).
3. How data move in Step 1: names, ID numbers and all dates removed at your
   hospital → secure transfer → central analysis → each site receives its own
   results.

The wording on the figures is taken from the approved summary; they add no
claim or number. Each figure has a
narrow (stacked, for phones) and a wide version; CSS shows one of them.
Colours come from the page's CSS variables, so both light and dark mode work.

Links to the published papers open in a new tab. They are links the reader
clicks, not resources the page loads. The Publications list gives author,
journal and year only (no article titles):

- Ding JJ et al. Am J Kidney Dis 2026 — https://doi.org/10.1053/j.ajkd.2026.05.020 ·
  https://pubmed.ncbi.nlm.nih.gov/42595038/
- Zhou X, Neyra JA. Editorial. Am J Kidney Dis 2026 —
  https://doi.org/10.1053/j.ajkd.2026.08.003 · https://pubmed.ncbi.nlm.nih.gov/42801327/
- Lin CS et al. (ECG12Net) JMIR Med Inform 2020, open access —
  https://doi.org/10.2196/15931 · https://pubmed.ncbi.nlm.nih.gov/32134388/

The two citations inside the summary link to the first and third DOI; their
visible text is unchanged.

## Data and privacy

This page sets no cookies, runs no analytics or tracking code, and loads no
third-party resources. A Content-Security-Policy in the page blocks any
outside resource from loading. The links to doi.org and PubMed are ordinary
links: nothing is fetched from those sites unless the reader clicks one. GitHub, which hosts the page, logs visitors'
IP addresses for security (see GitHub's documentation, "About GitHub Pages",
Data collection). The survey is a Google Form; it asks for professional
contact details and about the respondent's hospital, and does not ask for
patient data.

## Maintainer

Jhao-Jhuang Ding, MD — jamesdin1124@gmail.com

## Files

- `index.html` — the page
- `.nojekyll` — tells GitHub Pages to serve the files as they are
- `README.md` — this file

## Images for the Google Form

`img/fig1_what_the_model_does.png`, `img/fig2_three_steps.png` and `img/fig3_how_data_move.png` are PNG exports of the three figures on this page (light theme, 2x). The Google Form shows them at the top (inserted by URL in the form editor). They are not loaded by `index.html`.
