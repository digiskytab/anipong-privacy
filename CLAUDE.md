# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains the static website for **dotTreeSoft** (https://dottreesoft.com), a software company that develops AI-powered mobile applications. The primary product is **Nano Photo** (formerly known as "Anipong"), an AI photo-to-anime style conversion app available on both iOS App Store and Google Play Store.

## Site Architecture

The website is structured as a multi-page static HTML site with the following hierarchy:

```
/                           # Root homepage (dotTreeSoft company site)
├── anipong/                # Nano Photo/Anipong product page
│   ├── notice/             # App release notices and announcements
│   └── privacy-policy/     # Privacy policy page
├── robots.txt              # SEO crawler directives
└── sitemap.xml             # XML sitemap for search engines
```

### Key Pages and Their Purposes

- **index.html** (root): Company homepage with navigation to Company, Product, and Contact sections. Features the Nano Photo app as the main product with app icon overlay.

- **anipong/index.html**: Product landing page for Nano Photo app featuring:
  - App Store and Google Play Store badges with QR codes
  - Screenshot gallery (11 images) with horizontal scroll
  - Promotional image with modal enlargement functionality
  - Links to Notice and Privacy Policy pages
  - Detailed product description explaining the transition from Anipong to Nano Photo with Nano Banana AI engine

- **anipong/notice/index.html**: Release announcements and version history displayed in reverse chronological order with styled notice cards

- **anipong/privacy-policy/index.html**: Privacy policy detailing third-party services (Firebase, Replicate AI) and data retention policies. This page uses `noindex, nofollow` meta tags.

## SEO Configuration

The site implements comprehensive SEO optimization:

- **Meta tags**: Each page includes Open Graph and Twitter Card meta tags for social media sharing
- **Structured data**: JSON-LD schema for Organization (homepage) and MobileApplication (product page)
- **robots.txt**: Allows crawling of all pages except `/anipong/privacy-policy/` and hidden files
- **sitemap.xml**: Contains 3 URLs with priorities (homepage: 1.0, product: 0.9, notice: 0.7)
- **Canonical URLs**: All pages include canonical link tags

## Styling Approach

All HTML pages use inline `<style>` tags with:
- Responsive design using media queries
- Mobile-first approach with viewport meta tags
- CSS for navigation bars, galleries, modals, and QR code sections
- Store badge styling with disabled state support (grayscale filter)
- Gallery implemented with horizontal scroll (`overflow-x: auto`)

## Image Assets

The repository contains two categories of images:

1. **Branding assets**: Company logos (`dottree_w_logo.png`, `dottree_b_logo.png`), app icon (`app_icon.png`)
2. **Product screenshots**: 11 app screenshots (image1.png through image11.png) in the anipong directory
3. **Store badges**: App Store SVG badge and Google Play Store PNG badge
4. **Promotional images**: Feature graphic for Play Store listing

**Note**: QR codes are dynamically generated via external API (https://api.qrserver.com) rather than stored as static files.

## App Store Links

- **iOS App Store**: https://apps.apple.com/kr/app/anipong-애니퐁-ai-사진-애니메-스타일/id6748384896
- **Google Play Store**: https://play.google.com/store/apps/details?id=com.dottreesoft.anipong&pcampaignid=web_share

## Development Workflow

This is a static site with no build process. To work with the site:

1. **Previewing changes**: Open HTML files directly in a browser, or use a local web server:
   ```bash
   python3 -m http.server 8000
   # Then visit http://localhost:8000
   ```

2. **Testing links**: Ensure all relative paths work correctly (../ for parent directory navigation)

3. **Image optimization**: When adding new images, ensure they are appropriately sized for web delivery to maintain page load performance

4. **SEO updates**: When adding new pages, remember to update:
   - sitemap.xml (add new URL with appropriate priority and changefreq)
   - robots.txt (if the page should have special crawl rules)

## Git Workflow

The repository uses a simple main branch workflow. Recent commits show:
- App content updates (new versions, promotional images)
- Google Play Store integration
- SEO improvements

When committing, use descriptive messages that explain the content changes (e.g., "Add Google Play Store support with QR code and update to v1.1.3").

## Important Conventions

1. **App naming**: The app has undergone a rebrand from "Anipong" to "Nano Photo". URLs still use `/anipong/` for backward compatibility, but content refers to "Nano Photo".

2. **Version information**: The product page explains the version status across platforms (iOS App Store version vs. Google Play Store version).

3. **External dependencies**: QR codes, store badges, and analytics depend on external services. No local JavaScript or CSS frameworks are used.

4. **Contact information**: All inquiries go to contact@dottreesoft.com (referenced in privacy policy and contact section).
