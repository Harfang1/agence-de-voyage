# Dictionnaire de données épuré – Agence de voyage

| **Entité**       | **Attribut**       | **Type**   | **Taille** | **Clé** | **Obligatoire** | **Description / Règle métier** |
|------------------|-------------------|------------|------------|---------|-----------------|-------------------------------|
| **CLIENT**       | id_client         | INTEGER    | —          | PK      | O               | Identifiant unique du client |
|                  | nom               | VARCHAR    | 100        | —       | O               | Nom du client |
|                  | prenom            | VARCHAR    | 100        | —       | O               | Prénom du client |
|                  | email             | VARCHAR    | 255        | —       | N               | Adresse e-mail du client |
|                  | telephone         | VARCHAR    | 20         | —       | N               | Numéro de téléphone |
|                  | adresse           | VARCHAR    | 255        | —       | N               | Adresse postale du client |
| **ACCOMPAGNATEUR** | id_accompagnateur | INTEGER   | —          | PK      | O               | Identifiant unique de l’accompagnateur |
|                  | nom               | VARCHAR    | 100        | —       | O               | Nom de l’accompagnateur |
|                  | prenom            | VARCHAR    | 100        | —       | O               | Prénom de l’accompagnateur |
| **VILLE**        | id_ville          | INTEGER    | —          | PK      | O               | Identifiant unique de la ville |
|                  | nom               | VARCHAR    | 100        | —       | O               | Nom de la ville |
| **HOTEL**        | id_hotel          | INTEGER    | —          | PK      | O               | Identifiant unique de l’hôtel |
|                  | nom               | VARCHAR    | 100        | —       | O               | Nom de l’hôtel |
|                  | id_ville          | INTEGER    | —          | FK      | O               | Référence à VILLE (**RG2 : un seul hôtel par ville**) |
| **CIRCUIT**      | id_circuit        | INTEGER    | —          | PK      | O               | Identifiant unique du circuit |
|                  | date_depart       | DATE       | —          | —       | O               | Date de départ du circuit |
|                  | date_arrivee      | DATE       | —          | —       | O               | Date d’arrivée du circuit |
|                  | id_ville_depart   | INTEGER    | —          | FK      | O               | Référence à VILLE (départ) |
|                  | id_ville_arrivee  | INTEGER    | —          | FK      | O               | Référence à VILLE (arrivée) |
|                  | id_accompagnateur | INTEGER    | —          | FK      | O               | Référence à ACCOMPAGNATEUR (**RG4 : un seul par circuit**) |
| **NUIT**         | id_nuit           | INTEGER    | —          | PK      | O               | Identifiant unique de la nuit |
|                  | id_circuit        | INTEGER    | —          | FK      | O               | Référence au circuit |
|                  | id_hotel          | INTEGER    | —          | FK      | O               | Hôtel de la nuit (**RG5**) |
|                  | date_nuit         | DATE       | —          | —       | O               | Date de la nuit |
|                  | ordre_nuit        | INTEGER    | —          | —       | O               | Ordre de la nuit dans le circuit |
| **RESERVATION**  | id_reservation    | INTEGER    | —          | PK      | O               | Identifiant unique de la réservation |
|                  | id_client         | INTEGER    | —          | FK      | O               | Référence au client |
|                  | id_circuit        | INTEGER    | —          | FK      | O               | Référence au circuit réservé |
|                  | date_reservation  | DATE       | —          | —       | O               | Date de la réservation |
|                  | acompte_verse     | DECIMAL    | —          | —       | N               | Montant de l’acompte (**RG12**) |
|                  | solde_paye        | DECIMAL    | —          | —       | N               | Montant du solde payé (**RG12**) |

---

## Contraintes globales (RG)
- **RG2** : un seul hôtel par ville.  
- **RG4** : un seul accompagnateur par circuit.  
- **RG5** : chaque nuit d’un circuit doit être associée à un hôtel.  
- **RG6** : un circuit comprend au moins deux villes.  
- **RG8** : une ville ne peut être point de départ ou d’arrivée que pour un seul circuit à une date donnée.  
- **RG12** : une réservation peut contenir un acompte et/ou un solde.
