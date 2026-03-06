# OpenClaw Windows Installer - Deployment Guide

This guide walks you through deploying the OpenClaw Windows Installer landing page to GitHub Pages and connecting your Namecheap domain.

## Prerequisites

- GitHub account (free)
- Namecheap domain: `openclawwindowsinstaller.com`
- Git installed on your machine
- Text editor or IDE

## Step 1: Create a GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in to your account
2. Click the **+** icon in the top-right corner and select **New repository**
3. Configure your repository:
   - **Repository name**: `openclaw-installer`
   - **Description**: "Professional landing page for OpenClaw Windows Installer"
   - **Visibility**: Public (required for free GitHub Pages)
   - **Initialize with**: None (we'll push existing code)
4. Click **Create repository**

## Step 2: Push Code to GitHub

### Option A: Using Git Command Line

1. Open your terminal/command prompt
2. Navigate to the project directory:
   ```bash
   cd /home/ubuntu/openclaw-installer
   ```

3. Configure Git (if not already done):
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

4. Add the remote repository:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/openclaw-installer.git
   ```

5. Rename branch to main (if needed):
   ```bash
   git branch -M main
   ```

6. Add all files:
   ```bash
   git add .
   ```

7. Create initial commit:
   ```bash
   git commit -m "Initial commit: OpenClaw landing page with AEO optimization"
   ```

8. Push to GitHub:
   ```bash
   git push -u origin main
   ```

### Option B: Using GitHub Desktop

1. Download and install [GitHub Desktop](https://desktop.github.com)
2. Sign in with your GitHub account
3. Click **File** → **Clone Repository**
4. Select your newly created `openclaw-installer` repository
5. Choose a local path and click **Clone**
6. Copy the project files into the cloned directory
7. In GitHub Desktop, you'll see all changes listed
8. Enter a commit message: "Initial commit: OpenClaw landing page"
9. Click **Commit to main**
10. Click **Publish branch**

## Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (gear icon)
3. In the left sidebar, click **Pages**
4. Under "Source", select:
   - **Branch**: `main`
   - **Folder**: `/docs`
5. Click **Save**

GitHub will display a message: "Your site is published at `https://YOUR_USERNAME.github.io/openclaw-installer`"

## Step 4: Configure Custom Domain (Namecheap)

### Part A: Update CNAME File in Repository

The `docs/CNAME` file already contains `openclawwindowsinstaller.com`. If you need to update it:

1. Edit `docs/CNAME` to contain only:
   ```
   openclawwindowsinstaller.com
   ```

2. Commit and push:
   ```bash
   git add docs/CNAME
   git commit -m "Configure custom domain"
   git push origin main
   ```

### Part B: Configure DNS Records in Namecheap

1. **Log in to Namecheap**:
   - Go to [namecheap.com](https://namecheap.com)
   - Click your profile icon → **Dashboard**
   - Find `openclawwindowsinstaller.com` and click **Manage**

2. **Navigate to Advanced DNS**:
   - Click the **Advanced DNS** tab
   - You'll see existing DNS records

3. **Add GitHub Pages A Records**:
   - Click **Add New Record**
   - Select **A Record** from the dropdown
   - For **Host**: Enter `@`
   - For **Value**: Enter the first GitHub IP: `185.199.108.153`
   - Set **TTL**: 3600
   - Click the checkmark to save

4. **Add Additional A Records** (repeat step 3 for each):
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`

5. **Add CNAME Record for www**:
   - Click **Add New Record**
   - Select **CNAME Record**
   - For **Host**: Enter `www`
   - For **Value**: Enter `YOUR_USERNAME.github.io`
   - Set **TTL**: 3600
   - Click the checkmark to save

6. **Add AAAA Records** (optional, for IPv6):
   - Click **Add New Record**
   - Select **AAAA Record**
   - For **Host**: Enter `@`
   - For **Value**: Enter `2606:50c0:8000::153`
   - Repeat for: `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`

### DNS Configuration Summary

Your final DNS configuration should look like:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A | @ | 185.199.108.153 | 3600 |
| A | @ | 185.199.109.153 | 3600 |
| A | @ | 185.199.110.153 | 3600 |
| A | @ | 185.199.111.153 | 3600 |
| CNAME | www | YOUR_USERNAME.github.io | 3600 |

## Step 5: Verify DNS Configuration

1. **Wait for DNS Propagation** (24-48 hours typically, but often faster)

2. **Check DNS Status**:
   ```bash
   nslookup openclawwindowsinstaller.com
   ```
   
   You should see the GitHub IP addresses listed.

3. **Test Your Domain**:
   - Open your browser
   - Navigate to `https://openclawwindowsinstaller.com`
   - You should see your landing page

4. **Enable HTTPS** (GitHub Pages does this automatically):
   - In your repository **Settings** → **Pages**
   - Check **Enforce HTTPS** (if available)

## Step 6: Update GitHub Pages Settings (Final)

1. Go to your repository **Settings** → **Pages**
2. Verify:
   - **Source**: `main` branch, `/docs` folder
   - **Custom domain**: `openclawwindowsinstaller.com`
   - **Enforce HTTPS**: ✓ Checked
3. Click **Save**

## Troubleshooting

### Domain Not Resolving

- **Wait longer**: DNS changes can take up to 48 hours
- **Clear cache**: Flush your DNS cache or use a different network
- **Check records**: Verify all A records and CNAME are correctly entered in Namecheap
- **Verify CNAME file**: Ensure `docs/CNAME` contains exactly `openclawwindowsinstaller.com`

### HTTPS Not Working

- GitHub Pages automatically provides HTTPS for custom domains
- Wait 24 hours after DNS configuration for the certificate to be issued
- Check **Settings** → **Pages** → **Enforce HTTPS** is available and checked

### Site Shows 404

- Verify the `docs/` folder contains `index.html`
- Check that GitHub Pages is enabled in repository settings
- Ensure branch is set to `main` and folder is `/docs`

### Slow Page Load

- Check browser console for failed asset requests
- Verify all CSS and JS files are loading correctly
- Use Google PageSpeed Insights to identify optimization opportunities

## Maintenance & Updates

### Making Changes

1. Edit files locally
2. Commit changes:
   ```bash
   git add .
   git commit -m "Update: [describe changes]"
   git push origin main
   ```
3. Changes deploy automatically within seconds

### Updating Build Status

The build status page (`docs/build-status.html`) can be updated with latest GitHub Actions data:

1. Edit `docs/build-status.html`
2. Update the build information in the relevant sections
3. Commit and push to deploy

### Monitoring Performance

- Use [Google Analytics](https://analytics.google.com) for traffic insights
- Monitor [Google Search Console](https://search.google.com/search-console) for SEO performance
- Check [PageSpeed Insights](https://pagespeed.web.dev) for performance metrics

## Security Considerations

- Keep your GitHub token/credentials secure
- Enable two-factor authentication on your GitHub account
- Regularly update dependencies (if using any)
- Monitor your domain for unauthorized changes

## Next Steps

1. ✅ Create GitHub repository
2. ✅ Push code to GitHub
3. ✅ Enable GitHub Pages
4. ✅ Configure custom domain in Namecheap
5. ✅ Wait for DNS propagation
6. ✅ Verify site is live at `openclawwindowsinstaller.com`
7. Set up Google Analytics for tracking
8. Submit sitemap to Google Search Console
9. Monitor build status and update as needed

## Support Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Namecheap DNS Help](https://www.namecheap.com/support/knowledgebase/)
- [GitHub Community Support](https://github.community)

---

**Last Updated**: March 5, 2026  
**Maintained by**: Manus AI & Gemini Collaboration
