
#CU02 - Noter une réservation avec plusieurs chambres

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

## CU02 - Cas d'utilisation 
### CU02-Noter une réservation avec plusieurs chambres
**Pré(s) condition(s) :**
- Le commis est authentifié.
  
**Post condition(s) :**
- Une réservation est inscrite

**Acteur principal:**
- Le commis à la réception (commis).

**Scénario principal**
1. Un client appelle à l'hôtel pour placer une réservation.
1. Le commis démarre une nouvelle réservation.
1. Le commis entre:
   1. La date d'arrivée;
   2. La date de départ;
   3. Le nom de la catégorie de chambre;
   4. La quantité de chambres.
1. Le système inscrit les informations à la réservation.

Les étapes 3 et 4 sont répétées tant que le client n'indique pas qu'il a terminé.

5. Le commis termine la réservation.
1. Le système affiche toutes les informations entrées.
1. Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
1. Le système enregistre la réservation et affiche le numéro de confirmation.
1. Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**
*. En tout temps, le commis annule la réservation.
  1. Le système supprime la réservation.
  2. Fin du cas d'utilisation.

3a. Il n'y a pas assez de chambres de la catégorie choisie pour la période entrée.
  1. Le système affiche un message d'avertissement.
  1. Le système affiche les disponibilités de toutes les catégories pour la période entrée.
  1. Le commis communique les disponibilités au client.
  1. Retour à 3.


#### CU02-Réservation simple
Jean Hernandez appelle à l'hôtel pour réserver une chambre.
Le commis entrera:
Le 2011-06-01 comme date d'arrivée
Le 2011-06-02 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.

#### CU02-Réservation d'affaires
Jean Hernandez appelle à l'hôtel pour réserver deux chambres identiques, mais pour des périodes légèrement différentes. Son collègue, Patrice Retardataire, arrivera une journée après Jean.
Le commis entrera d'abord:
2011-08-02 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-08-03 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.

#### CU03-Réservation budgétaire
Jean Hernandez planifie des vacances avec son fils. Il appelle à l'hôtel pour réserver deux chambres de catégorie différente pour la même période.
Le commis entrera d'abord:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Standard" comme catégorie de cham¬
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.


## Interfaces usagé
```plantuml
@startuml
(*) --> "
{{
salt
{
**Menu Principal**
~~
[Noter une réservation]
}
}}
" as main

main -right-> "
{{
salt
{+
  **Noter une réservation**
  --
  Quantité de chambre | "99"
  Date d'arrivé | "2020-03-03"
  Date de départ | "2020-03-06"
  Catégorie | ^Categorie^ 
[Réserver] |
[Terminer la réservation]
== | ==
**Réservations**
~~ | ~~
  Quantité chambres: | 2
  Date d'arrivé : |  2020-03-03
  Date de départ : | 2020-03-06
  Catégorie: | Luxe
~~ | ~~
  Quantité chambres: | 2
  Date d'arrivé : |  2020-03-03
  Date de départ : | 2020-03-06
  Catégorie: | Luxe
  }
}}
" as reservations

reservations -right-> "
{{
salt
{+
**Menu Principal**
~~ | ~~
  No confirmation: | A1234
== | ==
[Noter une réservation]
  }
}}
" as mainReservationConfirme

@enduml
```

## Modèle du domaine

```plantuml
@startuml
class Hotel <<Conteneur, Object physique>>
class Categorie <<Description d'entité, Catalogue>> {
  nom: String
}
class Reservation <<Transaction>>{
noConfirmation: String
}
class LigneReservation <<Ligne de transaction>> {
  <s>quantity: String</s>
  dateArrive: Date                                                                                                
  dateDepart: Date
}
class Commis <<Role>>
class Chambre <<Objet physique, Contenu dans l'hotel, Produit d'une transaction>>
class Client <<Role>>

Hotel "1" -- "*" Chambre: possède
Chambre "*" -- "1" Categorie: appartient
Client "1" -- "1" Reservation: demande
Commis "1" -- "*" Reservation: cree
Reservation "1" -- "*" LigneReservation: contient
Hotel "1" -- "*" Commis : Emploie
LigneReservation "1" -- "*" Chambre : est reservé par <
@enduml
```

Cette version sous entends que les Catégories sont les même pour tous les Hotels.  Si ce   n’étais pas le cas, on associe Hotel à Catégorie et on enlève l’association entre Hotel et Chambre.

Catégorie peut être traité comme une classe de description ou un catalogue selon le sens par lequel nous utilisons les classes.  
Plusieurs chambres sont décrite par une catégorie (Classe de description)
Une Catégorie (Catalogue) contient plusieurs Chambre.




## Diagramme de séquence système

```plantuml
@startuml
title: Noter plusieurs réservations
skinparam style strictuml
Actor ":Commis" as Commis
Participant ":Systeme" as Systeme
Commis -> Systeme: demarrerReservation()
note right of Commis: Formulaire réservation\ndemander: {quantity,dateArrive,dateDepart, categorie}, retourne: [nomCategorie]] 
Commis <<-- Systeme: FormulaireReservation, historique réservations = []
loop [client n'a pas terminé]
  Commis -> Systeme: reserverChambres(quantity: integer, dateArrive:string, dateDepart:string, nomCategorie: String)
    Commis <<-- Systeme: formulaire réservation, historique réservations

end
 Commis -> Systeme: terminerReservation()
 Commis <<-- Systeme: Menu principale, noConfirmation
@enduml
```

## Contrat
**demarrerReservation()**
 - Précondition:
    - c:Commis est authentifier
  - 
  - Postcondition
    - Une instance r:Reservation a été créée
    - Une association a été cree entre c:Commis et r:Reservation
    - Une instance cl:Client a été créée (? Nom, Prénom, Courriel)
    - Une association entre r:Reservation et cl:Client a été créée

  **reserverChambres(quantity: integer, dateArrive:string, dateDepart:string, nomCategorie: String)**
  - Précondition:
    - c:Commis est authentifier
    - r:Reservation existe

  - Postcondition
    - Une instance lr:LigneReservation a été créé
    - Une association a été créée entre r:Reservation et lr:LigneReservation
    - <u>quantity</u> associations ont été créées entre lr:LigneReservation et Chambre sur la base de correspondance avec categorie.nom == <u>nomCategorie</u>
    - lr.dateArrivé est devenu <u>dateArrivé</u>
    - lr.dateDepart est devenu <u>dateDepart</u>

**terminerReservation()**
  - Précondition:
    - r:Reservation existe

  - Postcondition
    - r.noConfirmation est devenu un numéro unique

## RDCU

### demarrerReservation()
```plantuml
@startuml
skinparam style strictuml
Participant ":ControleurReservation" as S
Participant "r:Reservation" as R
Participant "c:Commis" as C
Participant "cl:Client" as CL
Participant "mc:Map<nom:String,categorie:Categorie>" as MC
Participant "llr:List<:LigneReservation>" as LLR

note right  of MC: Visible par le \ncontroleur puisque \ntout les hotels utilisent \nles mêmes catégories
note left of S:Controleur de session
note right of S: use mc.keys() to get array of category
 -> S: [nomCategorie] = demarrerReservation()
note right of S: Createur
 S -> CL**: cl = Create(?)
 note right of S: Créateur, cohésion et couplage
S -> R**: r=Create( \nc:Commis, \ncl:Client)
note right of R: Createur, r:Reservation possède les lr:LigneReservation
R --> LLR**: llr=Create()
@enduml
```

### reserverChambres
```plantuml
@startuml
skinparam style strictuml
Participant ":ControleurReservation" as S
Participant "mc:Map<nom:String,categorie:Categorie>" as MC
Participant "cat:Categorie" as CAT
Participant "r:Reservation" as R
Participant "lr:LigneReservation" as LR
Participant "llr:List<:LigneReservation>" as LLR

note right  of MC: Visible par le \ncontroleur puisque \ntout les hotels utilisent \nles mêmes catégories
note left of S:Controleur de session
 -> S: reserverChambres(\nquantity:integer\ndateArrive:String, \ndateDepart:String, \ncategorie: String)
 note right of S: Expert en information
S -> MC: cat = get(categorie: String)
 note right of S: Expert en information
S -> CAT: [ch] = getChambresLibre(\nquantity:integer\ndateArrivé: String, \ndateDepart:String)
note right of S: expert en information
S -> R: r=ajouterChambres(\n[ch]:Chambre, \ndateArrive:String, dateDepart: String)
note left of LR: Createur, forte cohesion, faible couplage
R -> LR**: r=create(\n[ch]:Chambre, \ndateArrive:String, dateDepart: String)
note left of LLR: expert en information\nr a une visibilité sur llr\nllr est une liste de ligne de réservation
R -> LLR: ajouterLigneReservarion(llr)

@enduml
```

### terminerReservation
```plantuml
@startuml
skinparam style strictuml
Participant ":ControleurReservation" as S
Participant "r:Reservation" as R

note left of S:Controleur de session
 -> S: noConfirmation = terminerReservation()
 note right of S: Expert en information\nMutateur d'attribut
S -> R: noConfirmation = terminerReservation()

@enduml
```


## Diagramme de classe

```plantuml
@startuml
class ControleurReservation{
  demarrerReservation()
  reserverChambres(quantity:Integer,dateArrive:String, dateDepart:String, categorie: String)
  terminerReservation()
}
class "Map<nom:String,categorie:Categorie>" as MC {
  get(nom:String): Categorie
}

class Hotel <<Conteneur, Object physique>>
class Categorie <<Description d'entité,**Catalogue**>> {
  nom: String
  getChambresLibre(quantity:Integer, dateArrivé: String,dateDepart:String): [Chambre]
}
class Reservation <<Transaction>>{
  noConfirmation: String
  Reservation(commis:Commis, client: Client)
  ajouterChambres([ch]:Chambre,dateArrive:String, dateDepart: String): String (json)
  terminerReservation(): String
}

class LigneReservation <<Ligne de transaction>>{
   dateArrive: Date
  dateDepart: Date
  create([ch]:Chambre,dateArrive:String, dateDepart: String)
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
Reservation "1" --> "*" LigneReservation: contient
LigneReservation "1" --> "*" Chambre : est reservé par <
ControleurReservation --> MC
ControleurReservation --> Commis
MC --> "*" Categorie
@enduml
```