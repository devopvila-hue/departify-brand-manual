# DEPARTIFY · Manual de Marca

Manual de marca oficial de **DEPARTIFY** (departify.app), v1.0 · 2026.

## Contenido

- `index.html` — manual completo (12 secciones, 34 páginas A4)
- `manual-assets/` — logos oficiales (D symbol, lockups)
- `manual-departify.pdf` — PDF para descargar

## Estructura

```
.
├── index.html              # Manual web (con CSS responsive)
├── manual-departify.pdf    # PDF imprimible (34 páginas A4)
└── manual-assets/
    ├── departify-d-symbol.png          # Símbolo D, fondo transparente
    ├── departify-d-flat.png            # Símbolo D plano
    ├── departify-logo-with-wordmark.png  # Símbolo + wordmark sobre transparente
    ├── departify-wordmark-on-light.png   # Wordmark sobre fondo claro
    └── departify-brand-meta.gif          # Brand showcase
```

## Visualización local

```bash
# Opción 1: abrir directamente
open index.html

# Opción 2: servidor local
python3 -m http.server 8000
# luego abre http://localhost:8000
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

## Brand

- **Logo:** marca D con split diagonal lime→verde
- **Colores:** Accent Lime `#D8FF62` · Background Ink `#0A0C08` · Forest `#0E3D1A`
- **Tipografía:** Inter (sans/display) + JetBrains Mono
- **Tagline:** "Te devolvemos tiempo"

## Made in Spain

DEPARTIFY, S.L. · [departify.app](https://departify.app)
