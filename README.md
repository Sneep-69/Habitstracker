# Habitudes

Suivi d'habitudes en PWA (HTML/CSS/JS sans dépendance), installable sur l'écran d'accueil iOS/iPadOS.
Données stockées en local (`localStorage`), export/import JSON.

## Mise en ligne sur GitHub Pages

1. Créer un dépôt public, par ex. `habitudes`.
2. Pousser les fichiers :
   ```bash
   cd habitudes
   git init
   git add .
   git commit -m "Habitudes v1"
   git branch -M main
   git remote add origin https://github.com/<ton-user>/habitudes.git
   git push -u origin main
   ```
3. Sur GitHub : **Settings → Pages → Source : Deploy from a branch → Branch : `main` / `/ (root)` → Save**.
4. URL : `https://<ton-user>.github.io/habitudes/` (1 à 2 min après le push).

## Installation sur iPhone / iPad

1. Ouvrir l'URL dans **Safari**.
2. Bouton Partager → **Sur l'écran d'accueil** → Ajouter.

## Mise à jour

Après une modification, incrémenter `CACHE` dans `sw.js` (`habitudes-v1` → `habitudes-v2`), puis push.
Rouvrir l'app deux fois pour que la nouvelle version s'affiche.

## Données

- Chaque appareil a son propre stockage : pas de synchro iPhone ↔ iPad.
- Transfert : Profil → **Exporter en JSON** (Enregistrer dans Fichiers / iCloud Drive), puis **Importer un JSON** sur l'autre appareil (Fusionner ou Remplacer).
- Supprimer l'icône de l'écran d'accueil efface les données de l'app : exporter avant.

### Format JSON

```json
{
  "app": "habitudes",
  "version": 1,
  "habits": [
    { "id": "abc123", "name": "Eau", "emoji": "💧", "color": "bleu",
      "type": "count", "target": 8, "step": 1, "unit": "verres",
      "days": [0,1,2,3,4,5,6], "created": "2026-09-19" }
  ],
  "logs": { "2026-09-19": { "abc123": 6 } },
  "settings": { "focus": "abc123" }
}
```

`days` : 0 = lundi … 6 = dimanche. `type` : `check` (oui/non) ou `count` (quantité avec objectif).
