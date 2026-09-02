# Production domain migration

The GitHub-side migration was approved and configured on 2026-09-02. GitHub Pages uses `www.stefanograncini.com` as the custom domain and created the repository-root `CNAME` file. Namecheap DNS has not yet been changed; `www.stefanograncini.com` therefore remains pointed at Google until the separately approved DNS handoff.

`jmp.stefanograncini.com`, the job-market-paper repository and workflow, email/MX records, and Search Console TXT verification records are outside this migration and must remain unchanged.

## Pre-flight

1. Record the current DNS records before any DNS handoff.
2. Confirm the GitHub Pages preview and all production-root paths render correctly.
3. Confirm `robots.txt`, `sitemap.xml`, JSON-LD, Open Graph URLs, and per-page canonical tags use `https://www.stefanograncini.com/`.
4. Confirm GitHub Pages reports `www.stefanograncini.com` as the custom domain before changing DNS. Do not alter `jmp.stefanograncini.com`.

## DNS and HTTPS

Use GitHub’s current Pages documentation to determine the required `www` CNAME and any apex configuration. Configure the apex only if deliberately desired; `www` should be the canonical public hostname. Wait for GitHub’s domain verification and HTTPS certificate, then enforce HTTPS only after it is issued.

## Transition and validation

Keep the Google Site available until the new `www` domain, HTTPS, homepage, `/research/`, `/teaching/`, `/sitemap.xml`, and `/robots.txt` all pass browser checks. Google Sites has limited redirect control; if it cannot issue path redirects, retain a concise transition page there temporarily. Verify Search Console ownership and submit the production sitemap.

## Rollback checklist

1. Disable the custom domain in GitHub Pages.
2. Restore the recorded Namecheap DNS records for Google Sites.
3. Confirm the Google Site resolves over HTTPS.
4. Recheck that `https://jmp.stefanograncini.com/paper.pdf` is unchanged.
5. Do not delete this preview repository; it remains a safe test environment.
