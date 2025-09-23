## Dictionnaire épuré 

| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **CLIENT** | Num_Client | Entier | - | PK | Oui | Identifiant unique du client |
| CLIENT | Nom_Client | Chaîne | 50 | - | Oui | Nom de famille du client |
| CLIENT | Prenom_Client | Chaîne | 50 | - | Oui | Prénom du client |
| CLIENT | Adresse_Client | Chaîne | 200 | - | Oui | Adresse postale complète |
| CLIENT | Tel_Client | Chaîne | 15 | - | Non | Numéro de téléphone |
| CLIENT | Email_Client | Chaîne | 100 | UQ | Non | Adresse email (unique) |
| CLIENT | Date_Naissance_Client | Date | - | - | Oui | Date de naissance |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
|CIRCUIT| Code_Circuit | Chaîne | 10 | PK | Oui | Code unique du circuit |
| CIRCUIT | Nom_Circuit | Chaîne | 100 | - | Oui | Nom du circuit touristique |
| CIRCUIT | Description_Circuit | Texte | 500 | - | Non | Description détaillée |
| CIRCUIT | Date_Depart | Date | - | - | Oui | Date de départ du circuit |
| CIRCUIT | Date_Retour | Date | - | - | Oui | Date de retour du circuit |
| CIRCUIT | Prix_Circuit | Décimal | 10,2 | - | Oui | Prix du circuit |
| CIRCUIT | Nb_Places_Max | Entier | - | - | Oui | Nombre maximum de places |
| CIRCUIT | Statut_Circuit | Chaîne | 20 | - | Oui | Statut (Programmé, Maintenu, Annulé) |
| CIRCUIT | Num_Accompagnateur | Entier | - | FK | Oui | Numéro de l'accompagnateur |
| CIRCUIT | Code_Periode | Chaîne | 10 | FK | Oui | Code de la période |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **VILLE** | Code_Ville | Chaîne | 10 | PK | Oui | Code unique de la ville |
| VILLE | Nom_Ville | Chaîne | 100 | UQ | Oui | Nom de la ville (unique) |
| VILLE | Pays | Chaîne | 50 | - | Oui | Pays de la ville |
| VILLE | Description | Texte | 300 | - | Non | Description touristique |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **HÔTEL** | Num_Hotel | Entier | - | PK | Oui | Numéro unique de l'hôtel |
| HÔTEL | Nom_Hotel | Chaîne | 100 | - | Oui | Nom de l'hôtel |
| HÔTEL | Adresse_Hotel | Chaîne | 200 | - | Oui | Adresse de l'hôtel |
| HÔTEL | Classe_Hotel | Entier | - | - | Non | Classification (1-5 étoiles) |
| HÔTEL | Tel_Hotel | Chaîne | 15 | - | Non | Téléphone de l'hôtel |
| HÔTEL | Code_Ville | Chaîne | 10 | FK | Oui | Code de la ville |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **ACCOMPAGNATEUR** | Num_Accompagnateur | Entier | - | PK | Oui | Numéro unique accompagnateur |
| ACCOMPAGNATEUR | Nom_Accomp | Chaîne | 50 | - | Oui | Nom de l'accompagnateur |
| ACCOMPAGNATEUR | Prenom_Accomp | Chaîne | 50 | - | Oui | Prénom de l'accompagnateur |
| ACCOMPAGNATEUR | Tel_Accomp | Chaîne | 15 | - | Non | Téléphone |
| ACCOMPAGNATEUR | Email_Accomp | Chaîne | 100 | - | Non | Email professionnel |
| ACCOMPAGNATEUR | Langues | Chaîne | 100 | - | Non | Langues parlées |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **RÉSERVATION** | Num_Reservation | Entier | - | PK | Oui | Numéro unique de réservation |
| RÉSERVATION | Date_Reservation | Date | - | - | Oui | Date de la demande |
| RÉSERVATION | Statut_Reservation | Chaîne | 20 | - | Oui | En attente, Confirmée, Définitive, Annulée |
| RÉSERVATION | Montant_Acompte | Décimal | 10,2 | - | Non | Montant de l'acompte versé |
| RÉSERVATION | Date_Acompte | Date | - | - | Non | Date du versement acompte |
| RÉSERVATION | Montant_Solde | Décimal | 10,2 | - | Non | Montant du solde |
| RÉSERVATION | Date_Solde | Date | - | - | Non | Date du versement solde |
| RÉSERVATION | Num_Client | Entier | - | FK | Oui | Numéro du client |
| RÉSERVATION | Code_Circuit | Chaîne | 10 | FK | Oui | Code du circuit |
---


| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **PÉRIODE** | Code_Periode | Chaîne | 10 | PK | Oui | Code de la période |
| PÉRIODE | Nom_Periode | Chaîne | 50 | - | Oui | Nom de la période (ex: Été 2025) |
| PÉRIODE | Date_Debut | Date | - | - | Oui | Date de début de période |
| PÉRIODE | Date_Fin | Date | - | - | Oui | Date de fin de période |
| PÉRIODE | Date_LimiteD1 | Date | - | - | Oui | Date limite pour 2ème versement |
| PÉRIODE | Date_LimiteD2 | Date | - | - | Oui | Date limite maintien circuit |
---

### Relation ÉTAPE 
| Attribut | Type | Longueur | Clé | Description |
|----------|------|----------|-----|-------------|
| CodeCircuit | Chaîne | 10 | FK/PK | Code du circuit |
| CodeVille | Chaîne | 10 | FK/PK | Code de la ville |
| NumOrdre | Entier | - | PK | Ordre de visite dans le circuit |
| NbNuits | Entier | - | - | Nombre de nuits dans cette ville |
| NumHotel | Entier | - | FK | Hôtel pour cette étape |
---

## Justification des suppressions

1. **NbPlacesReservees** : Redondant car calculable par COUNT() des réservations définitives
2. **VilleDepartCode** dans CIRCUIT : Redondant car déterminable par ÉTAPE avec NumOrdre=1
3. **Âge calculé** : Peut être déduit de DateNaissanceClient
4. **Attributs système** : Dates de création/modification non demandées dans le métier
