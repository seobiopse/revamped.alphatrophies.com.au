# Alpha Trophies — Revamped Frontend

**3-page redesign** of [alphatrophies.com.au](https://alphatrophies.com.au) built as a static HTML/CSS/JS prototype. Covers Homepage, Product Listing, and Product Detail — same design system across all three, wired for inter-page navigation.

🔗 **Live preview:** [seobiopse.github.io/revamped.alphatrophies.com.au](https://seobiopse.github.io/revamped.alphatrophies.com.au/)

---

## Pages

| File | URL | Description |
|---|---|---|
| `index.html` | `/` | Homepage — hero, category tabs, occasion grid, personalisation, FAQ |
| `product-listing.html` | `/product-listing.html` | Trophies listing — filter sidebar, product grid, comparison table, reviews |
| `product-detail.html` | `/product-detail.html` | Product detail — size selector, live engraving preview, related products |
| `alpha_devnotes_v5_handoff.html` | `/alpha_devnotes_v5_handoff.html` | Developer hand-off — before/after audit, code evidence, SEO·AEO·GEO breakdown |

---

## Navigation

### Homepage → Product Listing
- **"Trophies"** in the top nav bar
- **"Browse all trophies →"** in the mega menu dropdown
- **"Shop trophies"** hero CTA
- **Sport category cards** — AFL, Soccer, Cricket, Netball, Swimming, Dance, Golf etc.
- **"Browse all trophies"** in the category tabs section

### Homepage → Product Detail
- **Recommended product cards** — Netball Econo Medal, Glass Peak Budget Award, Legacy Circle Medal, Sunrise Medal, Traditional Medal

### Product Listing → Product Detail
- **Any product card** — all 30 cards with "View Product"

### Product Detail → Product Listing
- **Breadcrumb "Trophies"**
- **"View all Dance Trophies →"** in related products

### Product Detail → Homepage
- **Breadcrumb "Home"**

### All pages → Homepage
- **ALPHATROPHIES logo** (top-left of every page)

### All pages → Dev Notes
- **"DEV NOTES v5"** in the footer copyright bar (dotted underline)

---

## Design System

| Token | Value |
|---|---|
| Primary navy | `#1A2344` |
| Gold accent | `#AD7D35` |
| Gold light | `#C8953E` |
| Font | Poppins (300/400/500/600/700) |
| Border radius | 8px (cards), 12px (modals) |
| Flat-rate shipping | $9.90 |

---

## What Changed vs the Live Site

### SEO
- H1 above the fold on all 3 pages (existing: H1 buried mid-page or in sidebar)
- Heading hierarchy corrected — mega menu `<h2>` → `<p class="mp-title">` (was appearing before the page H1 in DOM order)
- Meta titles ≤60 chars and descriptions ≤160 chars on all pages (all 3 were over on the live site)
- Full schema stack per page — see table below
- `alt` text follows rule: `"Explore [Product] starting from [Price]"` on all product images
- `title` attribute: `"Buy Best [Product] Online from Alpha Trophies Australia from [Price]"`
- `llm.txt` footer link on all pages
- Mega menu with 88 sport sub-links — crawlable `<a href>` replacing `onclick="ShowTab()";return false` intercepts

### AEO
- 10-question FAQPage JSON-LD on homepage and listing (5 product + 5 business)
- 5-question product FAQPage JSON-LD on product detail
- Trophy type comparison HTML `<table>` on listing page
- "How ordering works" 4-step process block

### GEO
- Stat bar copy in DOM ("40+ years", "10,000+ products", "4.9 stars from 169 reviews")
- Organization JSON-LD with 3 Place objects (Melbourne, Adelaide, Sydney)
- Verbatim, attributed, dated review quotes
- `llm.txt` footer link signals AI crawl permission

### Schema per page

| Page | Schema types |
|---|---|
| Homepage | WebSite (SearchAction) · Organization (3× Place, aggregateRating) · ItemList (4 products + Offer) · FAQPage (10 Q&As) |
| Product Listing | CollectionPage · Organization (aggregateRating 4.9/169) · FAQPage (10 Q&As) · BreadcrumbList |
| Product Detail | Product · Offer (price 7.35 AUD, InStock) · AggregateRating (4.9/169) · FAQPage (5 Q&As) · BreadcrumbList |

### Bug fixes (existing site)
- Dual `<h1>` on product detail (`"FREE LOGO CENTRE"` was tagged `<h1>` — demoted to `<h3>`)
- Title tag trailing pipe on PDPs (`"Product Name |"` — `{site_name}` variable was not resolving)
- `<span class="size-guide">Size guide →</span>` was a dead click element — now a working modal with size comparison table and bar chart
- Footer CSS class collision — `.sc` used for both store city names and sport category cards, causing "Melbourne" to render as a full dark 3:4 ratio card (black box). Fixed by renaming footer elements to `.st-city`
- Twitter card tags missing on listing and detail pages. Homepage had `twitter:card` but was missing `title`, `description`, `image`, `site`
- All product images had `alt=""` on listing and detail pages

---

## File Structure

```
/
├── index.html                      # Homepage
├── product-listing.html            # Trophies listing page
├── product-detail.html             # Product detail page
├── alpha_devnotes_v5_handoff.html  # Developer hand-off document
└── README.md
```

---

## Dev Notes

The `alpha_devnotes_v5_handoff.html` file is a full developer hand-off document covering all 3 pages. It includes:

- **Before / after screenshot crops** with annotated panels (amber = issue, navy = fix)
- **Real code evidence** extracted from the existing HTML files via Python audit
- **SEO · AEO · GEO signal cards** per page explaining the impact of each change
- **Deployment checklist** — 15 items with page scope and owner
- **Heading hierarchy**, schema gaps, onclick audit results, image alt audit

---

## Prepared by

**Girish Kumar G** | Programmatic SEO Manager · Father of SEO · VDS Creator  
Impacteers (Genrichers Innovation Pvt Ltd) · Chennai  
[seobiopse.com](https://seobiopse.com) · 2026
