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

Les données proviennent de plusieurs fichiers Excel (étudiants, filières, inscriptions). 

Utilisation de composants tFileInputExcel dans Talend pour lire chaque fichier.

- Transformation :

Nettoyage et normalisation des données avec tMap, tFilterRow, tUniqRow.

Création de clés de substitution avec tSurrogateKey.

Conversion des dates et calcul des indicateurs.

- Chargement :

Chargement final dans les tables MySQL du Data Warehouse avec tMySQLOutput.

Respect du modèle en étoile : les dimensions sont chargées avant la table de faits.

<img width="1543" height="266" alt="image" src="https://github.com/user-attachments/assets/fd3fde2b-fd3e-4901-b35e-e6c23497636c" />


# 3- Extraction des données (ETL avec Talend)

## Sources :
Les données proviennent de fichiers Excel ou de bases de données SQL (Étudiants, Filières, Inscriptions).

- Outil utilisé : Talend Open Studio

- tFileInputExcel : lire les fichiers Excel.

- tMysqlInput : extraire les données d’une base SQL.

- tMap : pour relier et transformer les données.

- tMySQLOutput : pour charger les données dans le Data Warehouse.

## Processus d’extraction :

- Lire les fichiers sources (étudiants, filières, inscriptions).

- Sélectionner les colonnes utiles.

- Transférer ces données vers les composants de transformation.

# 4- Transformations nécessaires

- Nettoyage des données :

Supprimer les doublons (tUniqRow).

- Normalisation des dates :

Conversion du format texte → date (TalendDate.parseDate("yyyy-MM-dd", colonne)).

Extraction du mois et de l’année pour la dimension temps.

# Jobs : 
- dimensions
<img width="943" height="505" alt="image" src="https://github.com/user-attachments/assets/184f13f5-2198-42e9-879d-6af7c5338f4c" />
<img width="1919" height="1023" alt="image" src="https://github.com/user-attachments/assets/f455e15b-a987-4d9f-adea-5dfe370297b4" />

- Fait : 
<img width="979" height="600" alt="image" src="https://github.com/user-attachments/assets/9da406fa-b4f5-4455-81e0-c36236ebb41c" />
<img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/c3dbb3d1-b8b0-431b-b309-242103b0066b" />
<img width="1454" height="742" alt="image" src="https://github.com/user-attachments/assets/2318d0b6-06d7-4fad-b174-af027fbb4e77" />




