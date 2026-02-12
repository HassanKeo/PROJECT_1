# Guidage pour agents IA — Projet Portfolio statique

Ce dépôt est un site statique minimal composé de pages HTML simples. Ces instructions aident un agent IA à être immédiatement productif.

Contexte global
- Projet: site portfolio statique (pas de build tool, framework ou dépendances JS). Pages principales: `index.html`, `projects.html`, `articles.html`, `contact.html`.
- Structure: chaque page contient un `header` (titre + `nav`), un `main` et un `footer`. Les pages partagent des sections similaires (copier/coller manuel attendu si on modifie l'en-tête ou le pied de page).

Principes et patterns découvertes
- Navigation: liens relatifs simples (`index.html`, `projects.html`, ...). Ne changez pas la casse des noms de fichiers (système de fichiers Linux sensible à la casse).
- Formulaire de contact: présent dans `contact.html`. Actuellement les contrôles sont groupés dans des `<section>`; préférence projet: utiliser `fieldset`/`legend` pour la sémantique et l'accessibilité.
- Pas de scripts JS fournis: les comportements interactifs (ex : mise à jour automatique de l'année dans le footer, envoi AJAX du formulaire) ne sont pas implémentés — si vous ajoutez JS, placez-le dans un fichier `assets/js/` et référencez-le depuis les pages.

Exemples concrets (modèles à suivre)
- Remplacer les `<section>` de `contact.html` par `fieldset`:

```html
<form action="/send" method="POST">
  <fieldset>
    <legend>Contact</legend>
    <label for="name">Nom</label>
    <input id="name" name="name" required>
    <!-- autres champs -->
  </fieldset>
  <button type="submit">Envoyer</button>
</form>
```

- Pour tester localement (serveur statique simple) :

```bash
# depuis le dossier du projet
python3 -m http.server 8000
# puis ouvrir http://localhost:8000/index.html
```

Points importants pour l'agent
- Ne pas supposer l'existence d'un backend: `form` sans `action` ne persiste rien. Demandez confirmation avant d'ajouter une intégration serveur.
- Respecter la structure actuelle: si vous modifiez l'en-tête ou le footer, mettez à jour toutes les pages (`index.html`, `projects.html`, `articles.html`, `contact.html`).
- Nommez les nouveaux fichiers et répertoires en minuscules et sans espaces (convention observée ici).

Tests et vérifications simples
- Ouvrir les pages dans un navigateur ou via `python3 -m http.server` pour vérifier la navigation et les formulaires.
- Vérifier l'accessibilité minimale: s'assurer que chaque `input` a un `label` associé (via `for`/`id`).

Modifications acceptables automatiquement
- Ajustements de contenu textuel (titres, descriptions meta) et remplacements sémantiques (ex: `<section>` -> `fieldset`) sans créer de serveur.

Choses à demander avant de faire
- Voulez-vous qu'on ajoute un backend pour le formulaire (ex: endpoint `/send`) ou préférez-vous une soumission via un service tiers (Formspree, Netlify Forms)?
- Voulez-vous centraliser l'en-tête/pied de page (templating) ou garder les pages statiques séparées?

Retour
- Après avoir généré des changements, proposer un diff et demander validation avant de modifier toutes les pages similaires.

Fin du fichier.
