# Future domain migration — do not execute before explicit approval

This preview has **no CNAME file** and no custom-domain setting. `stefanograncini.com` remains served by Google Sites.

## Pre-flight

1. Record all current Namecheap DNS records (A, AAAA, CNAME, TXT, MX, and any Google-site verification record) and take screenshots.
2. Confirm the GitHub Pages preview renders correctly and replace the portrait placeholder.
3. Update the production base URL in `robots.txt`, `sitemap.xml`, JSON-LD, and add canonical tags pointing to `https://www.stefanograncini.com/`.
4. In GitHub repository Settings → Pages, set the custom domain to `www.stefanograncini.com`; only then follow GitHub’s DNS instructions exactly. Do not alter `jmp.stefanograncini.com`.

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
