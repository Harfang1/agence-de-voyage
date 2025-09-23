faire le tableau ici

| **Entité**         | **Attribut**       | **Type** | **Taille** | **Clé** | **Obligatoire** | **Description / Règle métier**                    |
| ------------------ | ------------------ | -------- | ---------- | ------- | --------------- | ------------------------------------------------- |
| **CLIENT**         | id\_client         | INTEGER  | —          | PK      | O               | Identifiant unique du client                      |
|                    | nom                | VARCHAR  | 100        | —       | O               | Nom du client                                     |
|                    | prenom             | VARCHAR  | 100        | —       | O               | Prénom du client                                  |
|                    | email              | VARCHAR  | 255        | —       | N               | Adresse e-mail (optionnelle)                      |
|                    | telephone          | VARCHAR  | 20         | —       | N               | Numéro de téléphone                               |
|                    | adresse            | VARCHAR  | 255        | —       | N               | Adresse postale du client                         |
| **ACCOMPAGNATEUR** | id\_accompagnateur | INTEGER  | —          | PK      | O               | Identifiant unique de l’accompagnateur            |
|                    | nom                | VARCHAR  | 100        | —       | O               | Nom de l’accompagnateur                           |
|                    | prenom             | VARCHAR  | 100        | —       | O               | Prénom de l’accompagnateur                        |
| **VILLE**          | id\_ville          | INTEGER  | —          | PK      | O               | Identifiant unique de la ville                    |
|                    | nom\_ville         | VARCHAR  | 100        | —       | O               | Nom de la ville                                   |
| **HOTEL**          | id\_hotel          | INTEGER  | —          | PK      | O               | Identifiant unique de l’hôtel                     |
|                    | nom\_hotel         | VARCHAR  | 100        | —       | O               | Nom de l’hôtel                                    |
|                    | id\_ville          | INTEGER  | —          | FK      | O               | Référence à VILLE (un seul hôtel par ville – RG2) |
| **CIRCUIT**        | id\_circuit        | INTEGER  | —          | PK      | O               | Identifiant unique du circuit                     |
|                    | date\_depart       | DATE     | —          | —       | O               | Date de départ du circuit                         |
|                    | date\_arrivee      | DATE     | —          | —       | O               | Date d’arrivée du circuit                         |
|                    | id\_ville\_depart  | INTEGER  | —          | FK      | O               | Référence à VILLE (ville de départ – RG8)         |
|                    | id\_ville\_arrivee | INTEGER  | —          | FK      | O               | Référence à VILLE (ville d’arrivée – RG8)         |
|                    | id\_accompagnateur | INTEGER  | —          | FK      | O               | Référence à ACCOMPAGNATEUR (1 par circuit – RG4)  |
| **NUIT**           | id\_nuit           | INTEGER  | —          | PK      | O               | Identifiant unique de la nuit                     |
|                    | id\_circuit        | INTEGER  | —          | FK      | O               | Référence au circuit                              |
|                    | id\_hotel          | INTEGER  | —          | FK      | O               | Hôtel de la nuit (RG5)                            |
|                    | date\_nuit         | DATE     | —          | —       | O               | Date de la nuit                                   |
|                    | ordre\_nuit        | INTEGER  | —          | —       | O               | Ordre de la nuit dans le circuit                  |
| **RESERVATION**    | id\_reservation    | INTEGER  | —          | PK      | O               | Identifiant unique de la réservation              |
|                    | id\_client         | INTEGER  | —          | FK      | O               | Référence au client                               |
|                    | id\_circuit        | INTEGER  | —          | FK      | O               | Référence au circuit réservé                      |
|                    | date\_reservation  | DATE     | —          | —       | O               | Date de la réservation                            |
|                    | acompte\_verse     | DECIMAL  | —          | —       | N               | Montant de l’acompte (RG12)                       |
|                    | solde\_paye        | DECIMAL  | —          | —       | N               | Montant du solde payé (RG12)                      |



