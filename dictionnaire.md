# Dictionnaire de données - Agence de voyage

## Analyse des règles de gestion

### Entités identifiées :
- **CLIENT** : Personnes effectuant des réservations
- **CIRCUIT** : Voyages organisés par l'agence
- **VILLE** : Destinations des circuits
- **HÔTEL** : Hébergements dans les villes
- **ACCOMPAGNATEUR** : Personnel encadrant les voyages
- **RÉSERVATION** : Demandes de participation aux circuits
- **PÉRIODE** : Périodes de programmation des circuits

## Dictionnaire de données détaillé

| Entité | Attribut | Type | Longueur | Clé | Description |
|--------|----------|------|----------|-----|-------------|
| **CLIENT** | NumClient | Entier | - | PK | Identifiant unique du client |
| CLIENT | NomClient | Chaîne | 50 | - | Nom de famille du client |
| CLIENT | PrenomClient | Chaîne | 50 | - | Prénom du client |
| CLIENT | AdresseClient | Chaîne | 200 | - | Adresse postale complète |
| CLIENT | TelClient | Chaîne | 15 | - | Numéro de téléphone |
| CLIENT | EmailClient | Chaîne | 100 | - | Adresse email |
| CLIENT | DateNaissanceClient | Date | - | - | Date de naissance |
| **CIRCUIT** | CodeCircuit | Chaîne | 10 | PK | Code unique du circuit |
| CIRCUIT | NomCircuit | Chaîne | 100 | - | Nom du circuit touristique |
| CIRCUIT | DescriptionCircuit | Texte | 500 | - | Description détaillée |
| CIRCUIT | DateDepart | Date | - | - | Date de départ du circuit |
| CIRCUIT | DateRetour | Date | - | - | Date de retour du circuit |
| CIRCUIT | PrixCircuit | Décimal | 10,2 | - | Prix du circuit |
| CIRCUIT | NbPlacesMax | Entier | - | - | Nombre maximum de places |
| CIRCUIT | NbPlacesReservees | Entier | - | - | Places déjà réservées |
| CIRCUIT | StatutCircuit | Chaîne | 20 | - | Statut (Programmé, Maintenu, Annulé) |
| CIRCUIT | VilleDepartCode | Chaîne | 10 | FK | Code ville de départ |
| CIRCUIT | NumAccompagnateur | Entier | - | FK | Numéro de l'accompagnateur |
| CIRCUIT | CodePeriode | Chaîne | 10 | FK | Code de la période |
| **VILLE** | CodeVille | Chaîne | 10 | PK | Code unique de la ville |
| VILLE | NomVille | Chaîne | 100 | UQ | Nom de la ville (unique) |
| VILLE | Pays | Chaîne | 50 | - | Pays de la ville |
| VILLE | Description | Texte | 300 | - | Description touristique |
| **HÔTEL** | NumHotel | Entier | - | PK | Numéro unique de l'hôtel |
| HÔTEL | NomHotel | Chaîne | 100 | - | Nom de l'hôtel |
| HÔTEL | AdresseHotel | Chaîne | 200 | - | Adresse de l'hôtel |
| HÔTEL | ClasseHotel | Entier | - | - | Classification (1-5 étoiles) |
| HÔTEL | TelHotel | Chaîne | 15 | - | Téléphone de l'hôtel |
| HÔTEL | CodeVille | Chaîne | 10 | FK | Code de la ville |
| **ACCOMPAGNATEUR** | NumAccompagnateur | Entier | - | PK | Numéro unique accompagnateur |
| ACCOMPAGNATEUR | NomAccomp | Chaîne | 50 | - | Nom de l'accompagnateur |
| ACCOMPAGNATEUR | PrenomAccomp | Chaîne | 50 | - | Prénom de l'accompagnateur |
| ACCOMPAGNATEUR | TelAccomp | Chaîne | 15 | - | Téléphone |
| ACCOMPAGNATEUR | EmailAccomp | Chaîne | 100 | - | Email professionnel |
| ACCOMPAGNATEUR | Langues | Chaîne | 100 | - | Langues parlées |
| **RÉSERVATION** | NumReservation | Entier | - | PK | Numéro unique de réservation |
| RÉSERVATION | DateReservation | Date | - | - | Date de la demande |
| RÉSERVATION | StatutReservation | Chaîne | 20 | - | En attente, Confirmée, Définitive, Annulée |
| RÉSERVATION | MontantAcompte | Décimal | 10,2 | - | Montant de l'acompte versé |
| RÉSERVATION | DateAcompte | Date | - | - | Date du versement acompte |
| RÉSERVATION | MontantSolde | Décimal | 10,2 | - | Montant du solde |
| RÉSERVATION | DateSolde | Date | - | - | Date du versement solde |
| RÉSERVATION | NumClient | Entier | - | FK | Numéro du client |
| RÉSERVATION | CodeCircuit | Chaîne | 10 | FK | Code du circuit |
| **PÉRIODE** | CodePeriode | Chaîne | 10 | PK | Code de la période |
| PÉRIODE | NomPeriode | Chaîne | 50 | - | Nom de la période (ex: Été 2025) |
| PÉRIODE | DateDebut | Date | - | - | Date de début de période |
| PÉRIODE | DateFin | Date | - | - | Date de fin de période |
| PÉRIODE | DateLimiteD1 | Date | - | - | Date limite pour 2ème versement |
| PÉRIODE | DateLimiteD2 | Date | - | - | Date limite maintien circuit |

## Relations identifiées

| Relation | Description | Entités concernées |
|----------|-------------|-------------------|
| ÉTAPE | Un circuit passe par plusieurs villes | CIRCUIT - VILLE |
| SÉJOURNER | À chaque étape, séjour dans un hôtel | ÉTAPE - HÔTEL |
| RÉSERVER | Un client réserve un circuit | CLIENT - CIRCUIT |
| ACCOMPAGNER | Un accompagnateur guide un circuit | ACCOMPAGNATEUR - CIRCUIT |
| PROGRAMMER | Les circuits sont programmés par période | CIRCUIT - PÉRIODE |
| SITUER | Un hôtel est situé dans une ville | HÔTEL - VILLE |

