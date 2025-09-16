# 1 - Analyse des besoins

## 1. Lister les acteurs

| Acteur                      | Rôle et responsabilités                                                                                                                |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Client**                  | Recherche / réservation / reçoit confirmation                                                                                          |
| **Réceptionniste**          | Crée/modifie/annule réservation, enregistre paiement, check in/out, consulte historiques clients                                       |
| **Admin**                   | Gère chambres, tarifs, crée comptes utilisateurs avec rôles (client, réceptionniste, admin), paramètres (saisons, réductions, taxes …) |
| **Gestionnaire des stocks** | Suit stock général, recharge minibar                                                                                                   |
| **Système de paiement**     | Gestion des transactions financières                                                                                                   |
| **Service d'email**         | Envoi des notifications et confirmations                                                                                               |

## 2. Fonctions principales du système

### Gestion des clients

- CRUD client
- Recherche rapide
- Historique de séjours
- Calcul auto de l'éligibilité à la réduction 10e réservation
- Consentements RGPD

### Gestion des chambres

- CRUD chambre et type
- Caractéristiques
- Statut (libre/occupée/maintenance)
- Rattachement minibar

### Gestion des stocks minibar

- Catalogue produits + catégories
- Stock général hôtel
- Stock par chambre
- Mouvements (entrée, sortie, réassort)
- Seuils d'alerte

### Réservations

- Création/modification/annulation
- Moteur de disponibilité par période
- Attribution de chambre
- Application réductions et tarifs saisonniers
- Check-in/out

### Paiements

- Enregistrement paiements (espèces/carte/en ligne)
- Multi-règlements
- Remboursements/avoirs
- Rapprochement avec réservation

### Facturation

- Génération facture PDF avec TVA et détails consommations minibar
- Envoi au client
- Liste des factures payées

### Utilisateurs et rôles

- Comptes
- Rôles (admin/réceptionniste/client)
- Authentification
- Journal d'audit

### Notifications

- Emails de confirmation/modification/annulation
- Rappels séjour
- Alertes stock bas minibar

### Reporting & tableaux de bord

- Taux d'occupation
- CA par période
- Suivi des consommations minibar
- Exports

### Paramétrage

- Tarifs par saison
- Taxes
- Modèles d'email
- Moyens de paiement
- Politiques d'annulation

## 3. Dictionnaire de données

### Table : Clients

- Utilisateur identifiant → **id_client** → INT (PK, AI)
- Nom du client → **nom** → texte
- Prénom du client → **prénom** → texte
- Adresse email du client → **email** → texte (UNIQUE)
- Numéro de téléphone → **téléphone** → texte
- Adresse postale → **adresse** → texte

### Table : Statut_Chambre

- Identifiant statut → **id_statut** → entier (PK)
- Libellé statut → **libelle** → varchar(50)
- Couleur statut → **couleur** → varchar(7)

### Table : Chambres

- Identifiant unique de la chambre → **id_chambre** → entier (PK)
- Numéro de la chambre → **numéro** → unique
- Type (simple, double, suite) → **type** → texte
- Prix par nuit → **prix_nuit** → décimal
- Statut → **statut** → FK (Statut_Chambre)

### Table : Réservation

- Identifiant unique de la réservation → **id_reservation** → entier (PK)
- Date d'arrivée → **date_arrivée** → date
- Date de départ → **date_depart** → date
- Montant total calculé → **montant_total** → décimal
- Statut (en attente, confirmée, annulée) → **statut** → texte
- Référence vers le client → **id_client** → entier (FK)
- Référence vers la chambre → **id_chambre** → entier (FK)

### Table : Paiement

- Identifiant unique du paiement → **id_paiement** → entier (PK)
- Espèces, carte, en ligne → **mode_paiement** → texte
- Montant payé → **montant** → décimal (8,2)
- Date du paiement → **date_paiement** → date
- Référence vers la réservation → **id_reservation** → entier (FK)

### Table : Statut_Facture

- Identifiant statut → **id_statut** → entier (PK)
- Libellé statut → **libelle** → varchar(50)
- Couleur statut → **couleur** → varchar(7)

### Table : Facture

- Identifiant unique de la facture → **id_facture** → entier (PK)
- Date d'émission → **date_facture** → date
- Montant facturé → **montant** → décimal
- TVA → **tva** → DECIMAL(8,2)
- Référence vers la réservation → **id_reservation** → entier (FK)
- Statut de la facture → **statut** → FK (Statut_Facture)

### Table : Produits

- Identifiant du produit → **id_produit** → INT (PK, AI)
- Nom du produit → **nom** → VARCHAR(50)
- Categorie → **categorie** → VARCHAR(50)
- Prix unitaire → **prix_unitaire** → FLOAT
- Stock général → **stock_général** → INT
- Stock initial minibar → **stock_minibar** → INT

### Table : Minibar

- Identifiant du minibar → **id_minibar** → INT (PK, AI)
- Identifiant de la chambre → **id_chambre** → INT (FK)

### Table : Produits_minibar

- Quantite → **quantite** → INT
- Identifiant du produit → **id_produit** → INT (FK)
- Identifiant du minibar → **id_minibar** → INT (FK)
