# Obsidian Canvas Exporter

Obsidian Canvas Exporter est un plugin premium pour Obsidian qui vous permet d'exporter instantanément vos tableaux blancs Canvas (`.canvas`) sous forme de documents PDF vectoriels propres et fidèles, tout en les copiant directement dans le presse-papiers de votre système. Conçu pour simplifier le partage de vos schémas et de vos idées graphiques en un seul clic.

## # Installation

Pour installer le plugin manuellement :

1. Téléchargez la dernière version disponible dans les [Releases GitHub](https://github.com/hjamet/obsidian-canvas-exporter/releases).
2. Créez un dossier nommé `obsidian-canvas-exporter` dans le répertoire des plugins de votre coffre Obsidian (chemin : `.obsidian/plugins/`).
3. Copiez-y les trois fichiers de la release : `main.js`, `manifest.json` et `styles.css`.
4. Activez le plugin dans les options d'Obsidian (*Réglages -> Plugins communautaires*).

## # Description détaillée

Le plugin intercepte et analyse la structure de données JSON des fichiers Obsidian Canvas pour en extraire l'ensemble des nœuds (textes, notes, images, cartes) et de leurs relations (flèches de connexion). 

### Le Cœur & Flux d'Exécution :
1. **Extraction** : Lecture du fichier Canvas actif et parsing du layout d'origine.
2. **Génération Vectorielle** : Reconstruction séquentielle du tableau dans un document PDF multi-pages à l'aide de bibliothèques vectorielles performantes.
3. **Copie Clipboard** : Encodage et injection automatique du fichier binaire résultant directement dans le presse-papiers système sous format natif de fichier/image pour collage immédiat dans n'importe quel logiciel tiers (Slack, Teams, Word, etc.).

---

## # Principaux résultats

Voici un aperçu comparatif des performances et de la fidélité d'exportation :

| Format Source | Qualité Visuelle | Vitesse d'Export | Poids Moyen du PDF | Copie Clipboard |
|---------------|------------------|------------------|--------------------|-----------------|
| Obsidian Canvas standard | Vectoriel natif (HD) | < 0.5 secondes | ~120 Ko | Immédiate (Automatique) |
| Capture d'écran classique | Rasterisé / Flou | Manuelle (>5s) | ~1.5 Mo | Manuelle |

---

## # Documentation Index

Retrouvez ci-dessous les fichiers d'indexation de la documentation technique :

| Titre (Lien) | Description |
|--------------|-------------|
| [Index Documentation CI](docs/index_ci.md) | Liste des documentations concernant l'intégration continue et la publication automatique |

---

## # Plan du repo

Voici l'organisation structurelle de notre projet :

```
obsidian-canvas-exporter/
├── .github/
│   └── workflows/
│       └── release.yml     # Workflow de Release Automatique (CI)
├── docs/
│   ├── ci/
│   │   └── release_flow.md # Fonctionnement détaillé de la CI
│   └── index_ci.md         # Index des docs d'intégration continue
├── esbuild.config.mjs      # Configuration de compilation du plugin
├── main.ts                 # Code source TypeScript du plugin
├── manifest.json           # Manifeste Obsidian (Id, Version, Auteur)
├── package.json            # Dépendances et scripts de développement
├── styles.css              # Feuille de styles du plugin
└── tsconfig.json           # Configuration TypeScript
```

---

## # Scripts d'entrée principaux

Les scripts suivants permettent de builder et de développer le plugin localement :

| Commande | Usage | Description |
|----------|-------|-------------|
| `npm run dev` | `dev` | Lance la compilation à la volée (`watch mode`) avec esbuild pour le développement actif |
| `npm run build` | `build` | Compile une version optimisée et packagée de production dans `main.js` |

---

## # Scripts exécutables secondaires & Utilitaires

* Aucun script exécutable secondaire n'est requis pour le moment.

---

## # Roadmap

Toutes les tâches futures sont rigoureusement liées à des issues GitHub pour en assurer le suivi :

| Nom de la Tâche | Objectif | État | Dépendances |
|-----------------|----------|------|-------------|
| [Personnalisation des options d'export](https://github.com/hjamet/obsidian-canvas-exporter/issues/1) | Ajouter un onglet de réglages pour personnaliser le format PDF, les marges et l'orientation | `En attente` | Aucune |
