# Forava Legal Documents - GitHub Pages Deployment

This directory contains the legal documents for Forava that will be hosted on GitHub Pages at `forava.com`.

## Files

- `index.html` - Landing page (redirects to privacy.html)
- `privacy.html` - Privacy Policy
- `terms.html` - Terms of Use

## Deployment Instructions

### Option 1: Create New GitHub Repository (Recommended)

1. **Create a new GitHub repository:**
   ```bash
   # On GitHub.com, create new repo: forava-legal
   # Clone it locally
   git clone https://github.com/YOUR_USERNAME/forava-legal.git
   cd forava-legal
   ```

2. **Copy files to the repo:**
   ```bash
   cp /Users/kirangokal/Documents/Forava/Forava02/github-pages/* .
   git add .
   git commit -m "Initial commit: Add legal documents"
   git push origin main
   ```

3. **Enable GitHub Pages:**
   - Go to repository Settings → Pages
   - Source: Deploy from branch `main` / root folder
   - Click "Save"
   - Wait 1-2 minutes for deployment

4. **Configure Custom Domain:**
   - In Settings → Pages → Custom domain
   - Enter: `forava.com`
   - Wait for DNS check

5. **Update DNS at your domain registrar:**
   ```
   A Records (for apex domain forava.com):
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153

   CNAME Record (for www.forava.com):
   YOUR_USERNAME.github.io
   ```

6. **Verify HTTPS:**
   - After DNS propagates (24-48 hours)
   - GitHub will automatically provision SSL certificate
   - Check "Enforce HTTPS" in Pages settings

### Option 2: Use Subdomain (Faster)

If you want to go live immediately without waiting for DNS propagation:

1. Use subdomain instead: `legal.forava.com`
2. Add CNAME record: `legal` → `YOUR_USERNAME.github.io`
3. Update app to use `https://legal.forava.com/privacy` and `https://legal.forava.com/terms`

### Testing

After deployment, verify:
- https://forava.com (or YOUR_USERNAME.github.io)
- https://forava.com/privacy
- https://forava.com/terms

All should load correctly with HTTPS.

## File Structure

```
forava-legal/
├── index.html          # Landing page (auto-redirects)
├── privacy.html        # Privacy Policy
├── terms.html          # Terms of Use
└── README.md          # This file
```

## URLs in App

The iOS app loads these documents from:
- Privacy: `https://forava.com/privacy`
- Terms: `https://forava.com/terms`

Make sure these exact URLs work after deployment.

## Maintenance

To update legal documents:
1. Edit the HTML files in this directory
2. Commit and push changes
3. GitHub Pages auto-deploys within 1-2 minutes

## Fallback

The app has fallback logic to load local HTML files if remote URLs fail, ensuring users can always access legal documents even if GitHub Pages is down.
