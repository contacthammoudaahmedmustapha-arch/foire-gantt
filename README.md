# 🚀 METTEC Gantt — Guide de déploiement complet

## Stack technique
- **Frontend** : HTML / CSS / JS pur (1 seul fichier)
- **Base de données** : Supabase (PostgreSQL, gratuit)
- **Hébergement** : Vercel (gratuit)

---

## Étape 1 — Créer votre base de données Supabase

1. Allez sur **https://supabase.com** → "Start for free"
2. Créez un nouveau projet (choisissez une région proche, ex: Frankfurt)
3. Une fois le projet créé, allez dans **SQL Editor** (menu gauche)
4. Copiez-collez le contenu de **supabase_setup.sql** et cliquez **Run**
5. Allez dans **Project Settings → API** et copiez :
   - **Project URL** (ex: `https://abcdefgh.supabase.co`)
   - **anon public key** (longue chaîne JWT)

---

## Étape 2 — Configurer index.html

Ouvrez `index.html` et remplacez les deux lignes en haut du `<script>` :

```js
// AVANT
const SUPABASE_URL  = 'VOTRE_SUPABASE_URL';
const SUPABASE_KEY  = 'VOTRE_SUPABASE_ANON_KEY';

// APRÈS (exemple)
const SUPABASE_URL  = 'https://abcdefgh.supabase.co';
const SUPABASE_KEY  = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...';
```

---

## Étape 3 — Déployer sur Vercel

### Option A — Via GitHub (recommandé)
1. Créez un dépôt GitHub et poussez `index.html`
2. Sur **https://vercel.com** → "Add New Project"
3. Importez votre dépôt GitHub
4. Vercel détecte automatiquement un site statique
5. Cliquez **Deploy** → votre URL est prête en 30 secondes !

### Option B — Drag & Drop
1. Sur https://vercel.com → "Add New Project"
2. Faites glisser le dossier contenant `index.html`
3. Cliquez **Deploy**

---

## Identifiants de connexion

| Champ            | Valeur       |
|-----------------|--------------|
| Nom d'utilisateur | `mettec2026` |
| Mot de passe     | `mettec2026` |

---

## Structure de la table Supabase

| Colonne      | Type      | Description                        |
|-------------|-----------|-------------------------------------|
| `id`        | UUID      | Identifiant unique (auto-généré)    |
| `name`      | TEXT      | Nom de la tâche                     |
| `start_date`| TEXT      | Date de début (YYYY-MM-DD)          |
| `start_time`| TEXT      | Heure de début (HH:MM)              |
| `end_date`  | TEXT      | Date de fin (YYYY-MM-DD)            |
| `end_time`  | TEXT      | Heure de fin (HH:MM)                |
| `people`    | TEXT[]    | Tableau de noms (array PostgreSQL)  |
| `color`     | TEXT      | Couleur hex de la barre             |
| `created_at`| TIMESTAMPTZ| Horodatage de création             |

---

## Limites du plan gratuit Supabase

- ✅ 500 MB de base de données
- ✅ 50 000 requêtes/mois
- ✅ Illimité en tâches pour cet usage
- ✅ Pas de carte de crédit requise

Largement suffisant pour la gestion d'une foire !
