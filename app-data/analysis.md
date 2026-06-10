# SR Engineering Services — Website & Assets Analysis

## Company Overview

**SR Engineering Services (Pvt) Ltd** is a Pakistan-based construction and engineering firm incorporated in September 2022 (SECP CUIN: 0211186). Headquartered in Islamabad (G-13/1), the company provides construction, civil engineering, MEP, infrastructure, and solar services. Key registrations: PEC Licence No. 29689 (Category C5/E), FBR NTN: 9366417-0, KPRA registered.

**Domain:** srengineeringservices.pk  
**LinkedIn:** https://www.linkedin.com/company/sr-engineering-services-private-limited/  
**Leadership:** Engr. Saad Raja (CEO), Engr. Raja Israr Kiyani (MD), Engr. Usayram Sultan (MD)

---

## SR Folder — Branding Assets

| File | Type | Size | Purpose |
|------|------|------|---------|
| Logo.png | Logo | 172 KB | Primary company logo |
| SR Logo.png | Logo | 106 KB | Alternate/smaller logo |
| saad.png | Photo | 896 KB | CEO portrait |
| israr.png | Photo | 829 KB | MD portrait |
| usayram.png | Photo | 929 KB | MD portrait |
| Final SR Profile reduced-updated-2.pdf | PDF | 220 MB | Company profile document (67 pages) |

**Note:** Team photos from this folder are already deployed in the website under `srengineering/images/team/` (identical files). The logos are NOT used on the website — the site currently uses a CSS-based "SR" text logo.

---

## Company Profile PDF Analysis

The 67-page PDF uses **custom embedded fonts** for body text, making most content unreadable via programmatic extraction. Only headers, company metadata (page 3), and vision/mission/goal text (page 4) are properly extractable.

**PDF Table of Contents:**
1. About Information (Page 3)
2. Vision, Mission, Goal (Page 4)
3. Introduction (Pages 5-6)
4. CEO's Message (Page 7)
5. Director's Message (Page 8)
6. Services (Pages 9-10)
7. Organization Chart (Pages 11-12)
8. Staff and Management (Pages 13-14)
9. Machinery and Equipment (Pages 15-18)
10. Company's Experience (Page 19)
11. Projects (Pages 20-62) — individual project detail pages with photos
12. Certifications (Pages 63-66) — scanned certificate images

**Extracted content saved to:** `/content/` folder (12 markdown files matching PDF sections)

---

## Website Structure (srengineering/)

### Tech Stack
- Pure static HTML/CSS/JS (no framework, no build tools)
- Single CSS file: `css/style.css` (40.7 KB)
- Single JS file: `js/main.js` (5 KB, vanilla)
- CNAME: `www.srengineeringservices.pk` (GitHub Pages hosted)
- No package.json, no dependencies

### Pages (9 total)

| Page | File | Size | Purpose |
|------|------|------|---------|
| Home | index.html | 19 KB | Landing page with hero, services overview, stats, featured projects |
| About | about.html | 19 KB | Company overview, vision/mission, quality policy, HSE, timeline, certifications |
| Services | services.html | 21 KB | 7 service categories with detailed descriptions |
| Team | team.html | 15 KB | Leadership (3), management (7), engineers (8 placeholder), HSE (3) |
| Contact | contact.html | 14 KB | Contact form, info cards, map placeholder |
| Projects | projects.html | 17 KB | Portfolio of 12 documented projects with filter tabs |
| Organization | organization.html | 19 KB | Org chart from CEO to site staff |
| Equipment | equipment.html | 11 KB | Equipment tables (civil tools, machinery, electrical, mechanical) |
| Experience | experience.html | 14 KB | Industries served, capabilities, achievements |

### Pages to Keep (5 total)

| Page | File |
|------|------|
| Home | index.html |
| About Us | about.html |
| Services | services.html |
| Team | team.html |
| Contact | contact.html |

### Pages to Remove

- projects.html
- organization.html
- equipment.html
- experience.html

**Also remove:** Any internal links pointing to these pages (from nav, footer, CTAs, etc.)

---

## Planned Changes

### 1. Header — Vertical Center Alignment & Logo Replacement

**Problem:** Nav content is touching the top edge. The CSS text-based "SR" logo box + company name title should be replaced with the actual logo image.

**Changes needed:**
- **CSS (`css/style.css`):** Replace `.nav-logo .logo-icon` styles (the orange 40x40 box) with a `.logo-img` class: `height: 42px; width: auto;`
- **All HTML files (header):** Replace:
  ```html
  <div class="logo-icon" aria-hidden="true">SR</div>
  <div class="logo-text">
    <strong>SR Engineering Services</strong>
    <span>(Pvt) Ltd</span>
  </div>
  ```
  With:
  ```html
  <img src="images/sr-logo.png" alt="SR Engineering Services" class="logo-img">
  ```
- **Copy logo file:** Copy `SR/SR Logo.png` → `srengineering/images/sr-logo.png`
- **Affected files:** All 9 HTML pages (header)

### 2. Footer Logo Replacement

**Problem:** Footer also uses the CSS text box logo.

**Changes needed:**
- **CSS:** Replace `.footer-brand .logo-icon` styles with `.footer-brand .logo-img` class: `height: 44px; width: auto;`
- **All HTML files (footer):** Replace the logo-wrap div contents with:
  ```html
  <div class="logo-wrap">
    <img src="images/sr-logo.png" alt="SR Engineering Services" class="logo-img">
  </div>
  ```
- **Affected files:** All 9 HTML pages (footer)

### 3. LinkedIn URL Update

**Problem:** Current LinkedIn URL is `https://pk.linkedin.com/company/sr-engineering-services`

**Change to:** `https://www.linkedin.com/company/sr-engineering-services-private-limited/`

**Affected files:** All 9 HTML pages (footer social links)

### 4. Add Company Tagline

**From LinkedIn:** "Your Structure Our Excellence"

**Changes needed:** Add tagline below company name/logo where appropriate (e.g., hero section or nav area).

### 5. Team Page — Fix Leadership Card Alignment & Spacing

**Problem:** The 3 leadership cards in the Leadership Team section have misaligned content.

**Changes needed:**
- **CSS:** Add to `.leader-info`:
  ```css
  .leader-info {
    padding: 22px 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  ```

### 5. Team Page — Remove Irrelevant Sections

**Problem:** The Team page has placeholder sections with `[NAME REQUIRED]` for 8 engineers and shows the HSE team separately. The Company Profile PDF only lists the 3 directors (Leadership), 7 management members, and 3 HSE staff. No individual engineer names are provided.

**Changes needed in `team.html`:**
- **KEEP:** Leadership section (3 cards: Saad Raja, Raja Israr, Usayram Sultan — these have real photos)
- **KEEP:** Management section (7 named people — real data from PDF)
- **KEEP:** HSE Team section (3 named people — real data from PDF)
- **REMOVE:** Engineers & Specialists section (all 8 cards are `[NAME REQUIRED]` placeholders)
- **REMOVE:** "Join Our Team" CTA section (optional)

**Real team data (from Company Profile PDF `content/08-staff-and-management.md`):**

Leadership:
- Engr. Saad Raja — CEO
- Engr. Raja Israr Kiyani — Managing Director
- Engr. Usayram Sultan — Managing Director

Management:
- Engr. Malik Adeel Ahmed — Project Director
- Engr. Muhammad Faizan Khalid — Project Manager / BDM (BS Civil Engineering)
- Engr. Moazzam Siddique — Design Manager (BS Civil, MS Structure)
- Bilal Ahmed — Finance Director
- Amir Ayub — Finance Manager (M.COM)
- Engr. Asim Ejaz — Tender & Procurement Manager (BS Civil, MS Project Management)
- Raja Naveed Hussain — Legal Advisor (LLB Honors)

HSE:
- Muhammad Nadeem — HSE Manager (NEBOSH, 10 Years Experience)
- Muhammad Zubair — HSE Engineer (IOSH, 5 Years Experience)
- Hassan Raees — HSE Supervisor (IOSH, 2 Years Experience)

---

## Existing Issues (unchanged)

### Data Discrepancies (LinkedIn vs Website vs PDF)

| Field | LinkedIn | Website | PDF |
|-------|----------|---------|-----|
| Founded | 2021 | "Since 2022" | Sep 2022 (SECP) |
| Building name | Friends Arcade | Cable Plaza | Cable Plaza |
| Website domain | srengineeringservices.com | srengineeringservices.pk | srengineeringservices.com |
| Company size | 51-200 employees | "50+ Expert Engineers" | — |
| Tagline | "Your Structure Our Excellence" | Not used | — |
| LinkedIn URL | /sr-engineering-services-private-limited/ | /sr-engineering-services | /sr-engineering-services |

**Recommended canonical values:**
- Founded: 2022 (matches legal incorporation)
- Address: Use "Cable Plaza" (matches PDF and majority of materials)
- Domain: srengineeringservices.pk (what CNAME points to)
- Tagline: Add "Your Structure Our Excellence" to website
- LinkedIn URL: Use the updated `/sr-engineering-services-private-limited/` everywhere

### Content Placeholders
- **Project images** — All 12+ project cards show `[PROJECT IMAGE REQUIRED]`
- **Client logos** — `[CLIENT LOGOS REQUIRED]` on homepage
- **Workforce quantities** — `[QTY]` on organization page
- **Certification images** — `[CERT IMAGES REQUIRED]`
- **Company photos** — `[IMAGE REQUIRED]` in about/experience sections
- **Google Maps embed** — placeholder on contact page

### Functional Issues
- **Contact form has no backend** — faked with JS
- **Project filter mismatch** — filter tabs (residential, commercial, industrial, infrastructure) don't match card data-category values (institutional, government)
- **Dead social links** — Facebook, Twitter, YouTube point to `#`
- **Nav inconsistency** — Projects, Organization, Equipment, Experience pages not in main nav

### Stat Discrepancies — MUST FIX

The website currently shows inflated numbers. Replace with realistic figures:

| Current (wrong) | Correct (from LinkedIn/PDF) |
|-----------------|----------------------------|
| 200+ Projects Completed | 18+ Projects Completed |
| 50+ Expert Engineers | 51-200 Employees (team) |
| 15+ Years Experience | Est. 2022 (3 Years) |
| 100+ Satisfied Clients | Remove or use realistic number |

These appear on `index.html` (hero stats + stats section). Fix them to reflect reality.

### Missing Technical Elements
- No favicon
- No robots.txt or sitemap.xml
- No Open Graph / social media meta tags
- No structured data (JSON-LD)
- No 404 error page
- No analytics tracking
- Team photos are ~900KB uncompressed PNGs
