# Access control — restrict the site to `@3ieimpact.org`

We host the site on **Cloudflare Pages** and gate it with **Cloudflare Access**
(Zero Trust), which allows only people whose verified email ends in
`@3ieimpact.org`. Cloudflare's free plan covers up to 50 seats.

Plain GitHub Pages cannot do this — that is why hosting moves to Cloudflare Pages.
GitHub still holds the source; GitHub Actions renders and deploys on every push.

## One-time setup

### 1. Cloudflare account + Pages project
1. Create a free Cloudflare account.
2. In **Workers & Pages > Create > Pages**, create a project named **`eso-course`**
   (choose "Direct Upload" — the GitHub Action will push builds to it).
3. Note your **Account ID** (Workers & Pages > right sidebar).

### 2. API token for the GitHub Action
1. Cloudflare dashboard > **My Profile > API Tokens > Create Token**.
2. Use the **"Edit Cloudflare Workers"** template, or a custom token with
   **Account > Cloudflare Pages > Edit**.
3. Copy the token.

### 3. GitHub secrets
In the GitHub repo: **Settings > Secrets and variables > Actions > New repository secret**:
- `CLOUDFLARE_API_TOKEN` = the token above
- `CLOUDFLARE_ACCOUNT_ID` = your account ID

### 4. Deploy
Push to `main` (or run the workflow manually). The Action renders the site and
deploys it. The site appears at `https://eso-course.pages.dev` (or your custom
domain). Update `site-url:` in `_quarto.yml` to that URL.

### 5. Gate it with Cloudflare Access (the actual restriction)
1. Open **Zero Trust** (one-time: pick the free plan).
2. **Access > Applications > Add an application > Self-hosted**.
3. Application domain: `eso-course.pages.dev` (or your custom domain).
4. Add a policy:
   - **Action:** Allow
   - **Include:** *Emails ending in* → `@3ieimpact.org`
5. Login methods: **One-time PIN** (email code, no IdP needed) works immediately.
   For single sign-on, add **Microsoft Entra ID** (or Google) as an identity
   provider under Zero Trust > Settings > Authentication.
6. Save. The site now prompts for a 3ie email and lets in only `@3ieimpact.org`.

## Result
Anyone visiting the site is challenged by Cloudflare Access; only verified
`@3ieimpact.org` users reach the handbook. Revoking access = removing someone from
3ie email / your IdP.

> Alternative (no Cloudflare): if 3ie is on **GitHub Enterprise Cloud**, you can
> instead keep the repo private and set Pages visibility to *private* (org members
> only). That restricts by GitHub org membership rather than email domain.
