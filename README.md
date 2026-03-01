# Fleet Maintenance Pro — Guide de Déploiement
**HABATECH** · Conakry, Guinée

---

## 📁 Structure des fichiers

```
/
├── index.html              ← Application principale (Fleet Maintenance Pro)
├── manifest.json           ← PWA manifest (icônes, nom app)
├── robots.txt              ← Directives robots Google
├── sitemap.xml             ← Plan du site pour Google Search
├── netlify.toml            ← Config Netlify (headers, redirections, cache)
├── _redirects              ← Redirections Netlify (SPA fallback)
├── firebase.json           ← Config Firebase Hosting
├── .firebaserc             ← Projet Firebase "fleet-habatech"
├── firestore.rules         ← Règles de sécurité Firestore
└── icons/                  ← Icônes PWA (72, 96, 128, 144, 152, 192, 384, 512px)
```

---

## 🚀 Déploiement sur Netlify

### Option A — Interface Web (recommandé)
1. Aller sur [app.netlify.com](https://app.netlify.com)
2. "Add new site" → "Deploy manually"
3. Glisser-déposer ce dossier
4. Le site sera disponible sur `https://xxx.netlify.app`
5. Configurer le domaine personnalisé : `fleet.habatech.gn`

### Option B — CLI Netlify
```bash
npm install -g netlify-cli
netlify login
netlify deploy --prod --dir .
```

### Variables d'environnement Netlify
Aucune variable requise (Firebase SDK configuré dans index.html).

---

## 🔥 Configuration Firebase

### 1. Créer le projet
```bash
npm install -g firebase-tools
firebase login
firebase init hosting firestore
```

### 2. Remplacer les clés dans `index.html`
Chercher `VOTRE_API_KEY` et remplacer par vos vraies clés Firebase :
```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "fleet-habatech.firebaseapp.com",
  projectId: "fleet-habatech",
  storageBucket: "fleet-habatech.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123",
  measurementId: "G-XXXXXXXXXX"
};
```

### 3. Déployer Firebase
```bash
firebase deploy --only hosting,firestore:rules
```

---

## 🔍 SEO Google Search

### Métadonnées incluses
- ✅ `<title>` et `<meta description>` optimisés
- ✅ Open Graph (Facebook, LinkedIn)
- ✅ Twitter Card
- ✅ Schema.org JSON-LD (SoftwareApplication)
- ✅ `robots.txt` et `sitemap.xml`
- ✅ `rel="canonical"`

### Soumettre le sitemap à Google
1. Aller sur [Google Search Console](https://search.google.com/search-console)
2. Ajouter la propriété `fleet.habatech.gn`
3. Sitemaps → Soumettre `https://fleet.habatech.gn/sitemap.xml`

---

## 💰 Devise
L'application utilise le **Franc Guinéen (GNF)** comme devise principale.

---

© 2024 **HABATECH** · contact@habatech.gn · [habatech.gn](https://habatech.gn)
