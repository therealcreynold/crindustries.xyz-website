# crindustries.xyz

The public website for **CR Industries LLC** — an independent app studio for Apple platforms
(makers of [WhereIsIt](https://whereisit.now)).

It exists primarily to satisfy the **Apple Developer Program organization enrollment**
requirement that the company have a real, public website on a domain associated with the
legal entity, and to provide company-level contact, privacy, and terms pages.

## Stack

Plain static HTML + one CSS file. **No build step**, no framework, no dependencies.
Hosted free on **GitHub Pages**, served from the `main` branch root.

```
index.html        Company home (legal name, what we do, products, contact)
support.html      Company + product support / contact hub
privacy.html      Website privacy policy (apps have their own)
terms.html        Website terms of use
404.html          Not-found page
styles.css        Design system ("cyber-aurora" — bold indie-studio look)
app.js            Progressive enhancement (scroll reveal, nav shadow) — site works without it
assets/           favicon + WhereIsIt product screenshots
CNAME             Custom domain (crindustries.xyz) — do not delete
.nojekyll         Serve files as-is (skip Jekyll)
robots.txt, sitemap.xml
```

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy

Push to `main`. GitHub Pages redeploys automatically. The repo **must be public**
for free GitHub Pages.

Pages config: **Settings → Pages → Build and deployment → Deploy from a branch →
`main` / `/ (root)`**, Custom domain = `crindustries.xyz`, **Enforce HTTPS** on.

## DNS (managed at Namecheap — BasicDNS)

Set at **Domain List → Manage → Advanced DNS → Host Records**.
**Leave the existing Google Workspace MX records untouched** (they run `info@crindustries.xyz`).

| Type  | Host | Value                     |
|-------|------|---------------------------|
| A     | @    | 185.199.108.153           |
| A     | @    | 185.199.109.153           |
| A     | @    | 185.199.110.153           |
| A     | @    | 185.199.111.153           |
| AAAA  | @    | 2606:50c0:8000::153        |
| AAAA  | @    | 2606:50c0:8001::153        |
| AAAA  | @    | 2606:50c0:8002::153        |
| AAAA  | @    | 2606:50c0:8003::153        |
| CNAME | www  | therealcreynold.github.io. |

Remove the old apex `A → 172.66.0.70` record and the default Namecheap parking/URL-redirect
records. Verify with `dig crindustries.xyz +short` (expect the four `185.199.x.153` IPs).

© 2026 CR Industries LLC.
