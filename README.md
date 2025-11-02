# 1 - Identifier les axes d’analyse pertinents et les tables de dimensions
Axes d’analyse → tables de dimensions

- Étudiant → Dim_Étudiant (id, nom, prénom, sexe, date_naissance, ville, région, statut)

- Filière → Dim_Filiere (id, nom_filiere, niveau, id_departement)

- Département → Dim_Departement (id, nom_departement)

- Temps → Dim_Temps (id, date, mois, semestre, année_académique)

- Table de faits : Fait_Inscriptions (fk_etudiant, fk_filiere, fk_departement, fk_temps, statut_inscription, montant_paye)

# 2 - Schéma de flux d’intégration

<img width="2428" height="306" alt="image" src="https://github.com/user-attachments/assets/1816872a-e77e-44c6-b6c7-957b0ce9243f" />


# 3 -  Extraction avec un outil ETL

- Connecter l’ETL aux bases (JDBC) et aux fichiers Excel.

- Lire et copier les tables/feuilles dans des staging tables.

- Vérifier le nombre de lignes et les erreurs (log simple).

# 4 - Principales transformations

- Nettoyage : supprimer doublons, lignes évidentes invalides.

- Normalisation dates : tout en YYYY-MM-DD.

- Conversion types : montant → décimal, date → date, téléphone → chiffres.

- Standardisation : uniformiser libellés.

- Calculs : age, taux_redoublement.

- Déduplication : par num_etudiant ou (nom+prenom+date_naissance).
