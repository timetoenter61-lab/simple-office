# Simple Office – client site template

A static, owned-by-the-client business site: a newspaper-style home page, a payment/order page, and browser-based invoice and quote generators with PDF download. No server, no subscription.

**Create a new client site from this template:**
https://github.com/new?template_name=simple-office&template_owner=timetoenter61-lab

> Never edit this template for one client. Always create a fresh copy per client so no details carry over.

## 1. Personalise the copy (per client)

Search the whole repo for each placeholder and replace it.

| Placeholder | Replace with | Where |
|---|---|---|
| `YOUR-DOMAIN.COM` | the client's domain | every `.html` file, `sitemap.xml`, `robots.txt` |
| `YOUR BUSINESS NAME` | the client's business name | every `.html` file |
| `YOUR TAGLINE OR OFFER` | a short line for the header bar | `index.html` |
| `REPLACE_WITH_SELLER_EMAIL` | the client's public order email (two places) | `page2.html` |
| `A$XXX` / `$XXX` | the client's pricing, or delete the offer section | `page2.html` |
| `officeprint.jpg` | the client's own photo (about 1200 px wide, under 300 KB) | repo root |

Also rewrite the home page and the order page copy for the client's business.

The email is visible in the page source. Use an address the client is happy to make public.

The invoice page ships with blank BSB and account number. The client enters their own.

## 2. Publish with GitHub Pages

1. Repo **Settings → Pages**: deploy from branch `main` (or `master`), folder `/ (root)`.
2. Add a file named `CNAME` containing only the client's domain, for example `clientdomain.com`.
3. Tick **Enforce HTTPS** once the certificate is ready.

Free GitHub accounts need a public repo for Pages.

## 3. Domain

- Compare **renewal** prices, not first-year prices. Cheap extensions often renew at much higher rates.
- The client registers the domain in their own name. Cloudflare Registrar sells at wholesale cost.
- `.com.au` needs an Australian business link, usually an ABN.
- No domain? A free `clientname.github.io/repo` address still works.
- DNS for GitHub Pages: four `A` records for the root domain: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`. For `www`, add a `CNAME` to `<github-username>.github.io`.

## 4. Optional login for the invoice and quote tools

A JavaScript password on a static site is not secure, so do not add one in the page code. Use Cloudflare Access (free for up to 50 users per Cloudflare account):

1. Add the domain to Cloudflare on the Free plan and move the nameservers.
2. Keep the DNS records **Proxied** and set SSL/TLS to **Full**.
3. In **Zero Trust → Access → Applications → Self-hosted**, protect `invoice.html` and `quote.html`.
4. Add an **Allow** policy that lists the client's email addresses (one-time PIN login).
5. Test in a private window.

The client should create their own Cloudflare account so their login list is theirs alone. Access only gates the served pages. The repo code stays readable if the repo is public.

## 5. Hand over to the client

1. Client creates their own GitHub account and turns on **two-factor authentication**.
2. Transfer the repo: **Settings → Danger Zone → Transfer ownership**. Optionally keep yourself as a collaborator for support.
3. Client points the domain at GitHub Pages (section 3) and, optionally, adds the login (section 4).
4. Confirm the site loads over HTTPS at the client's domain.
5. Remind the client to renew the domain every year.

## 6. Handover notes for the client

- **Saved invoices and quotes live only in that browser** on that device. Clearing browser data or changing devices deletes them. Download the PDF of everything and keep copies.
- Invoice and quote pages load Tailwind, Alpine and html2pdf from the internet, so PDF export needs a connection.
- Enter the client's own ABN. The ABN field locks once saved.
- The default invoice heading says **TAX INVOICE**. Only a GST-registered seller should use that label, and tax invoices need specific details. Have the client's accountant confirm the wording before use.
- This tool is not tax, legal or accounting advice.

## Files

| File | Purpose |
|---|---|
| `index.html`, `style.css` | newspaper-style home page |
| `page2.html` | order request / payment page |
| `invoice.html`, `quote.html` | generators with PDF download |
| `404.html`, `robots.txt`, `sitemap.xml` | not-found page and search-engine files |
| `officeprint.jpg` | placeholder photo of a portable receipt printer |
