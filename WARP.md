# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a static website for RUSH Process Service, Inc., a process serving company established in 1992 in Portland, Oregon. The site is a single-page application with no build process or backend dependencies.

## Architecture

**Single-Page Static Site**
- `index.html` - Main HTML file containing all content sections (services, about, team, contact)
- `styles.css` - All styling in a single CSS file
- Vanilla JavaScript embedded in HTML for dropdown menu functionality
- No framework or build tools

**Key Design Patterns**
- Fixed header with navigation bar that stays at top of viewport
- Fixed hero banner image positioned below header
- Smooth scrolling to anchor sections (`#services`, `#about`, `#team`, `#contact`)
- All sections use `scroll-margin-top: 129px` to account for fixed header height
- Dropdown menu system using vanilla JS event listeners and CSS transitions

**Content Structure**
- Navigation menu includes: Services, About, Our Team, Contact, and a Tools dropdown
- Tools dropdown contains external links (Status, Service Request PDF, OECI, Oregon Business Registry)
- Organization memberships displayed: NAPPS and OAPS

## Development Commands

Since this is a static site with no build process, development is straightforward:

**Local Development**
```powershell
# Option 1: Python HTTP server (if Python installed)
python -m http.server 8000

# Option 2: Node.js HTTP server (if Node.js installed)
npx http-server -p 8000

# Option 3: PHP built-in server (if PHP installed)
php -S localhost:8000
```

Then navigate to `http://localhost:8000` in your browser.

**File Validation**
```powershell
# Check HTML validity (if validator.nu installed)
curl -H "Content-Type: text/html; charset=utf-8" --data-binary @index.html https://validator.w3.org/nu/?out=text

# Check CSS validity (if csslint installed)
npx csslint styles.css
```

## File Structure

- `index.html` - Main page with all content
- `styles.css` - All styles
- `CNAME` - Domain configuration for GitHub Pages (`www.rushprocessservice.com`)
- `images/` - Image assets (couriers.jpg, map.png, organization logos)
- `media/` - Downloadable files (RUSH FORM 2025.pdf)

## Deployment

This site appears to be hosted on GitHub Pages:
- Domain: www.rushprocessservice.com (configured via CNAME)
- Any push to the main branch will trigger automatic deployment
- No build step required

## Editing Guidelines

**CSS Modifications**
- Fixed header height is 129px - if changed, update `scroll-margin-top` values in sections
- Brand colors: Red `rgb(226, 28, 33)`, Dark gray `#333`, Light gray `#555`
- Container width: 720px (centered)
- Hero banner dimensions: 720px width × 473px height

**HTML Changes**
- When adding new sections, include `scroll-margin-top: 129px` in CSS
- Dropdown menu structure requires: `.dropdown` → `.dropdown-toggle` + `.dropdown-menu` → `li` → `a`
- Team members list uses uppercase styling via CSS

**JavaScript**
- Dropdown functionality is in inline `<script>` tag at end of HTML
- Closes other dropdowns when one is opened
- Closes all dropdowns when clicking outside
