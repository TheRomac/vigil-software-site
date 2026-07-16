# Vigil Software site

Two self-contained pages, no build step:

- `index.html` — home page (company + Vigil + Vintage Reader)
- `support.html` — support page with contact form, mailto to romac@vigil-software.com

The logo and favicon are embedded as base64 inside the HTML, so these two
files are the whole site — no separate `/assets` folder to keep track of.

## Deploy to GitHub Pages

1. Create a new **public** repo, e.g. `vigil-software-site`.
2. Add `index.html`, `support.html`, `CNAME`, and this `README.md` to the repo root
   (or push this whole folder as-is).
3. In the repo: **Settings → Pages → Source → Deploy from a branch**, pick
   `main` / `root`, save.
4. It'll build at `https://<your-username>.github.io/vigil-software-site/`.

## Custom domain (vigil-software.com)

The `CNAME` file is already set to `vigil-software.com`. At your DNS
provider, add:

- Four **A** records for the apex domain (`@`) pointing at GitHub Pages:
  ```
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```
- A **CNAME** record for `www` → `<your-username>.github.io`

Then in **Settings → Pages**, enter `vigil-software.com` as the custom
domain and tick **Enforce HTTPS** once it's verified (can take a little
while to issue the certificate).

If your registered domain isn't actually `vigil-software.com`, just edit
the `CNAME` file to match.

## Contact form (FormSubmit)

The support form posts to [FormSubmit](https://formsubmit.co) — a free
service that forwards form submissions to an email address, no backend or
signup required (works fine on static GitHub Pages hosting).

**One-time step:** the *first* submission to a new target email triggers a
confirmation email from FormSubmit to `romac@vigil-software.com`. You (or
whoever submits the test) needs to click the activation link in that email
before the form will actually deliver messages. Submit a test message
yourself right after deploying to get this out of the way.

Notes on the current form config:
- `_captcha` is set to `true` (FormSubmit's own spam captcha, shown after
  submit). Set it to `false` in both `support.html` forms if you'd rather
  skip that step, at the cost of more spam.
- No `_next` redirect is set, so FormSubmit shows its own default "thanks"
  page after a submit. You can point `_next` at a page of your own if you
  want a branded thank-you instead.

## Legal footer

The footer states the company name, registered-in-Scotland status, and
company number (SC895863), pulled from the Companies House certificate —
deliberately without the registered office address, per your instruction.
If you register for VAT, add HMRC-related trading disclosures, or want a
full privacy policy later (the contact form does collect name/email/message),
that's worth adding as the business grows.
