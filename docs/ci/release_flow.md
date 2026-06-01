# Processus de Release Automatique (CI)

Ce document décrit en détail le fonctionnement de l'intégration continue (CI) configurée pour générer les releases du plugin.

## Fonctionnement Global

Le workflow GitHub Actions s'exécute de manière entièrement transparente et automatisée :

1. **Détection** : Dès qu'un push est effectué sur la branche `main` et que le fichier `manifest.json` a été modifié, le workflow se déclenche.
2. **Extraction de version** : La CI lit la propriété `"version"` du fichier `manifest.json` à l'aide de Node.js.
3. **Vérification d'existence** :
   - Elle vérifie si un tag Git du même nom existe déjà sur le dépôt.
   - Si le tag **existe déjà**, le workflow s'arrête en toute sécurité sans recréer de doublon.
   - Si le tag **n'existe pas**, la CI continue vers le build et la release.
4. **Compilation** : Les packages npm sont restaurés proprement via `npm ci` et le build est lancé via `npm run build`. Cela génère le fichier compilé `main.js`.
5. **Vérification des Assets** : Elle s'assure que les trois fichiers indispensables au plugin Obsidian sont présents :
   - `main.js` (le code JavaScript compilé)
   - `manifest.json` (les métadonnées et version)
   - `styles.css` (les styles CSS de mise en forme)
6. **Tagging Git** : Un tag Git avec le numéro exact de version est créé localement par le bot GitHub Actions puis poussé sur le dépôt distant.
7. **Publication de la Release** : Une release GitHub publique est publiée avec ce tag, contenant le code source compressé ainsi que les trois fichiers assets associés.

## Déclenchement Manuel

Il est également possible de lancer le workflow manuellement depuis l'onglet **Actions** de l'interface GitHub grâce à l'option `workflow_dispatch` incluse.
