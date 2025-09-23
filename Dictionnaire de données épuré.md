## Dictionnaire épuré 

| Entité | Attribut | Type | Longueur | Clé | Obligatoire | Description |
|--------|----------|------|----------|-----|-------------|-------------|
| **CLIENT** | NumClient | Entier | - | PK | Oui | Identifiant unique du client |
| CLIENT | NomClient | Chaîne | 50 | - | Oui | Nom de famille du client |
| CLIENT | PrenomClient | Chaîne | 50 | - | Oui | Prénom du client |
| CLIENT | AdresseClient | Chaîne | 200 | - | Oui | Adresse postale complète |
| CLIENT | TelClient | Chaîne | 15 | - | Non | Numéro de téléphone |
| CLIENT | EmailClient | Chaîne | 100 | UQ | Non | Adresse email (unique) |
| CLIENT | DateNaissanceClient | Date | - | - | Oui | Date de naissance |
| **CIRCUIT** | CodeCircuit | Chaîne | 10 | PK | Oui | Code unique du circuit |
| CIRCUIT | NomCircuit | Chaîne | 100 | - | Oui | Nom du circuit touristique |
| CIRCUIT | DescriptionCircuit | Texte | 500 | - | Non | Description détaillée |
| CIRCUIT | DateDepart | Date | - | - | Oui | Date de départ du circuit |
| CIRCUIT | DateRetour | Date | - | - | Oui | Date de retour du circuit |
| CIRCUIT | PrixCircuit | Décimal | 10,2 | - | Oui | Prix du circuit |
| CIRCUIT | NbPlacesMax | Entier | - | - | Oui | Nombre maximum de places |
| CIRCUIT | StatutCircuit | Chaîne | 20 | - | Oui | Statut (Programmé, Maintenu, Annulé) |
| CIRCUIT | NumAccompagnateur | Entier | - | FK | Oui | Numéro de l'accompagnateur |
| CIRCUIT | CodePeriode | Chaîne | 10 | FK | Oui | Code de la période |
| **VILLE** | CodeVille | Chaîne | 10 | PK | Oui | Code unique de la ville |
| VILLE | NomVille | Chaîne | 100 | UQ | Oui | Nom de la ville (unique) |
| VILLE | Pays | Chaîne | 50 | - | Oui | Pays de la ville |
| VILLE | Description | Texte | 300 | - | Non | Description touristique |
| **HÔTEL** | NumHotel | Entier | - | PK | Oui | Numéro unique de l'hôtel |
| HÔTEL | NomHotel | Chaîne | 100 | - | Oui | Nom de l'hôtel |
| HÔTEL | AdresseHotel | Chaîne | 200 | - | Oui | Adresse de l'hôtel |
| HÔTEL | ClasseHotel | Entier | - | - | Non | Classification (1-5 étoiles) |
| HÔTEL | TelHotel | Chaîne | 15 | - | Non | Téléphone de l'hôtel |
| HÔTEL | CodeVille | Chaîne | 10 | FK | Oui | Code de la ville |
| **ACCOMPAGNATEUR** | NumAccompagnateur | Entier | - | PK | Oui | Numéro unique accompagnateur |
| ACCOMPAGNATEUR | NomAccomp | Chaîne | 50 | - | Oui | Nom de l'accompagnateur |
| ACCOMPAGNATEUR | PrenomAccomp | Chaîne | 50 | - | Oui | Prénom de l'accompagnateur |
| ACCOMPAGNATEUR | TelAccomp | Chaîne | 15 | - | Non | Téléphone |
| ACCOMPAGNATEUR | EmailAccomp | Chaîne | 100 | - | Non | Email professionnel |
| ACCOMPAGNATEUR | Langues | Chaîne | 100 | - | Non | Langues parlées |
| **RÉSERVATION** | NumReservation | Entier | - | PK | Oui | Numéro unique de réservation |
| RÉSERVATION | DateReservation | Date | - | - | Oui | Date de la demande |
| RÉSERVATION | StatutReservation | Chaîne | 20 | - | Oui | En attente, Confirmée, Définitive, Annulée |
| RÉSERVATION | MontantAcompte | Décimal | 10,2 | - | Non | Montant de l'acompte versé |
| RÉSERVATION | DateAcompte | Date | - | - | Non | Date du versement acompte |
| RÉSERVATION | MontantSolde | Décimal | 10,2 | - | Non | Montant du solde |
| RÉSERVATION | DateSolde | Date | - | - | Non | Date du versement solde |
| RÉSERVATION | NumClient | Entier | - | FK | Oui | Numéro du client |
| RÉSERVATION | CodeCircuit | Chaîne | 10 | FK | Oui | Code du circuit |
| **PÉRIODE** | CodePeriode | Chaîne | 10 | PK | Oui | Code de la période |
| PÉRIODE | NomPeriode | Chaîne | 50 | - | Oui | Nom de la période (ex: Été 2025) |
| PÉRIODE | DateDebut | Date | - | - | Oui | Date de début de période |
| PÉRIODE | DateFin | Date | - | - | Oui | Date de fin de période |
| PÉRIODE | DateLimiteD1 | Date | - | - | Oui | Date limite pour 2ème versement |
| PÉRIODE | DateLimiteD2 | Date | - | - | Oui | Date limite maintien circuit |

### Relation ÉTAPE (Many-to-Many entre CIRCUIT et VILLE)
| Attribut | Type | Longueur | Clé | Description |
|----------|------|----------|-----|-------------|
| CodeCircuit | Chaîne | 10 | FK/PK | Code du circuit |
| CodeVille | Chaîne | 10 | FK/PK | Code de la ville |
| NumOrdre | Entier | - | PK | Ordre de visite dans le circuit |
| NbNuits | Entier | - | - | Nombre de nuits dans cette ville |
| NumHotel | Entier | - | FK | Hôtel pour cette étape |

## Justification des suppressions

1. **NbPlacesReservees** : Redondant car calculable par COUNT() des réservations définitives
2. **VilleDepartCode** dans CIRCUIT : Redondant car déterminable par ÉTAPE avec NumOrdre=1
3. **Âge calculé** : Peut être déduit de DateNaissanceClient
4. **Attributs système** : Dates de création/modification non demandées dans le métier
