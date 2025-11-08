# 1- Axes d’analyse et tables de dimensions

## Axes d’analyse pertinents :

- Étudiant → analyser selon le sexe, la région.

- Filière → analyser selon le nom de la filière.

- Temps → analyser par année, mois d’inscription.

- Inscriptions (fait) → mesurer le montant payé.

## Tables du modèle étoile :

- Fait_inscription : contient les mesures (montant payé).

- Dim_etudiant : informations sur les étudiants.

- Dim_filiere : informations sur les filières.

- Dim_temps : informations sur les dates (jour, mois, année).

# 2. Schéma de flux ETL (Extraction → Transformation → Chargement)

## Étapes du flux :

- Extraction :

Les données proviennent de plusieurs fichiers Excel (étudiants, filières, inscriptions). + 

Utilisation de composants tFileInputExcel dans Talend pour lire chaque fichier.

- Transformation :

Nettoyage et normalisation des données avec tMap, tFilterRow, tUniqRow.

Création de clés de substitution avec tSurrogateKey.

Conversion des dates et calcul des indicateurs.

- Chargement :

Chargement final dans les tables MySQL du Data Warehouse avec tMySQLOutput.

Respect du modèle en étoile : les dimensions sont chargées avant la table de faits.
