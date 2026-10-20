# Skill Radar 2026

A student-first career intelligence demo for finding current job postings, comparing nearby city demand, identifying skill gaps, and exploring learning options.

## Run locally

Requires Node.js 20 or later. No npm packages are required.

1. Copy `.env.example` to `.env`.
2. Put your TinyFish API key in `TINYFISH_API_KEY` in `.env`.
3. Run `npm start` from this folder.
4. Open <http://localhost:4173>.

With TinyFish configured, the default Lucknow Data Analyst search loads three pages (up to 30 results), deduplicated by URL, and searches broadly across indexed job boards and employer career pages. Select a card to see the source snippet, then use “Scan full listing with TinyFish” to inspect the public ad for fraud signals. Open the original source page to apply. Search engines cannot expose every job on the internet; results may include job-board category pages, can expire, and should be checked on the source before applying.

With a key configured, searches, city comparisons, and learning-resource lookups call TinyFish Search for current results. Keep `.env` private; the browser never receives the key. If a key is ever exposed publicly, rotate it in TinyFish and update your local environment.

## Put the project on GitHub

Create an empty repository on GitHub, then upload the contents of this project folder. Do not upload `.env`; it is ignored by `.gitignore`. The `.env.example` file is safe to include and shows which variable the app expects. If you use Git from a terminal, run these commands in this folder after creating your repository:

```sh
git init
git add .
git commit -m "Add Skill Radar demo"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Replace the GitHub URL with your repository's URL. GitHub stores the code; it does not run this Node server as a live website by itself. To publish the demo, deploy the repository to a Node.js hosting service, set `TINYFISH_API_KEY` in that service's private environment-variable settings, and use its public URL. The server reads the hosting provider's `PORT` environment variable automatically.

## TinyFish integration

The Node server sends queries to `GET https://api.search.tinyfish.ai` and authenticates with the `X-API-Key` header. The returned search links power job results, nearby-city comparisons, and local learning options. Quick scam checks inspect the title and search-result snippet for common warning phrases. On demand, the TinyFish Agent API inspects the full public page and returns its evidence and risk assessment. These are warning signals, not employer verification or a guarantee of safety.

## Resume privacy

Resume files are read in the browser only and are never transmitted to TinyFish or the server. The quick scan checks common skill keywords locally. DOCX and plain-text resumes are supported. Text-based PDFs work best; scanned or image-only PDFs may not expose readable text to this lightweight demo.

## Demo details

- Save roles to a local shortlist.
- Add or remove skills in the skills panel.
- Submit a star rating and optional feedback, stored on the current device.
- Nearby-city counts shown before refresh are illustrative, not verified market statistics. Skill suggestions are starter examples, not measured salary estimates.

## Stack

Node.js built-in HTTP server, browser JavaScript, HTML, and CSS. No user account or database is required.
