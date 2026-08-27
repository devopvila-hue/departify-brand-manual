# DEPARTIFY · Manual de Marca

Manual de marca oficial de **DEPARTIFY** (departify.app), v1.0 · 2026.

## Contenido

- `index.html` — manual completo (12 secciones, 34 páginas A4, con CSS responsive)
- `manual-departify.pdf` — PDF para descargar
- `manual-assets/` — logos oficiales en PNG
- `assets/` — logos vectoriales en SVG (variantes de color)
- `brand/` — **assets de marca descargables para humanos y agentes** (logos SVG + manifiesto JSON + página de brand)

## Brand assets · URL pública

Una vez desplegado en Vercel, los assets están disponibles en:

| Recurso | URL |
| --- | --- |
| Página de marca (HTML) | `https://departify-brand-manual.vercel.app/brand/` |
| Logo principal (SVG, gradiente) | `https://departify-brand-manual.vercel.app/brand/logo.svg` |
| Logo monocromo lime | `https://departify-brand-manual.vercel.app/brand/logo-lime.svg` |
| Logo monocromo forest | `https://departify-brand-manual.vercel.app/brand/logo-forest.svg` |
| Logo monocromo blanco | `https://departify-brand-manual.vercel.app/brand/logo-white.svg` |
| Logo monocromo negro | `https://departify-brand-manual.vercel.app/brand/logo-black.svg` |
| Manifiesto JSON (para LLMs) | `https://departify-brand-manual.vercel.app/brand/manifest.json` |

## Cómo incluir el logo en tu output (para agentes y scripts)

```json
{
  "brand": "DEPARTIFY",
  "logo_url": "https://departify-brand-manual.vercel.app/brand/logo.svg",
  "logo_white_url": "https://departify-brand-manual.vercel.app/brand/logo-white.svg",
  "tagline": "Te devolvemos tiempo",
  "color_accent": "#D8FF62",
  "color_ink": "#0A0C08"
}
```

## Estructura

```
.
├── index.html              # Manual web (con CSS responsive)
├── manual-departify.pdf    # PDF imprimible (34 páginas A4)
├── manual-assets/          # Logos PNG originales
│   ├── departify-d-symbol.png
│   ├── departify-d-flat.png
│   ├── departify-logo-with-wordmark.png
│   ├── departify-wordmark-on-light.png
│   └── departify-brand-meta.gif
├── assets/                 # Logos SVG vectoriales
│   ├── departify-d-gradient.svg
│   ├── departify-d-lime.svg
│   ├── departify-d-forest.svg
│   ├── departify-d-white.svg
│   └── departify-d-black.svg
└── brand/                  # Assets públicos para descarga
    ├── index.html          # Página "brand assets" navegable
    ├── logo.svg            # Logo principal (con gradiente de marca)
    ├── logo-lime.svg
    ├── logo-forest.svg
    ├── logo-white.svg
    ├── logo-black.svg
    └── manifest.json       # Metadatos estructurados para LLMs
```

## Brand

- **Logo:** marca D con split diagonal lime→verde
- **Colores:** Accent Lime `#D8FF62` · Background Ink `#0A0C08` · Forest `#0E3D1A`
- **Tipografía:** Inter (sans/display) + JetBrains Mono
- **Tagline:** "Te devolvemos tiempo"

## Visualización local

```bash
# Abrir el manual en el navegador
open index.html

# Servidor local
python3 -m http.server 8000
# luego abre http://localhost:8000

# Ver los brand assets
open brand/index.html
```

## Regenerar el PDF

El HTML está pensado para imprimirse como A4. Para regenerar el PDF:

```bash
python3 -c "
from playwright.sync_api import sync_playwright
import os
CHROMIUM = '/path/to/chrome'
with sync_playwright() as p:
    b = p.chromium.launch(executable_path=CHROMIUM, headless=True)
    pg = b.new_page()
    pg.goto('file://' + os.path.abspath('index.html'), wait_until='networkidle')
    pg.wait_for_timeout(2000)
    pg.pdf(path='manual-departify.pdf', format='A4',
           margin={'top':'0','right':'0','bottom':'0','left':'0'},
           print_background=True)
    b.close()
"
```

## Made in Spain

DEPARTIFY, S.L. · [departify.app](https://departify.app)
