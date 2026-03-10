# صفیح — Safiih
### Urdu Poetry Companion

> A beautiful, mobile-first web app for exploring, browsing, and understanding Urdu poetry — built as a single HTML file, powered by GitHub Models (Llama-3.3-70B), with no backend required.

---

## ✨ Features

- **AI Chat** — Ask questions about Urdu poetry, get ghazals explained, learn prosody, translate shers. Powered by Llama-3.3-70B via GitHub Models (free).
- **Browse** — Browse shers, ghazals, nazms, qitas, and rubaiyat from your datasets. Filter by script (Urdu/Roman), poet, or keyword.
- **Taqti (Scansion)** — Algorithmic meter analysis: syllable weights, behr (meter) detection, radeef & qafiya identification.
- **Dictionary** — Built-in curated Urdu poetry glossary with search and autocomplete.
- **Favourites** — Save shers, ghazals, and poems with heart button; persisted in browser storage.
- **Chat History** — Auto-saves and restores conversations across sessions.
- **Zero backend** — Everything runs in a single HTML file in the browser.

---

## 🗂 Repository Structure

```
safiih/
├── index.html              ← Main app (open this in a browser)
├── README.md               ← You are here
├── datasets/
│   ├── README.md           ← How to format and load datasets
│   ├── ds_unified.js       ← Shers dataset (DS_UNIFIED)
│   ├── ds_ghazals.js       ← Ghazals index + text (DS_GHAZALS_INDEX, DS_GHAZALS_TEXT)
│   ├── ds_nazms.js         ← Nazms index + text (DS_NAZMS_INDEX, DS_NAZMS_TEXT)
│   ├── ds_qita.js          ← Qita index + text (DS_QITA_INDEX, DS_QITA_TEXT)
│   ├── ds_rubai.js         ← Rubai index + text (DS_RUBAI_INDEX, DS_RUBAI_TEXT)
│   └── ds_dictionary.js    ← Dictionary (DICTIONARY) and wordlist (POETRY_WORDLIST)
└── docs/
    └── DATASETS.md         ← Full dataset format reference
```

> **Note:** The current `index.html` has datasets embedded inline as JavaScript. The `datasets/` folder shows you how to split them out into separate files for easier editing.

---

## 🚀 How to Use (Locally)

1. **Download** `index.html`
2. **Open** it in any modern browser — no server needed
3. **Enter your GitHub Token** when prompted (free, takes 1 minute — see below)
4. Start chatting about Urdu poetry!

### Getting a GitHub Token (Free)

The app uses **GitHub Models** to access Llama-3.3-70B for free:

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token (classic)**
3. Check only ✓ `models:read` — nothing else needed
4. Copy the token and paste it into the app

Your token is saved only in your browser (`localStorage`) and never sent anywhere except GitHub's API.

---

## 🌐 How to Host on GitHub Pages

1. Fork or upload this repo to GitHub
2. Go to your repo → **Settings** → **Pages**
3. Under **Source**, select `main` branch → `/ (root)`
4. Click **Save**
5. Your app will be live at `https://yourusername.github.io/safiih/`

---

## 📦 Working with Separate Dataset Files

Currently the datasets are embedded inside `index.html`. If you want to edit them separately (recommended for large datasets), you can extract them into the `datasets/` folder and load them via `<script>` tags.

### Step 1 — Extract a dataset from `index.html`

Find the variable declaration inside `<script>` tags in `index.html`, for example:

```js
const DS_UNIFIED = [ ... ];
```

Cut it out and paste it into `datasets/ds_unified.js`.

### Step 2 — Load the file in `index.html`

Add a `<script>` tag in the `<head>` of `index.html` **before** the main `<script>` block:

```html
<script src="datasets/ds_unified.js"></script>
<script src="datasets/ds_ghazals.js"></script>
<script src="datasets/ds_nazms.js"></script>
<script src="datasets/ds_qita.js"></script>
<script src="datasets/ds_rubai.js"></script>
<script src="datasets/ds_dictionary.js"></script>
```

### Step 3 — Remove the inline declarations from `index.html`

Delete the original `const DS_UNIFIED = [...]` etc. from inside `index.html` to avoid duplicate variable errors.

> ⚠️ If you're opening `index.html` directly from your filesystem (using `file://`), some browsers block loading of external `.js` files for security. In that case, either use a local server (`npx serve .`) or keep datasets embedded.

---

## 📋 Dataset Variables Reference

| Variable | Type | Used For |
|---|---|---|
| `DS_UNIFIED` | `Array<Sher>` | Shers (couplets) browser + random chip |
| `DS_GHAZALS_INDEX` | `Array<GhazalMeta>` | Ghazals browse list |
| `DS_GHAZALS_TEXT` | `Array<string>` | Full ghazal text (parallel index to above) |
| `DS_NAZMS_INDEX` | `Array<NazmMeta>` | Nazms browse list |
| `DS_NAZMS_TEXT` | `Array<string>` | Full nazm text |
| `DS_QITA_INDEX` | `Array<QitaMeta>` | Qita browse list |
| `DS_QITA_TEXT` | `Array<string>` | Full qita text |
| `DS_RUBAI_INDEX` | `Array<RubaiMeta>` | Rubai browse list |
| `DS_RUBAI_TEXT` | `Array<string>` | Full rubai text |
| `DICTIONARY` | `Object` | Urdu poetry glossary |
| `POETRY_WORDLIST` | `Set<string>` | Known poetry words (spell-check / autocomplete) |

See [`datasets/README.md`](datasets/README.md) for the full schema of each type.

---

## ⚠️ Known Limitations

- **Taqti (scansion) is not 100% accurate.** Urdu prosody is nuanced and context-dependent. Always verify with a human *ustad* or a trusted classical reference.
- The app was built with AI assistance and may have rough edges.
- GitHub Models has rate limits on free tokens — if you hit them, wait a few minutes.
- The dictionary and datasets are manually curated and may be incomplete.

---

## 🤝 Contributing

Pull requests welcome! Good areas to contribute:

- Expand `DS_UNIFIED` with more shers
- Add more ghazals / nazms to the respective datasets
- Improve the taqti (scansion) algorithm
- Fix bugs or UI polish
- Add more entries to `DICTIONARY`

---

## 📄 License

This project is open source. Poetry content belongs to its respective poets and estates — please use respectfully.

---

*Built with ✦ and Urdu poetry.*
