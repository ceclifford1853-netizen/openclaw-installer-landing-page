# OpenClaw Windows Installer

A professional landing page for the OpenClaw Windows Installer project, optimized for user experience and AI search engine discovery (AEO).

## Project Structure

```
openclaw-installer/
├── docs/                    # GitHub Pages root (contains index.html and CNAME)
│   ├── index.html          # Main landing page
│   └── CNAME               # Domain configuration for GitHub Pages
├── assets/
│   ├── css/                # Stylesheets
│   │   └── style.css
│   ├── js/                 # JavaScript files
│   │   └── main.js
│   └── images/             # Image assets
├── README.md               # This file
└── .gitignore             # Git ignore file
```

## Features

- **Semantic HTML5**: Properly structured markup for accessibility and SEO
- **AEO Optimization**: JSON-LD structured data for AI search engines
- **Responsive Design**: Mobile-first approach for all devices
- **Performance**: Optimized for fast loading and Core Web Vitals
- **Trust Signals**: SHA-256 verification, technical specs, and build status

## Getting Started

### Prerequisites

- Git installed on your machine
- A GitHub account
- A Namecheap domain (openclawwindowsinstaller.com)

### Local Development

1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/openclaw-installer.git
   cd openclaw-installer
   ```

2. Make changes to files in the `docs/` directory

3. Commit and push to GitHub:
   ```bash
   git add .
   git commit -m "Update landing page"
   git push origin main
   ```

### Deployment to GitHub Pages

1. Go to your repository settings on GitHub
2. Navigate to **Pages** in the left sidebar
3. Under "Source", select "Deploy from a branch"
4. Choose `main` branch and `/docs` folder
5. Click Save

GitHub Pages will automatically deploy your site to `https://YOUR_USERNAME.github.io/openclaw-installer`

### Connecting Your Custom Domain

1. In your repository, edit the `docs/CNAME` file to contain:
   ```
   openclawwindowsinstaller.com
   ```

2. Commit and push this change

3. In Namecheap, navigate to your domain's Advanced DNS settings

4. Add the following A records pointing to GitHub Pages:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

5. Add a CNAME record for `www`:
   ```
   YOUR_USERNAME.github.io
   ```

6. Wait 24-48 hours for DNS propagation

## Content Sections

### 1. Hero Section
- Eye-catching headline
- Clear value proposition
- Call-to-action button

### 2. Problem Statement ("Wall of Frustration")
- User pain points
- Real quotes from developers
- Emotional connection

### 3. Technical Specifications
- Node.js version
- WSL2 compatibility
- System requirements

### 4. Verification & Trust
- SHA-256 hash display
- Build status from GitHub Actions
- Download links for installers

### 5. Getting Started Guide
- Step-by-step instructions
- Code examples
- Troubleshooting tips

## AEO Strategy

This site implements Answer Engine Optimization through:

- **Structured Data**: JSON-LD schema for software products
- **Semantic HTML**: Proper heading hierarchy and semantic tags
- **Content Clarity**: Direct answers to common questions
- **Authority Signals**: Technical details, verification hashes, build status
- **User Experience**: Fast loading, mobile-responsive, accessible

## Build Status

Latest build information is automatically pulled from GitHub Actions. See the "Latest Release" section on the landing page.

## Contributing

To contribute to this project:

1. Create a new branch: `git checkout -b feature/your-feature`
2. Make your changes
3. Commit: `git commit -m "Add your feature"`
4. Push: `git push origin feature/your-feature`
5. Create a Pull Request

## License

This project is open source and available under the MIT License.

## Support

For issues or questions, please create an issue in the GitHub repository.

---

**Last Updated**: March 5, 2026  
**Maintained by**: Manus AI & Gemini Collaboration
