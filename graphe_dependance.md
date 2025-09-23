# Dictionnaire des Entités GDF

## CLIENT

| Champ               | Type    | Clé / Contraintes            | Remarques                           |
|--------------------|---------|------------------------------|------------------------------------|
| Num_Client         | INT     | PK                           | Identifiant unique                 |
| Nom_Client         | VARCHAR |                              | Obligatoire                         |
| Prenom_Client      | VARCHAR |                              | Obligatoire                         |
| Adresse_Client     | VARCHAR |                              |                                    |
| Tel_Client         | VARCHAR |                              | Format valide                        |
| Email_Client       | VARCHAR | UNIQUE si non NULL           | Relation → Num_Client si présent    |
| Date_Naissance_Client | DATE |                              |                                    |

## CIRCUIT

| Champ               | Type    | Clé / Contraintes            | Remarques                           |
|--------------------|---------|------------------------------|------------------------------------|
| Code_Circuit       | INT     | PK                           | Identifiant unique                 |
| Nom_Circuit        | VARCHAR |                              |                                    |
| Description_Circuit| VARCHAR |                              |                                    |
| Date_Depart        | DATE    |                              |                                    |
| Date_Retour        | DATE    |                              |                                    |
| Prix_Circuit       | DECIMAL |                              |                                    |
| Nb_Places_Max      | INT     |                              |                                    |
| Statut_Circuit     | VARCHAR |                              |                                    |
| Num_Accompagnateur | INT     | FK → ACCOMPAGNATEUR          |                                    |
| Code_Periode       | INT     | FK → PERIODE                 |                                    |

## VILLE

| Champ       | Type    | Clé / Contraintes                 | Remarques                              |
|------------|---------|----------------------------------|---------------------------------------|
| Code_Ville | INT     | PK                               | Identifiant unique                     |
| Nom_Ville  | VARCHAR |                                  | Dépendance bidirectionnelle (RG3)     |
| Pays       | VARCHAR |                                  |                                       |
| Description| VARCHAR |                                  |                                       |

## HOTEL

| Champ         | Type    | Clé / Contraintes              | Remarques                             |
|---------------|---------|-------------------------------|--------------------------------------|
| Num_Hotel     | INT     | PK                            | Identifiant unique                    |
| Code_Ville    | INT     | FK → VILLE(Code_Ville)        | Dépendance bidirectionnelle (RG2)    |
| Nom_Hotel     | VARCHAR |                               |                                      |
| Adresse_Hotel | VARCHAR |                               |                                      |
| Classe_Hotel  | VARCHAR |                               |                                      |
| Tel_Hotel     | VARCHAR |                               |                                      |

## ACCOMPAGNATEUR

| Champ          | Type    | Clé / Contraintes            | Remarques                           |
|----------------|---------|------------------------------|------------------------------------|
| Num_Accompagnateur | INT  | PK                           | Identifiant unique                 |
| Nom_Accomp     | VARCHAR |                              |                                    |
| Prenom_Accomp  | VARCHAR |                              |                                    |
| Tel_Accomp     | VARCHAR |                              |                                    |
| Email_Accomp   | VARCHAR |                              | Format valide                        |
| Langues        | VARCHAR |                              |                                    |

## RESERVATION

| Champ           | Type    | Clé / Contraintes                  | Remarques                             |
|-----------------|---------|-----------------------------------|--------------------------------------|
| Num_Reservation | INT     | PK                                | Identifiant unique                    |
| Date_Reservation| DATE    |                                   |                                      |
| Statut_Reservation | VARCHAR |                                |                                      |
| Montant_Acompte | DECIMAL |                                   |                                      |
| Date_Acompte    | DATE    |                                   |                                      |
| Montant_Solde   | DECIMAL |                                   |                                      |
| Date_Solde      | DATE    |                                   |                                      |
| Num_Client      | INT     | FK → CLIENT(Num_Client)           |                                      |
| Code_Circuit    | INT     | FK → CIRCUIT(Code_Circuit)       |                                      |
| Clé_Composite   |         | Num_Client + Code_Circuit         | Clé composite                         |

## PERIODE

| Champ           | Type    | Clé / Contraintes            | Remarques                             |
|-----------------|---------|------------------------------|--------------------------------------|
| Code_Periode    | INT     | PK                           | Identifiant unique                    |
| Nom_Periode     | VARCHAR |                              |                                      |
| Date_Debut      | DATE    |                              |                                      |
| Date_Fin        | DATE    |                              |                                      |
| Date_Limite_D1  | DATE    |                              |                                      |
| Date_Limite_D2  | DATE    |                              |                                      |

## ETAPE

| Champ       | Type    | Clé / Contraintes                     | Remarques                           |
|------------|---------|--------------------------------------|------------------------------------|
| Code_Circuit | INT   | FK → CIRCUIT(Code_Circuit)           |                                    |
| Num_Ordre   | INT    |                                      | Numéro de l’étape dans le circuit |
| Code_Ville  | INT    | FK → VILLE(Code_Ville)               |                                    |
| Nb_Nuits    | INT    |                                      |                                    |
| Num_Hotel   | INT    | FK → HOTEL(Num_Hotel)                |                                    |
| Clé_Alternative |     | (Code_Circuit, Code_Ville) → Num_Ordre |                                    |
