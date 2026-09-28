# Website maintenance guide

## Scope and repository

- Local repository: `/Users/stefanograncini/Desktop/WORK/Job Market/Website`
- GitHub repository: `sgrancini/academic-website-preview`
- Canonical production URL: `https://www.stefanograncini.com/`
- GitHub Pages custom domain: `www.stefanograncini.com`

Never change DNS, Namecheap, GitHub Pages custom-domain settings, `jmp.stefanograncini.com`, `/Users/stefanograncini/Desktop/WORK/Job Market/job-market-paper`, or its publishing automation without explicit user approval.

## Content locations

- Homepage biography, JMP summary, working papers, references, teaching summary: `index.html`
- CV highlights, preview, and conference history: `cv/index.html`
- Complete research portfolio: `research/index.html`
- Teaching record: `teaching/index.html`
- Shared visual system: `assets/css/site.css`
- Authoritative CV URL (what every CV link on the site uses): `https://sgrancini.github.io/cv/cv.pdf`
- Local synchronized CV copy (input for the preview image only): `assets/documents/cv_stefano_grancini.pdf`
- Content ambiguities: `CONTENT_REVIEW.md`

Use verified source materials before changing research facts. Keep the JMP hyperlink exactly `https://jmp.stefanograncini.com/paper.pdf` and every CV hyperlink exactly `https://sgrancini.github.io/cv/cv.pdf`.

## CV updates are automated

The CV is published by `/Users/stefanograncini/Desktop/WORK/Job Market/Publish CV.command` (logic and documentation in `Job Market/.cv-publisher/`). After it has verified that `https://sgrancini.github.io/cv/cv.pdf` serves the approved PDF, it replaces `assets/documents/cv_stefano_grancini.pdf` with that exact PDF, regenerates `assets/images/cv-preview.png` with the command below, and commits and pushes only those two files. Do not replace them by hand. The publisher refuses to run while this repository has other uncommitted changes or unpushed commits, so commit and push unrelated work first.


When replacing `assets/documents/cv_stefano_grancini.pdf`, regenerate its first-page preview from the same approved PDF:

`gs -q -dSAFER -dBATCH -dNOPAUSE -sDEVICE=png16m -r120 -dFirstPage=1 -dLastPage=1 -sOutputFile=assets/images/cv-preview.png assets/documents/cv_stefano_grancini.pdf`

## Routine updates

For a presentation or paper update, change the relevant page(s), preserve the existing plain-paper structure, validate internal links and render desktop/mobile screenshots. For a CV replacement, use `Publish CV.command`; do not replace `assets/documents/cv_stefano_grancini.pdf` manually. For a portrait replacement, add the approved image under `assets/images/`, replace the `SG` placeholder with an `<img>` bearing descriptive alt text, and optimize it.

Whenever `assets/css/site.css` is materially changed in a production deployment, update the stylesheet URL's cache-busting version parameter on every HTML page to the new short commit SHA or another monotonically changing version. This prevents stale browser CSS after deployment.

## Validate and deploy

1. Run a local server: `python3 -m http.server 8017 --directory .`
2. Check `/`, `/research/`, `/teaching/`, the CV, `robots.txt`, and `sitemap.xml`.
3. Capture 1440px and 390px Playwright screenshots; inspect for overflow, hierarchy, and link visibility.
4. Commit one coherent change, push `main`, then verify the Pages URL returns the updated deployment.

Do not use the GitHub web editor; maintenance is performed through this repository.
