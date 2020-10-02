
#CU01 - Noter une réservation

## Diagramme de cas d'utilisation

```plantuml
@startuml
left to right direction
package "Application de gestion hotelière" {
 usecase "CU01-Noter une reservartion d'une seule chambre" as N
 usecase "CU02-Noter une reservartion de plusieurs séjour" as S
 usecase "CU03-Transférer un séjour de chambre" as T
 
}
Commis --> N
Commis --> S
Commis --> T

@enduml
```

## Cas d'utilisation «Noter une réservation»

Scénario principal

1. Un client appelle à l'hôtel pour placer une réservation.
1. Le commis démarre une nouvelle réservation.
1. Le commis entre:
   1. La date d'arrivée;
   2. La date de départ;
        3. Le nom de la catégorie de chambre;
2. Le système inscrit les informations à la réservation.

## Interfaces usagé
```plantuml
@startuml
(*) --> "
{{
salt
{
Menu Principal
~~
[Noter une réservation]
}
}}
" as main

main -right-> "
{{
salt
{+
  Noter une réservation
  --
  Date d'arrivé | "2020-03-03"
  Date de départ | "2020-03-06"
  Catégorie | ^Categorie^ 
   [Cancel] | [Réserver]
}
}}
" as reserver

reserver -right-> "
{{
salt
{+
Menu Principal
~~
Confirmation de votre ?
--
  No confirmatino: | ?
  Date d'arrivé : |  2020-03-03
  Date de départ : | 2020-03-06
  Catégorie: | categorie1
==
[Noter une réservation]
  --}
}}
" as mainReservationConfirme

@enduml
```

## Modèle du domaine

```plantuml
@startuml
class Hotel <<Conteneur, Object physique>>
class Categorie <<Description d'entité>> {
  nom: String
}
class Reservation <<Transaction>>{
  dateArrive: date
  dateDepart: date
}
class Commis <<Role>>
class Chambre <<Objet physique, Contenu dans l'hotel, Produit d'une transaction>>
class Client <<Role>>

Hotel "1" -- "*" Chambre: possède
Chambre "*" -- "1" Categorie: appartient
Client "1" -- "1" Reservation: demande
Commis "1" -- "*" Reservation: cree
Hotel "1" -- "*" Commis : Emploie
Reservation "*" -- "1" Chambre : est reservé par <
@enduml
```

## Diagramme de séquence système

```plantuml
@startuml
title: Noter une réservation
skinparam style strictuml
Actor ":Commis" as Commis
Participant ":Systeme" as Systeme
Commis -> Systeme: demarrerReservation()
Commis <<-- Systeme: demander dateArrive,dateDepart, categorie, [nomCategorie] 
Commis -> Systeme: reserverChambre(dateArrive:string, dateDepart:string, nomCategorie: String)
Commis <<-- Systeme: confirmation?, menu principale
@enduml
```

## Contrat
**demarrerReservation()**
  - aucune

  **reserverChambre(dateArrive:string, dateDepart:string, nomCategorie: String)**
  - Précondition:
    - c:Commis est authentifier

  - Postcondition
    - Une instance r:Reservation a été créé
    - Une association a été créée entre r:Reservation et Chambre sur la base de correspondance avec categorie.nom == nomCategorie
    - Une association a été cree entre c:Commis et r:Reservation
    - Une instance cl:Client a été créée (? Nom, Prénom, Courriel)
    - Une association entre r:Reservation et cl:Client a été créée
    - r.dateArrivé est devenu dateArrivé
    - r.dateDepart est devenu dateDepart

## RDCU

### demarrerReservation()
```plantuml
@startuml
skinparam style strictuml
Participant ":ControleurReservation" as S
Participant "mc:Map<nom:String,categorie:Categorie>" as MC

note right  of MC: Visible par le \ncontroleur puisque \ntout les hotels utilisent \nles mêmes catégories
note left of S:Controleur de session
note right of S: use mc.keys() to get array of category
 -> S: [nomCategorie] = demarrerReservation()

@enduml
```

### reserverChambre
```plantuml
@startuml
skinparam style strictuml
Participant ":ControleurReservation" as S
Participant "c:Commis" as C
Participant "cl:Client" as CL
Participant "mc:Map<nom:String,categorie:Categorie>" as MC
Participant "cat:Categorie" as CAT
Participant "ch:Chambre" as CH
Participant "r:Reservation" as R

note right of C: Visible par le \ncontroleur\npuisque c'est une \nprécondition
note right  of MC: Visible par le \ncontroleur puisque \ntout les hotels utilisent \nles mêmes catégories
note left of S:Controleur de session
 -> S: reserverChambre(\ndateArrive:String, \ndateDepart:String, \ncategorie: String)
 note right of S: Createur
 S -> CL**: cl = Create(?)
 note right of S: Expert en information
S -> MC: cat = get(nom: String)
 note right of S: Expert en information
S -> CAT: ch = getChambreLibre(\ndateArrivé: String, \ndateDepart:String)
note right of S: Createur, cohésion et couplage
S -> R**: r=Create(\nch:Chambre, \nc:Commis, \ncl:Client, \ndateArrive:String, dateDepart: String)

@enduml
```



## Diagramme de classe

```plantuml
@startuml
class ControleurReservation{
  demarrerReservation()
  reserverChambre(dateArrive:string, dateDepart:string, categorie: String)
}
class "Map<nom:String,categorie:Categorie>" as MC {
  get(nom:String): Categorie
}

class Hotel <<Conteneur, Object physique>>
class Categorie <<Description d'entité>> {
  nom: String
  getChambreLibre(dateArrivé: String,dateDepart:String): Chambre
}
class Reservation <<Transaction>>{
  dateArrive: date
  dateDepart: date
  Reservation(ch:Chambre,c:Commis,cl:Client,dateArrive:String, dateDepart: String)
}
class Commis <<Role>>
class Chambre <<Objet physique, Contenu dans l'hotel, Produit d'une transaction>>
class Client <<Role>> {
  Client(?)
}

Hotel  *--> "*" Chambre: possède
Chambre "*" --o Categorie: appartient
Client  <--  Reservation: demande
Commis  <--  Reservation: cree
Hotel  *-- "*" Commis : Emploie
Reservation "*" --> "1" Chambre : est reservé par <
ControleurReservation --> MC
ControleurReservation --> Commis
MC --> "*" Categorie
@enduml
```


### CU01-Exercices-Notez une réservation
1. Représentez le fait qu’un Client est responsable d’une Réservation.
1. Représentez le fait qu’une Réservation peut avoir plusieurs Ligne de Réservation.
1. Représentez le fait qu’une Catégorie de chambre regroupe plusieurs Chambres.
1. Est-il nécessaire d’associer un Client à une Chambre? Justifiez la réponse.
1. Représentez le fait qu’un Client désire occuper une Chambre d’une catégorie précise 1. durant la première fin de semaine de mois de juillet. Justifiez les associations à 1. l’aide d’un verbe exprimant la raison d’être de l’association. Indiquez les 1. attributs des classes conceptuelles.
1. Représentez le fait qu’un Commis a confirmé la Réservation à l’Agenda à l’aide des 1. informations personnelles (nom et numéro de téléphone) du Client. Justifiez les 1. associations à l’aide d’un verbe d’action. Indiquez les attributs nécessaires.
1. Bâtissez le modèle du domaine partiel du système de l’hôtel. Justifiez les 1. associations à l’aide d’un verbe. Indiquez tous les attributs pertinents


### CU01-CU02-Exercices-RDCU

1. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une réservation. Annotez votre solution des principes GRASP.
 
2. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une ligne de réservation. Annotez votre solution des principes GRASP.
 
3. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’associer une ligne de réservation à une catégorie de chambre. Annotez votre solution des principes GRASP.
 
4. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de stocker une réservation dans l’agenda. Annotez votre solution des principes GRASP.
 
5. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de repérer une réservation à partir de son numéro de confirmation. Annotez votre solution des principes GRASP.
 
 6. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de créer un client tout en l’associant à une nouvelle réservation. Annotez votre solution des principes GRASP.
 
7. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de détruire une réservation appartenant à un client. Annotez votre solution des principes GRASP.
 
8. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’imprimer une facture incluant l’information sur une réservation, ses lignes de réservation et les catégories de chambres associées.  Annotez votre solution des principes GRASP.
