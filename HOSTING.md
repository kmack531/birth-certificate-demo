# Hosting on GitHub Pages + Custom Domain (Squarespace)

Follow these steps to put the site on GitHub Pages and connect your Squarespace domain.

---

## Part 1: Push the site to GitHub

### 1. Create a new repository on GitHub

1. Go to [github.com/new](https://github.com/new).
2. **Repository name:** e.g. `birth-certificate-demo` (or any name you like).
3. Leave it **Public**. Do **not** add a README, .gitignore, or license (the project already has these).
4. Click **Create repository**.

### 2. Push your project from your computer

In Terminal, run (replace `YOUR_USERNAME` with your GitHub username and `birth-certificate-demo` with your repo name if different):

```bash
cd /Users/kyle/birth-certificate-demo
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/birth-certificate-demo.git
git push -u origin main
```

If GitHub asks you to sign in, use your credentials or a personal access token.

---

## Part 2: Turn on GitHub Pages

1. On GitHub, open your repository.
2. Go to **Settings** → **Pages** (left sidebar).
3. Under **Build and deployment**:
   - **Source:** Deploy from a branch
   - **Branch:** `main` → **/ (root)** → **Save**.
4. Wait 1–2 minutes. Your site will be live at:
   `https://YOUR_USERNAME.github.io/birth-certificate-demo/`

(If the repo is named `YOUR_USERNAME.github.io`, the URL is `https://YOUR_USERNAME.github.io/`.)

---

## Part 3: Connect your Squarespace domain

### 1. Add the custom domain in GitHub

1. In the same **Settings** → **Pages** section, find **Custom domain**.
2. Enter your domain, e.g. `www.yourdomain.com` or `yourdomain.com`.
3. Click **Save**. GitHub may show a DNS warning until Squarespace is configured; that’s normal.

**Choosing www vs non-www:**

- Use **www.yourdomain.com** if you want URLs like `https://www.yourdomain.com/order.html`.
- Use **yourdomain.com** (apex) if you want `https://yourdomain.com/order.html`.  
You can change this later.

### 2. Configure DNS in Squarespace

1. In Squarespace: **Settings** → **Domains** (or **Website** → **Domains**).
2. Click your domain, then open **DNS Settings** (or **Manage DNS** / **Advanced Settings**).
3. Add the records GitHub expects. In **Settings** → **Pages** → **Custom domain**, GitHub shows the exact values; use these if they differ from below.

**If you use www (e.g. www.yourdomain.com):**

| Type  | Host / Name | Value / Points to      |
|-------|-------------|-------------------------|
| CNAME | www         | YOUR_USERNAME.github.io |

Replace `YOUR_USERNAME` with your GitHub username. Leave any other “Points to” field as Squarespace suggests (e.g. “External”).

**If you use the apex/root (e.g. yourdomain.com):**

Add these four **A** records (Squarespace may list “Host” and “Data” or “Points to”):

| Type | Host / Name | Value / Data        |
|------|-------------|---------------------|
| A    | @ (or blank)| 185.199.108.153     |
| A    | @ (or blank)| 185.199.109.153     |
| A    | @ (or blank)| 185.199.110.153     |
| A    | @ (or blank)| 185.199.111.153     |

**If you want both www and apex:** add the CNAME for `www` and the four A records for `@`. In GitHub, set the custom domain to `yourdomain.com`; GitHub will redirect www to it if you enable “Enforce HTTPS” (recommended).

### 3. Wait for DNS and HTTPS

- DNS can take from a few minutes up to 48 hours.
- In GitHub **Settings** → **Pages**, when DNS is correct you’ll see a green check and the option to **Enforce HTTPS**. Turn that on.
- Visit `https://www.yourdomain.com` (or `https://yourdomain.com`) to confirm the site loads.

---

## Troubleshooting

- **“Domain’s DNS record is incorrect”**  
  Double-check the CNAME or A records in Squarespace. Host should be `www` (for CNAME) or `@` (for A). No typos in `YOUR_USERNAME.github.io`.
- **Site works at github.io but not on my domain**  
  Wait a bit longer for DNS, then try again in an incognito window.
- **Squarespace “parked” or “redirect” on the domain**  
  Make sure the domain is not set to “Redirect to Squarespace site” or similar; it should only use the DNS records above so GitHub can serve the site.

---

## Updating the site later

After you change files in the project folder:

```bash
cd /Users/kyle/birth-certificate-demo
git add .
git commit -m "Describe your changes"
git push
```

GitHub Pages will redeploy automatically; the live site and your custom domain will update in a minute or two.
