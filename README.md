# BlueMoon – Application de gestion d’hôtel

## 1. Présentation du projet

BlueMoon est un projet pédagogique de conception d’une application complète de gestion d’hôtel.  
Objectifs :

- Informatiser la gestion des clients, chambres, réservations, paiements et stocks de minibars.
- Mettre en œuvre les étapes classiques de l’ingénierie logicielle (analyse, modélisation Merise, UML, design patterns).

Travail réalisé par : **Hicham – Tristan – Antoine**

## 2. Fonctionnalités principales

- Gestion des clients (création, recherche rapide, historique, RGPD, réduction automatique à la 10e réservation).
- Gestion des chambres et minibars (types, statuts, rattachement minibar, stock général et par chambre).
- Réservations (création, modification, annulation, moteur de disponibilité, check-in/out, tarifs saisonniers).
- Paiements & facturation (multi-modes, TVA, PDF, suivi factures, facturation minibar).
- Comptes utilisateurs et rôles (admin, réceptionniste, client).
- Notifications (emails de confirmation, alertes stock).
- Reporting (taux d’occupation, CA, suivi minibar).
- Paramétrage (tarifs saisonniers, taxes, modèles d’email).

## 3. Modélisation des données

- **MCD → MLD → MPD** avec entités Client, Chambre, Réservation, Paiement, Facture, Produits, Minibar.
- Base de données choisie : **PostgreSQL** (sécurité, contraintes avancées, performance sur gros volumes, gestion native des chevauchements).
- Voir diagrammes dans le `pdf`.

## 4. Modélisation UML

- Cas d’utilisation (use cases)
- Diagrammes de séquence (ex. réserver une chambre)
- Diagramme de classes complet du système
- Diagramme d’activité (check-in client)
- Liens PlantUML fournis dans le `pdf`.

## 5. Design Patterns

- **MVC** (séparation interface/logiciel/données)
- **DAO** (accès aux données)
- **Observer** (notifications aux clients, alertes stock)
- **Singleton** (accès unique aux ressources partagées, ex. configuration)
- Diagrammes UML correspondants dans le `pdf`.

## 6. Organisation du projet

### Rétroplanning conception

- J1 matin : Analyse besoins + dictionnaire
- J1 aprèm : Fonctions + MCD
- J2 matin : MLD → MPD + choix SGBD
- J2 aprèm : UML (Use cases, séquence, activité)
- J3 matin : Diagrammes UML
- J3 aprèm : Refonte schémas UML
- J4 matin : Design patterns
- J4 aprem : UML patterns + README + slides

### Planning prévisionnel développement

Voir tableau dans le `pdf`.
Grandes étapes : socle technique → gestion utilisateurs → clients/chambres → moteur de réservation → paiements/facturation → notifications → stock minibar → reporting.

## 7. Technologies et outils

- **Base de données** : PostgreSQL
- **Modélisation** : Merise, PlantUML
- **Gestion de versions** : Git
- **Documentation** : Markdown, Google slides

## 8. Livrables

- Modèles Merise et UML
- Diagrammes des patterns
- Planning conception et développement
- Slides de présentation
- README (ce fichier)

## 9. Auteurs

Projet réalisé dans le cadre du TP Perf Conception – LiveCampus.  
Contributeurs : Hicham, Tristan, Antoine.
