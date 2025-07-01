# 📘 Etappe 4 – Dokumentation mit MkDocs + Material

!!! info "Ziel dieser Etappe"

     Auf dieser Etappe deiner *Route* lernst du, wie du ein eigenes Dokumentationsprojekt mit **MkDocs** und dem beliebten Theme **Material for MkDocs** aufsetzt – lokal und öffentlich über **GitHub Pages**.

    MkDocs ist ein statischer Website-Generator, der speziell für technische Dokumentationen gedacht ist. Du schreibst in Markdown und erhältst eine elegante Webseite – ideal für Teams, Projekte oder Lernpfade wie diesen.

    Im Rahmen des Moduls **324** führen wir zwei bestehende Algorithmen-Projekte zusammen.
    Da das **Frontend** über **Netlify** und das **Backend** über einen **Ubuntu-Server** betrieben wird, war eine zentrale, leicht zugängliche Dokumentation notwendig.

    Damit sich alle Beteiligten entlang der gleichen *Route* bewegen, wurde diese Dokumentation erstellt und via **GitHub Pages** veröffentlicht.


    Die wichtigsten Merkmale von MkDocs:

    ✅ **Einfacher Einstieg**: Du schreibst deine Inhalte in Markdown (`.md`) – leicht zu lernen und schnell zu schreiben.

    📁 **Struktur**: Die Seiten liegen in einem `docs/`-Verzeichnis. Die Navigation steuerst du über eine `mkdocs.yml`.

    🎨 **Design & Themes**: MkDocs bringt ein modernes Standard-Theme mit. Besonders beliebt ist das **Material for MkDocs**.

    🚀 **Live-Vorschau**: Mit `mkdocs serve` startest du einen lokalen Entwicklungsserver, der Änderungen automatisch anzeigt.

    🛠️ **Deployment**: Ideal zur Veröffentlichung auf **GitHub Pages** mit dem Befehl `mkdocs gh-deploy`.

---

## Voraussetzungen

!!! tip "Du brauchst"

    - Python 3.x installiert
    - GitHub-Account
    - Git & VS Code empfohlen

---

## 1. MkDocs & Material installieren

Installiere MkDocs und das Material-Theme mit:

```bash
python -m pip install --upgrade pip
python -m pip install mkdocs-material --user
```

---

## 2. Projektstruktur anlegen

Starte ein neues Projekt:

```bash
mkdocs new mein-projekt
cd mein-projekt
```

Struktur:

```
mein-projekt/
├── docs/
│   └── index.md
└── mkdocs.yml
```

---

## 3. `mkdocs.yml` konfigurieren

```yaml
site_name: Mein Projekt
theme:
  name: material
  language: de
  palette:
    scheme: default
    primary: blue
    accent: light blue
markdown_extensions:
  - admonition
  - attr_list
  - toc:
      permalink: true
  - pymdownx.superfences
  - pymdownx.emoji
  - pymdownx.details
```

---

## 4. Lokale Vorschau starten

```bash
python -m mkdocs serve
```

👉 Öffne `http://127.0.0.1:8000` im Browser

---

## 5. Deployment auf GitHub Pages

1. Repository auf GitHub erstellen
2. Projekt pushen
3. GitHub Pages aktivieren (Branch: `gh-pages`)
4. Deployment ausführen:

```bash
python -m mkdocs gh-deploy
```

---

## Bonus-Tipps

- Nutze `!!! info`, `!!! tip`, `!!! warning` für schöne Hinweise
- Erstelle mehrere `.md`-Dateien unter `docs/` und binde sie über `nav:` im `mkdocs.yml` ein
- Für Emojis einfach `:emoji:` oder Unicode-Symbole verwenden

---

## Weitere Links

- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [MkDocs Doku](https://www.mkdocs.org/)
