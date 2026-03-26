# Cloudflare Pages Deploy

## Connect GitHub Repo

1. Go to https://dash.cloudflare.com
2. Click **Workers & Pages** in the sidebar
3. Click **Create** > **Pages** > **Connect to Git**
4. Select the **rayden2** repo
5. Settings:
   - Project name: `rayden2`
   - Production branch: `main`
   - Build command: (leave empty — static site)
   - Build output directory: `/` (root)
6. Click **Save and Deploy**

## Result

Site will be live at: `https://rayden2.pages.dev`

Every push to main auto-deploys.

## Optional: Custom Domain

If you want a custom subdomain (e.g., rayden.joeycastillo.us):
1. In the Pages project, go to **Custom domains**
2. Add `rayden.joeycastillo.us`
3. Cloudflare handles DNS + SSL automatically
