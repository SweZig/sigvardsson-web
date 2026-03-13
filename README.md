# sigvardsson.org — Astro 2026 v2.0

## Ändringar i v2.0

### ✅ Nya funktioner
1. **Originallogotyper** — S_blue-trans.png (header), S_white.png (footer/hero), S_blue.png
2. **Global 100 Awards** — 2024, 2025 & 2026 visas i header, hero och footer
3. **Tvåspråkighet (SV/EN)** — Hela sajten på svenska och engelska via en CSS-klass-metod
4. **Sammanslagen tjänstesida** — `/services/` ersätter `/capabilities/` och `/retail-optimering/`
5. **Strukturerad tjänsteportfölj** — 3 kategorier: Retail Optimering, Teknologi & System, Rådgivning & Strategi

### 🔀 URL-ändringar & SEO
| Gammal URL | Ny URL | Typ |
|---|---|---|
| `/capabilities/` | `/services/` | 301 redirect |
| `/retail-optimering/` | `/services/` | 301 redirect |
| `/Contact` | `/Contact/` | 301 redirect |

Alla redirects är konfigurerade i **vercel.json**, **public/_redirects** (Netlify) och via meta-refresh i sidfilerna.

---

## Hur språkväxling fungerar

Implementerat med ren CSS + localStorage:

```html
<!-- I HTML -->
<span class="sv-text">Svensk text</span>
<span class="en-text">English text</span>
```

```css
/* I Layout.astro */
[data-lang="sv"] .en-text { display: none !important; }
[data-lang="en"] .sv-text { display: none !important; }
```

Språkvalet sparas i `localStorage` med nyckeln `scg-lang`. Standard är `sv`.

**Lägga till ny text:** Lägg alltid till BOTH `sv-text` och `en-text` spans.

---

## Lokal utveckling

```powershell
cd sigvardsson
npm install
npm run dev
```

Dev-server: http://localhost:4321

---

## Deploy

### Vercel (rekommenderat)
1. Gå till vercel.com → Add New Project → importera GitHub-repo
2. Vercel känner igen Astro automatiskt
3. Custom domain: www.sigvardsson.org
4. `vercel.json` med alla redirects är inkluderad

### GitHub Pages
1. Repo Settings → Pages → Source: GitHub Actions
2. `.github/workflows/deploy.yml` bygger automatiskt vid push till main
3. Lägg till `public/CNAME` med innehållet: `www.sigvardsson.org`

### Netlify
- Build command: `npm run build`
- Publish directory: `dist`
- `public/_redirects` hanterar redirects automatiskt

---

## Filstruktur

```
src/
  layouts/
    Layout.astro          # Huvud-layout, CSS-variabler, språksystem
  components/
    Header.astro          # Sticky header, nav, Global100-badges, language toggle
    Footer.astro          # Footer med wave, kolumner, awards
  pages/
    index.astro           # Startsida
    services/index.astro  # Samlad tjänstesida (3 kategorier, 16 tjänster)
    what-we-do/           # Tre pelare
    our-process/          # 5-stegsprocess
    our-people/           # Team (platshållare — fyll i riktigt innehåll)
    customer-satisfaction/ # NPS & korrelationsanalys
    Contact/index.astro   # Kontaktformulär
    capabilities/         # SEO-redirect → /services/
    retail-optimering/    # SEO-redirect → /services/
    sitemap.xml.astro
    404.astro

public/
  images/
    logos/                # S_blue-trans.png, S_blue.png, S_white.png
    awards/               # global_100_2024.png, 2025.png, 2026.png
  robots.txt
  _redirects              # Netlify redirects
```

---

## Nästa steg (prioriterade)

| # | Åtgärd | Prioritet |
|---|---|---|
| 1 | Koppla Google Analytics — avkommentera i Layout.astro | Hög |
| 2 | Koppla Google Search Console + skicka in /sitemap.xml | Hög |
| 3 | Fyll i riktiga teammedlemmar på Our People | Hög |
| 4 | Koppla kontaktformuläret (Netlify Forms, Formspree) | Hög |
| 5 | Komplettera "Perfekt Feedback" med riktigt innehåll | Medel |
| 6 | Lägg till kundlogotyper/citat på customer-satisfaction | Medel |
| 7 | Verifiera alla 301-redirects med Screaming Frog | Medel |
| 8 | Testa Core Web Vitals med Lighthouse | Låg |

---

## Brand guidelines

### Typografi
- **Rubriker:** Chakra Petch Medium 500
- **Brödtext:** Nunito ExtraLight 200

### Färger
```css
--color-navy:       #010D60
--color-navy-mid:   #1A277A
--color-navy-lite:  #3D4893
--color-blue:       #2A4EA9
--color-blue-mid:   #4867B6
--color-blue-lite:  #90A2CF
--color-off-white:  #F5F6FA
```

---

*sigvardsson.org — Astro v2.0 — Mars 2026*
