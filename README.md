# 📦 Bloc 3 - Implémentation et Optimisation de Solutions de Stockage et de Traitement de Données sur le Cloud

## 🎯 Objectif du projet

Ce projet a pour but de concevoir, implémenter et optimiser une solution cloud de traitement et de visualisation de données pour une **école de danse**. L'ensemble de l'architecture repose sur **Microsoft Fabric**, combinant un **Data Lake moderne** au format **Delta Lake**, une approche **ETL robuste**, et des tableaux de bord interactifs via **Power BI**.

---

## 🏗️ Architecture Technique

### 🔧 Choix technologiques
- **Microsoft Fabric** : unification du stockage, traitement et visualisation
- **PySpark** : traitement distribué des données
- **Delta Lake** : stockage versionné et performant
- **Power BI** : visualisation des KPI métiers
- **Lakehouse Architecture** : flexibilité du data lake et structure du data warehouse

---

## 📁 Données Sources

| Fichier | Description |
|--------|-------------|
| `danseurs.csv` | Informations clients (personnelles et marketing) |
| `inscriptions.csv` | Historique des inscriptions |
| `tarifs.csv` | Grille tarifaire |
| `formule.csv` | Types de formules proposées |
| `duree.csv` | Durée des cours |
| `danse.csv` | Catalogue des danses enseignées |

---

## 🧠 Modélisation des Données

### 🧩 Modèle en Étoile
- **Table de faits** : `FAIT_INSCRIPTIONS`
- **Dimensions** : clients, danses, formules, durées, tarifs, temps

### 🕓 Gestion de l’historique
- `SCD Type 2` : pour `DIM_DANSEUR` (versioning)
- `SCD Type 1` : pour `DIM_FORMULE` (mise à jour simple)

### 🏷️ Enrichissement
- `DIM_TARIF` enrichie avec formules, durées et types de danse

---

## 🔄 Pipeline ETL

- **Zone Staging** : ingestion et nettoyage des CSV
- **Transformation métier** :
  - Calcul du nombre de séances
  - Calcul de rentabilité, coût unitaire, CA
- **Dimension temporelle dynamique** : août 2024 à juillet 2025

---

## 💾 Stockage & Sécurité

- **Organisation Data Lake** : Raw → Staging → Gold
- **Formats supportés** : CSV, Delta, JSON
- **Change Data Feed** + sauvegarde incrémentale
- **Sécurité** :
  - Chiffrement au repos et en transit
  - Hachage des données sensibles
  - Conformité RGPD (anonymisation, suppression logs, rétention différenciée)

---

## 📊 Visualisation avec Power BI

Des dashboards dynamiques ont été construits :
- CA par type de danse
- Répartition des inscriptions par formule
- Suivi de la fidélité client
- Périodes de pic d’activité

### 📈 KPI suivis :
- Évolution mensuelle du chiffre d'affaires
- Taux de rétention client
- Rentabilité par formule
- Prévision des inscriptions

---

## 🔍 Monitoring & Optimisation

- **Observabilité** :
  - Logs centralisés
  - Alertes en cas d’anomalie
  - Suivi des performances
- **Optimisations** :
  - Auto-compaction
  - Z-ordering
  - Vacuum automatique
  - Ajustement des ressources Spark

---

## 🛠️ Défis rencontrés

| Défi | Solution |
|------|----------|
| Problèmes d'encodage | Fonction de nettoyage personnalisée |
| Logique métier complexe | Expressions régulières & conditions personnalisées |
| Historisation SCD | Algorithme de détection des changements via jointure intelligente |

---

## ✅ Critères Bloc 3 Validés

- ✔️ Architecture Data Lake multi-format
- ✔️ Pipelines ETL cloud robustes
- ✔️ Sécurité et RGPD respectés
- ✔️ Monitoring & optimisation des coûts
- ✔️ Visualisations dynamiques pour les métiers

---

## 📌 Conclusion

Ce projet démontre une **maîtrise complète** de la chaîne de traitement de données sur le cloud :

- Architecture scalable & moderne
- Pipelines métiers solides
- Gouvernance et conformité intégrées
- Visualisations percutantes pour les utilisateurs métiers

---

## 📂 Contenu du dépôt

- `Stagingsdcdatawarehouse.ipynb` : pipeline PySpark
- `rapportanalysedance.pbix` : rapport Power BI
- `Modele semantique.png` : diagramme du modèle en étoile

---

## 👤 Auteur

> [@ada-wq](https://github.com/ada-wq) – Projet réalisé dans le cadre du Bloc 3 Data Engineering à l’EFREI
