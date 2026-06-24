# OpenRBE - Registre des Bénéficiaires Effectifs

**Plateforme nationale de consultation du secteur extractif sénégalais**  
Initiative portée par la **CN-ITIE Sénégal** dans le cadre de la Norme ITIE 2023 (Exigence 2.5).

---

## Présentation

OpenRBE rend public et lisible le registre national des bénéficiaires effectifs des entreprises pétrolières, gazières et minières opérant au Sénégal.

La plateforme est accessible à tous - citoyens, journalistes, agents publics, partenaires - sans compte ni installation.

---

## Fonctionnalités

| Module | Description |
|--------|-------------|
| **Tableau de bord** | KPIs, graphiques de répartition par région, nationalité, secteur |
| **Base complète** | Tableau paginé, filtrable et exportable (Excel, CSV, PDF) |
| **Analyse PPE** | Identification des Personnes Politiquement Exposées |
| **Réseaux** | Visualisation des liens entre entreprises et bénéficiaires (D3.js) |
| **Cartographie** | Carte interactive des entreprises par région (Leaflet) |
| **Recherche** | Recherche par entreprise ou bénéficiaire avec autocomplétion |
| **Filtres globaux** | Panneau de filtres déplaçable (région, nationalité, pays, PPE, période) |

---

## Architecture

Application **mono-fichier** (`index.html`) - aucun serveur, aucun build requis.

```
index.html
├── CSS inline        - design system, responsive, composants
├── HTML              - structure des pages (SPA)
└── JavaScript inline - logique, chargement des données, graphiques
```

### Bibliothèques externes (CDN)

| Bibliothèque | Usage |
|-------------|-------|
| [Leaflet.js](https://leafletjs.com/) | Carte interactive |
| [Chart.js](https://www.chartjs.org/) | Graphiques |
| [D3.js](https://d3js.org/) | Visualisation réseau |
| [SheetJS (XLSX)](https://sheetjs.com/) | Lecture fichiers Excel |
| [jsPDF](https://github.com/parallax/jsPDF) | Export PDF |
| [Font Awesome](https://fontawesome.com/) | Icônes |

---

## Source des données

Les données sont chargées en direct depuis un **Google Sheet public** (format CSV ou XLSX).  
Un instantané intégré (`SNAPSHOT`) assure le fonctionnement hors-ligne.

### Format du fichier Excel attendu

Le parser est **robuste et non sensible à l'ordre des colonnes**.  
Il détecte automatiquement l'en-tête dans les 12 premières lignes et mappe les colonnes par leur nom.

Colonnes reconnues (synonymes acceptés) :

| Champ | Noms acceptés |
|-------|---------------|
| Région | Région, Localité, Département, District… |
| Dénomination sociale | Dénomination, Raison sociale, Société, Entreprise… |
| Bénéficiaire | Bénéficiaire effectif, Nom prénom, Identité… |
| Date acquisition | Date acquisition, Date déclaration, Date dépôt… |
| % Actions | % Action, Part capital, Participation… |
| % Voix | % Voix, Droit de vote… |
| Nationalité | Nationalité, Citoyenneté… |
| Pays résidence | Pays de résidence, Pays… |
| PPE | PPE, Personne politiquement exposée… |
| Fonction PPE | Fonction, Poste, Qualité… |
| Greffe | Greffe, Tribunal de commerce… |

---

## Déploiement

Le site est déployé automatiquement via **GitHub Actions** à chaque push sur `main`.

```bash
# Lancer localement
open index.html   # ou double-clic sur le fichier
```

Aucune dépendance à installer - tout est chargé via CDN.

---

## Cadre légal

- **Décret n° 2021-1443** - Création et organisation du RBE au Sénégal
- **Décret n° 2021-1803** - Modalités de tenue du registre
- **Arrêté n° 24577 du 2 septembre 2022** - Volet fiscal (DGID)
- **Loi n° 2021-29 du 5 juillet 2021** - Renforcement CGI articles 633 et 667
- **Norme ITIE 2023** - Exigence 2.5 : divulgation des bénéficiaires effectifs

---

## Liens

- [CN-ITIE Sénégal](https://www.itie.sn/)
- [DGID Sénégal](https://www.dgid.sn/)
- [EITI Standard 2023](https://eiti.org/sites/default/files/2023-06/EITI%20Standard%202023_FR.pdf)
