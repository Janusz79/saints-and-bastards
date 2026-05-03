# Saints & Bastards - Official Website

Sito statico ufficiale della band **Saints & Bastards**.

## 🚀 Tecnologie

- **Vue3** - Framework frontend
- **Vite** - Build tool
- **Node.js** - Runtime

## 📦 Installazione

```bash
npm install
```

## 🔧 Development

```bash
npm run dev
```

Il sito sarà disponibile su `http://localhost:5173`

## 🏗️ Build

```bash
npm run build
```

Genera i file ottimizzati nella cartella `dist/`

## 📤 Deploy

### GitHub Pages

1. Aggiorna il repository URL in `package.json` (sotto "repository")
2. Abilita GitHub Pages nelle impostazioni del repo
3. Esegui:
   ```bash
   npm run deploy
   ```

### Cloudflare Pages

1. Connetti il repo GitHub a Cloudflare Pages
2. Build command: `npm run build`
3. Build output directory: `dist`

### Netlify

1. Connetti il repo GitHub a Netlify
2. Build command: `npm run build`
3. Publish directory: `dist`

## 📁 Struttura

```
saints-and-bastards/
├── src/
│   ├── components/
│   │   ├── Home.vue
│   │   ├── Music.vue
│   │   ├── Tour.vue
│   │   └── Contact.vue
│   ├── App.vue
│   └── main.js
├── public/
├── index.html
├── vite.config.js
├── package.json
└── README.md
```

## 🎸 Sezioni del Sito

- **Home** - Pagina principale con hero section
- **Musica** - Elenco brani e album
- **Tour** - Prossime date dei concerti
- **Contatti** - Modulo per contattare la band

## 📝 Licenza

© 2026 Saints & Bastards - Tutti i diritti riservati.
