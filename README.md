# MabyaPilot

> Cockpit HTML autonome de pilotage du portefeuille de projets de développement Groupe Mabya selon la méthode **Goose** / Ten Steps.
>
> *« Comprendre pour mieux conseiller » — Mabya × L4A Agency*

## Contenu du repo

| Fichier | Description |
|---|---|
| `mabya_pilot.html` | **Application complète** — un seul fichier HTML autonome (HTML + CSS + JS embarqués). Pas de serveur, pas de build. |
| `Cadrage projets Mabya avec equipes nominatives.pptx` | Source officielle des équipes nominatives (10 slides — 3 projets) |
| `.claude/launch.json` | Config preview locale (port 8094) |

## Architecture

- **HTML autonome** : pattern `qualipex-app` / `calcul-import` — un seul fichier sans dépendance build
- **Stockage** : `localStorage` (clé `mabya-pilot-v1`) + export/import JSON
- **CDN** : SheetJS (XLSX), jsPDF, PptxGenJS
- **Charte** : palette verte Budget McD (`#1B5E3B` / `#4CAF78` / `#E8F5EE`) + accent orange chevron Mabya (`#E2502F`)
- **Migrations versionnées** : flag `STATE.migrations.<id>` pour ne jamais réécraser les modifications utilisateur

## 7 Modules

1. **Dashboard portefeuille** — vue consolidée des 4 projets Mabya
2. **Fiche Projet** — 11 sections du Brief Projet méthode Goose
3. **Simulateur P&L 3 ans** — multi-scénarios (Base + Agressif), calcul cascade MCV → MB → EBITDA → REX
4. **Rétroplanning Gantt** — 6 phases Goose, jalons Go/No-Go, chemin critique, today line
5. **Matrice Risques** — calcul criticité auto (matrice Goose 4×4 → 1/2/3), plans préventifs/correctifs
6. **COC Room** — préparation, prise de notes live, génération CR
7. **Paramétrage centralisé** — règle d'or : aucune valeur chiffrée hardcodée ailleurs

## Bannière permanente Note de cadrage

- **Section 1** — Équipe projet (Sponsor / Leader / Co-leader + Core team + Extended team)
- **Section 6** — Contrat QCD/DQC/CDQ/CQD/DCQ/QDC (3 cartes auto-réordonnées par priorité)

## Système structuré markdown-light

Toutes les sections du Brief utilisent un parser markdown light :
```
## Sous-section niveau 1 (collapsible <details>)
### Sous-titre niveau 2 (h4)
_Note italique_ (callout vert)
• Bullet niveau 1
  ◦ Bullet niveau 2
    ▪ Bullet niveau 3
| Col1 | Col2 |
|---|---|
| Cellule | Cellule |
```

**Édition inline (contenteditable)** sur tous les éléments :
- Bullets (`<li>`) avec bouton `×` au hover pour suppression
- Cellules de tableau (`<td>`, `<th>`)
- Sous-titres et titres de sous-sections
- Boutons `+ Sous-section` / `+ Point` pour enrichir

## Exports disponibles

| Format | Contenu |
|---|---|
| 📦 JSON complet | Backup / réimport (préserve les migrations) |
| 📕 **PDF projet complet** | Cover + 11 sections + P&L + Rétro + Risques (≈17 pages, charte verte) |
| 🎭 **PPTX projet complet** | Cover + sections + P&L + Rétro + Risques (≈48 slides) |
| 📄 PDF Note de cadrage seule | Synthèse 1-2 pages (équipe + contrat) |
| 📊 Excel multi-onglets | Cadrage / P&L / Rétro / Risques / Équipe |

## Lancer l'application

### Option 1 — Double-clic
Ouvrir `mabya_pilot.html` directement dans le navigateur. Sauvegarde en `localStorage`.

### Option 2 — Serveur local (recommandé)
```bash
cd MabyaPilot/
python -m http.server 8094
# → http://localhost:8094/mabya_pilot.html
```

## Stratégie de développement en 2 phases

- **Phase 1 (livré)** : mono-utilisateur local, autonomie offline, `localStorage`
- **Phase 2 (à venir)** : multi-utilisateur centralisé (backend, auth, audit trail)

L'abstraction `Storage` est déjà en place pour faciliter la migration phase 2.

## État du projet (29/04/2026)

✅ MVP Phase 1 livré — 4 phases de développement complétées
✅ Charte graphique verte Budget McD appliquée
✅ Logo Mabya SVG inline (chevrons orange superposés)
✅ Sections rétractables avec persistance localStorage
✅ Édition inline contenteditable + reconstruction markdown
✅ Cartes contrat C/D/Q agrandissables + modal plein écran
✅ **Brief Distribution 100 % alimenté** : Sections 1-11 + Module Risques + Simulateur P&L (Base + Agressif) + Rétroplanning (31 tâches, 6 jalons)
✅ Exports PDF complet + PPTX complet

⏳ À alimenter : autres projets (Pain, Viennoiserie, Coffee Shop Tiroir)

## Skills associés

10 skills `mabya-*` dans `~/.claude/skills/` :
- Méthodologiques : `cadrage-projet`, `goose-methodology`, `analyse-risques`, `retroplanning`, `coc-reporting`
- Projets : `projet-pain`, `projet-viennoiserie`, `projet-distribution`, `coffee-shop-tiroir`
- Stratégique : `strategy-dashboard`
- App : `mabya-pilot-app`

## License

Privé — Groupe Mabya × L4A Agency.
