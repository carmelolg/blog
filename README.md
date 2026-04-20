# Shizuka 静か

Un diario editoriale. Pensieri lenti su design, codice, e quiete.

Costruito con [Hugo](https://gohugo.io/), tema artigianale ispirato all'estetica *shibui*.

---

## Prerequisiti

- [Hugo Extended](https://gohugo.io/installation/) v0.128 o superiore
- Git

```bash
hugo version
```

---

## Setup locale

```bash
git clone https://github.com/USERNAME/jap-blog.git
cd jap-blog
hugo server -D
```

Il flag `-D` include anche i post in stato `draft: true`.
Apri il browser su `http://localhost:1313`.

---

## Struttura del progetto

```
jap-blog/
├── archetypes/         # template per nuovi post
├── assets/css/         # stylesheet principale
├── content/
│   ├── posts/          # articoli del blog
│   ├── about.md        # pagina about
│   └── archive.md      # pagina archivio
├── layouts/            # template Hugo
│   ├── _default/       # baseof, list, single, terms, archive
│   ├── partials/       # head, header, footer, meta
│   └── index.html      # home page
├── static/             # file statici (favicon, ecc.)
├── docs/               # output compilato per GitHub Pages
├── .github/workflows/  # GitHub Actions deploy
└── hugo.toml           # configurazione sito
```

---

## Creare un nuovo post

```bash
hugo new posts/titolo-del-mio-articolo.md
```

Il file viene creato in `content/posts/` con front matter precompilato.
Cambia `draft: false` quando sei pronto a pubblicare.

---

## Build per produzione

```bash
hugo --minify
```

L'output va in `docs/`. Non modificare `docs/` manualmente.

---

## Deploy su GitHub Pages

### Metodo 1: GitHub Actions (raccomandato)

Il workflow `.github/workflows/deploy.yml` pubblica automaticamente ad ogni push su `main`.

**Setup:**
1. Push del repository su GitHub
2. **Settings → Pages → Source → GitHub Actions**
3. Modifica `baseURL` in `hugo.toml`:

```toml
baseURL = "https://USERNAME.github.io/jap-blog/"
```

Da questo momento ogni push su `main` triggera build e deploy automatico.

### Metodo 2: Deploy da directory docs/ (alternativo)

1. Esegui `hugo --minify` localmente
2. Fai commit e push includendo `docs/`
3. **Settings → Pages → Source → Deploy from a branch**
4. Scegli branch `main`, cartella `/docs`

---

## Personalizzazione

### Identità del sito (`hugo.toml`)

```toml
baseURL = "https://USERNAME.github.io/jap-blog/"
title = "Il Tuo Blog"

[params]
  description = "La tua descrizione"
  author = "Il Tuo Nome"
```

### Colori e tipografia

Modifica le CSS custom properties in `assets/css/main.css` nella sezione `1. CSS Custom Properties`.

---

## Decisioni di design

- **Hugo** scelto per performance, tassonomie native, archetypes, e stabilità
- **Nessun tema esterno**: tutto inline, facile da modificare
- **CSS custom properties**: design system centralizzato
- **Fonts**: EB Garamond (body), IBM Plex Sans (UI), IBM Plex Mono (codice)
- **Dark mode**: automatica via `prefers-color-scheme`
- **`publishDir = "docs"`**: output diretto per GitHub Pages

---

## Licenza

MIT — fai ciò che vuoi, ma non togliere il credito se hai trovato questo utile.
