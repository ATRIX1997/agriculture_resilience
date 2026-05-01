# Agriculture et résilience — Burkina Faso

Projet d’analyse exploratoire des données (EDA) sur les **indicateurs agricoles et le développement rural** au Burkina Faso. L’objectif est de mettre en évidence les tendances temporelles, les liens entre variables et les enjeux de **productivité**, **usage des terres** et **conditions de vie en milieu rural**, dans une perspective de **résilience** du secteur agricole et de la sécurité alimentaire.

## Contexte

Le Burkina Faso est un pays à forte composante rurale et agricole. Les séries de la Banque mondiale (diffusées sur HDX) permettent de suivre sur plusieurs décennies des indicateurs liés aux terres, aux rendements, aux intrants et à l’accès aux services de base. Ce dépôt regroupe le jeu de données utilisé, le notebook d’analyse, les figures exportées et un mémo PDF associé au travail académique ou professionnel.

## Données

- **Fichier :** `agriculture_burkina.csv` (format long : une ligne par combinaison année / indicateur).
- **Colonnes :** pays (`Burkina Faso`), code ISO3 (`BFA`), **année**, libellé d’**indicateur**, **code** indicateur (ex. codes Banque mondiale type `AG.*`), **valeur** numérique.
- **Volume :** environ **1 724 lignes** brutes ; après nettoyage (conversion numérique de l’année et de la valeur, suppression des lignes incomplètes), environ **1 723 observations** exploitables pour l’EDA.
- **Période :** les années couvertes varient selon l’indicateur (souvent des décennies de données par série).

**Source officielle :** Banque mondiale, jeu « agriculture and rural development » pour le Burkina Faso, via le **Humanitarian Data Exchange (HDX)** :

[Dataset HDX — World Bank Indicators for Burkina Faso](https://data.humdata.org/dataset/cd97d950-0124-468b-9bf0-71d232e47668/resource/81856343-2ffc-4336-8eb6-c1bd90ec9759/download/agriculture-and-rural-development_bfa.csv)

## Méthodologie (notebook)

Le notebook `EDA_Agriculture_Burkina_Faso.ipynb` enchaîne les étapes suivantes :

1. **Environnement** — Installation des bibliothèques (`pandas`, `matplotlib`, `seaborn`, `tabulate`), création du dossier `plots/` pour les exports graphiques.
2. **Chargement** — Lecture du CSV avec colonnes nommées : `Country`, `ISO3`, `Year`, `Indicator`, `Code`, `Value`.
3. **Nettoyage** — Conversion de `Year` et `Value` en numérique (`errors='coerce'`), suppression des lignes sans année ou sans valeur.
4. **Statistiques descriptives** — Tableaux récapitulatifs (`describe`) par indicateur pour un sous-ensemble d’indicateurs clés (voir ci-dessous).
5. **Visualisations** — Séries temporelles et matrice de corrélation entre indicateurs ; enregistrement des figures en PNG dans `plots/`.

**Indicateurs centraux de l’analyse** (libellés exacts dans les données) :

| Thème | Indicateur |
|--------|------------|
| Production | Rendement céréalier (kg par hectare) |
| Terres | Terres agricoles (% de la superficie) |
| Terres | Terres arables (% de la superficie) |
| Démographie rurale | Population rurale (% de la population totale) |
| Infrastructure | Accès à l’électricité en milieu rural (% de la population rurale) |
| Intrants | Consommation d’engrais (% de la production d’engrais) |

## Résultats livrés (`plots/`)

| Fichier | Contenu |
|---------|---------|
| `rendement_cerealier.png` | Évolution du rendement céréalier (kg/ha) dans le temps |
| `terres_agricoles.png` | Évolution de la part des terres agricoles |
| `demographie_infrastructure_rurale.png` | Séries liées à la population rurale et à l’électrification rurale |
| `correlation_indicateurs.png` | Matrice de corrélation entre les indicateurs retenus (après pivot par année) |

Ces graphiques sont générés dans le notebook avec `seaborn` / `matplotlib` (style `whitegrid`), en **150 dpi** pour une réutilisation dans des rapports.

## Synthèse des conclusions (EDA)

Les analyses du notebook soulignent des **défis importants** en matière de **productivité agricole** et d’**accès aux infrastructures de base** en milieu rural. Elles mettent en avant l’intérêt d’**investissements** dans l’**électrification rurale** et l’**adoption de pratiques agricoles durables** pour renforcer la **résilience** et la **sécurité alimentaire**.


## Contenu du dépôt

| Élément | Rôle |
|---------|------|
| `EDA_Agriculture_Burkina_Faso.ipynb` | Analyse complète (code + interprétation) |
| `agriculture_burkina.csv` | Données sources utilisées dans le notebook |
| `plots/` | Figures exportées |
| `sain_defis_1_by_abdel_kader_razack.pdf` | Document associé au projet |
| `.gitignore` | Exclusion des checkpoints Jupyter et environnements virtuels |

## Prérequis et exécution

- **Python** 3.10+ recommandé  
- **Dépendances :** `pandas`, `matplotlib`, `seaborn`, `numpy`, `tabulate`

```bash
pip install pandas matplotlib seaborn numpy tabulate
```

```bash
jupyter notebook EDA_Agriculture_Burkina_Faso.ipynb
```

Le notebook suppose que `agriculture_burkina.csv` est **à la racine du même dossier** que le fichier `.ipynb`. Un bloc commenté permet, si besoin, de retélécharger le fichier depuis HDX avec `requests`.

## Auteur et dépôt

Travail associé au compte GitHub [@ATRIX1997](https://github.com/ATRIX1997) — dépôt **agriculture_resilience**.
