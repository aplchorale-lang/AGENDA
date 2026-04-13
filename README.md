# 🎵 APL — Antsam-Pideran'ny Lanitra
### Application de gestion des événements de la chorale

---

## Présentation

Application web monopage (SPA) pour la gestion des événements de la chorale **APL — Antsam-Pideran'ny Lanitra**. Conçue pour ~50 membres non-techniciens, sans base de données externe, entièrement fonctionnelle via `localStorage`.

**Référence biblique :** Kol. 3,16

---

## Fonctionnalités

### Accès & sécurité
- Page de connexion avec mot de passe unique (`Apl26`)
- Mode administrateur protégé (même mot de passe)
- Aucun compte utilisateur, aucune inscription

### Membres
- **Accueil** : statistiques rapides + prochains événements
- **Calendrier** : vue mensuelle colorée par type d'événement
- **Événements** : liste filtrée par type, période, recherche
- **Statistiques** : graphiques par type, activité mensuelle, suivi chansons

### Administrateurs
- Création / modification / suppression d'événements
- Formulaire complet avec toutes les sections
- Export texte de chaque événement

### Structure d'un événement
- Informations générales (type, date, lieu, horaires, initiateur)
- Description, programme, programme liturgique
- **Chansons** : titre, auteur, durée, lien YouTube/Spotify, statut d'apprentissage
- **Transport** : responsable, contact, places, frais, liste des inscrits
- **Logistique** : éléments modulables avec statut (préparé / en cours / terminé)
- **Checklist** des préparatifs (cochable par les membres)
- Notes importantes
- Contacts d'urgence

---

## Installation locale

```bash
# Cloner le dépôt
git clone https://github.com/votre-utilisateur/apl-evenements.git
cd apl-evenements

# Aucune dépendance ! Ouvrir directement dans le navigateur
open index.html
# Ou via un serveur local simple :
npx serve .
# Ou avec Python :
python3 -m http.server 8080
```

---

## Déploiement sur Netlify

### Méthode 1 — Interface Netlify (recommandée)

1. Créer un compte sur [netlify.com](https://netlify.com)
2. Cliquer sur **"Add new site"** → **"Import an existing project"**
3. Connecter votre dépôt GitHub
4. Paramètres de build :
   - **Build command** : *(laisser vide)*
   - **Publish directory** : `.`
5. Cliquer **"Deploy site"**

### Méthode 2 — Glisser-déposer

1. Aller sur [app.netlify.com/drop](https://app.netlify.com/drop)
2. Glisser le dossier du projet dans la zone de dépôt
3. L'application est immédiatement en ligne !

### Méthode 3 — CLI Netlify

```bash
npm install -g netlify-cli
netlify login
netlify deploy --prod --dir=.
```

### Nom de domaine personnalisé

Dans l'interface Netlify : **Domain settings** → **Add custom domain**

---

## Structure des fichiers

```
apl-evenements/
├── index.html          # Application complète (HTML + CSS + JS)
├── LOGO_APL.jpg        # Logo de la chorale
├── netlify.toml        # Configuration de déploiement
└── README.md           # Cette documentation
```

---

## Données

Les données sont stockées dans le **localStorage** du navigateur :
- Clé principale : `apl_evenements_v1`
- Checklist par événement : `apl_checks_v1_<id>`

> ⚠️ Les données sont locales au navigateur. Pour partager entre membres, exportez et réimportez manuellement, ou envisagez un service de synchronisation (GitHub Pages avec JSON, Firebase, etc.)

### Sauvegarde manuelle

Depuis la console du navigateur :
```javascript
// Exporter
const data = localStorage.getItem('apl_evenements_v1');
console.log(data); // Copier et sauvegarder

// Importer
localStorage.setItem('apl_evenements_v1', '<data_copiée>');
location.reload();
```

---

## Personnalisation

### Changer le mot de passe

Dans `index.html`, ligne avec `const MDP = 'Apl26';` :
```javascript
const MDP = 'VotreNouveauMotDePasse';
```

### Changer le logo

Remplacer le fichier `LOGO_APL.jpg` par votre image (même nom).

### Ajouter un type d'événement

Dans le fichier `index.html`, rechercher `COULEURS_TYPE` et ajouter :
```javascript
const COULEURS_TYPE = {
  'Messe dominicale':    'var(--messe)',
  'Votre Nouveau Type':  '#HexCouleur',
  // ...
};
```
Puis ajouter l'option dans les deux `<select>` de type d'événement.

---

## Compatibilité

| Navigateur | Support |
|-----------|---------|
| Chrome 90+ | ✅ |
| Firefox 88+ | ✅ |
| Safari 14+ | ✅ |
| Edge 90+ | ✅ |
| Mobile Chrome | ✅ |
| Mobile Safari | ✅ |

---

## Palette de couleurs

Inspirée du logo APL (argent et or) :
- **Or** `#C9A84C` — Accent principal
- **Argent** `#B0B8C1` — Éléments secondaires
- **Fond** `#F5F3EE` — Arrière-plan chaud

---

## Licence

Usage exclusif de la chorale APL — Antsam-Pideran'ny Lanitra.

---

*"Que la parole du Christ habite en vous avec toute sa richesse" — Kol. 3,16*
