# Réserver un livre à la bibliotheque
https://drive.google.com/file/d/1wclLv1Zt32XfMATWVzaEcqPBaql8ULXd/view
# Diagramme de cas d'utlisation
```plantuml
@startuml

package SystèmeBibliotheque{
(CU01-Reserver un livre) as (CU01)  
}
Membre->(CU01)
@enduml
```
# Cas d’utilisation - Réserver un livre de la bibliothèque
**Parties prenantes et intérêts :** 
 - Le **Membre**. Il veut un moyen de recherche exact et rapide et ne veut pas que la Bibliothèque mémorise des informations sur ses recherches (confidentialité). Il veut pouvoir réaliser des réservations aisément, obtenir un service rapide en fournissant un minimum d’efforts. Il veut également une preuve de réservation.
 - La **Bibliotheque**. Elle veut enregistrer correctement les réservations et satisfaire les souhaits des membres. 

**Préconditions :** Le Membre est identifié et authentifié

**Acteur principal :** Membre
1. Le membre choisit la fonction « recherche » et saisit du texte décrivant le livre 1. (par exemple, une partie du titre, « UML »).
1. Le système affiche une liste de livres (le titre, l’auteur et l’année) 1. correspondant à la recherche, par exemple, « UML2 et les design patterns, Craig 1. Larman, 2005 » et « UML par la pratique, Pascal Rocques, 2009 ».
1. Le membre choisit un livre parmi les résultats, par exemple, « UML2 et les design 1. patterns, Craig Larman, 2005 ».
1. Le système affiche les informations détaillées du livre (le titre, l’auteur, le 1. numéro ISBN, la maison d’édition, le numéro de l’édition et l’année) ainsi que la 1. liste de tous les exemplaires du livre indiquant s’ils sont disponibles ou pas, 1. par exemple, deux exemplaires du livre « UML2 et les design patterns », un avec 1. l’identificateur d’exemplaire « 1 » qui est disponible et un avec 1. l’identificateur d’exemplaire « 2 » qui n’est pas disponible.
1. Le membre réserve un exemplaire du livre qui est disponible.
1. Le système confirme la réservation en affichant un numéro de réservation avec le 1. nom du membre et le code de l’exemplaire du livre.

**Extensions (scénarios alternatifs) :**
2. Aucun livre ne correspond au texte de la recherche. 
- Le système affiche un message indiquant qu’aucun livre n’a été trouvé.
- Le membre lance une nouvelle recherche.
4. Tous les exemplaires ne sont pas disponibles. 
- Le système affiche toutes les informations du livre et des exemplaires, mais un message indique qu’il n’est pas possible de réserver, faute d’exemplaires disponibles.
- Le membre lance une nouvelle recherche.


# MDD
```plantuml
@startuml
class M as "Membre" <<Role>>{
  nom: string
}

class B as "Bibliotheque" <<Conteneur>>
class L as "Livre" << Description d'entité>>   {
  titre: String
  <s>auteur: String</s>
  isbn: String
  <s>maisonEdition: String</s>
  noEdition: String
  annee: integer
} 
class ME as "MaisonEdition" <<Description d'entité>>
class A as "Auteur" <<Role>>
class EL as "ExemplaireLivre" <<Objet physique, contenue de Bibiliotheque, Produit ou service lié a un transaction>>{
  code: string
}
class R  as "Reservation" <<Transaction>> {
  noReservation:String
}

B --"*" L: permet la recherche
M --"*" R: fait
R -- EL: est pour
EL "*" -- L: sont décrit 
L -- A: est écrit par 
L -- ME: est éditer par une
B -- "*" M: offre des service à 
@enduml
```

# DSS
```plantuml
@startuml
title: Réserver un livre à la bibliothèque
skinparam style strictuml
Actor ":Membre" as M
participant ":System" as S
M -> S: demarrerRechercheLivre()
M <<-- S: formulaire de recherche

M -> S: rechercherLivre(texte:string)
M <<-- S: [livre]

M -> S: selectionnerLivre(livre:string)
note left of S: livre => titre auteur, isbn, maison edition, no édition, année
M <<-- S: livre,[exemplaire]

M -> S: reserverExemplaire(livre:string, code:string)
M <<-- S: noReservation, nom du membre, code de l'exemplaire


@enduml
```

# Contrats

## operation: demarrerRechercheLivre()
**- Prédondition**
**- Postcondition**
  - Aucune


## operation: rechercherLivre(livre:string)
**- Prédondition**
**- Postcondition**
 - Aucune


## operation: selectionnerLivre(livre:string)
**- Prédondition**
**- Postcondition**
 - Aucune


## operation: reserverExemplaire(livre:string, code:string)
**- Prédondition**
  - m:Membre est authentifier


**- Postcondition**
  - Une instance de r:Reservation a été créée
  - Une association a été créée entre m:Membre et r:Reservation
  - Une association a été créée entre r:Reservation et Exemplaire sur la base de correspondance avec Exemplaire.code
  - r.noConfirmation est devenu un no unique (spécifier le format dans le glossaire)



## RDCU demarrerRechercheLivre
```plantuml
@startuml
skinparam style strictuml
participant ":ControleurReservation" as S
note left of S: Controlleur de session

 -> S: demarrerRechercheLivre() 

@enduml
```

## RDCU rechercherLivre
```plantuml
@startuml
title: rechercherLivre
skinparam style strictuml
participant ":ControleurReservation" as S
note left of S: Controlleur de session
participant ":Bibliotheque" as B
participant "ll:List<:Livre>" as LL

 -> S: [livre] = rechercherLivre(texte:string)
note left of B: Expert en information,\ncontroleur possède la Bibliotheque,\nBibliotheque possède la liste de livre
S -> B: [livre] =rechercherLivre(texte:string)
note left of LL: List<:Livre> est l'expert pour trouver les livres en sachant un texte
B -> LL: [livre] = find(texte:string)

@enduml
```


# RDCU selectionnerLivre
```plantuml
@startuml
skinparam style strictuml
participant ":ControleurReservation" as S
note left of S: Controlleur de session
participant ":Bibliotheque" as B
participant "ml:Map<nom, :Livre>" as ML
participant "l:Livre" as L

 -> S: selectionnerLivre(livre:string)
 note left of B: Expert en information \nControleur -> Bibliotheque\nBibliotheque -> map de livre
 S->B: [l,[exemplaire]] = selectionnerLivre(livre:string)
 note left of ML: Expert en information
 B->ML: l = get(nom:string)

 note left of L: Expert Livre décrit plusieurs exemplaire
 B->L: [exemplaire] = getExemplaires()
@enduml
```


# RDCU
```plantuml
@startuml
title: Réserver un livre à la bibliothèque
skinparam style strictuml
participant ":ControleurReservation" as S
note left of S: Controlleur de session
participant ":Reservation" as Reservation
participant ":Bibliotheque" as B
participant "ml:Map<nom, :Livre>" as ML
participant "l:Livre" as L
participant "me:Map<code:string, :Exemplaire>" as ME

 -> S**: reserverExemplaire(livre:string, code:string)
note right of S: Createur par default, \nfaible couplage avec parametre m:Membre
S->B: exemplaire =  getExemplaire(livre:string, code:string)
B -> ML: l = get(livre:string)
note left of L: expert en information\nl possède une map d'exemmplaires
B -> L: exemplaire = getExemplaire(code:string) 
note left of L: expert en information 
L -> ME: exemplaire = get(code)

note left of Reservation: createur par default, PUCE n'est pas application
note left of Reservation: r.noConfirmation est devenu no unique
S -> Reservation**: create(m:Membre, exemplaire:Exemplaire)
Reservation ->Reservation: initNoConfirmation()

@enduml
```

# DCC - DCL
```plantuml
@startuml
class C as "ControleurReservation"{
  demarrerRechercheLivre() 
 rechercherLivre(texte:string): list<Livre:json>
 selectionnerLivre(livre:string): string
 reserverExemplaire(code:string)
}
class M as "Membre" <<Role>>{
  nom: string
}

class B as "Bibliotheque" <<Conteneur>>{
  rechercherLivre(texte:string): [:Livre]
  selectionnerLivre(livre:string): [:Livre,[:Exemplaire]]
  getExemplaire(code:string): Exemplaire
}

class L as "Livre" << Description d'entité>>   {
  titre: String
  <s>auteur: String</s>
  isbn: String
  <s>maisonEdition: String</s>
  noEdition: String
  annee: integer
  [Exemplaire] = getExemplaires()
  exemplaire = getExemplaire(code:string) 
} 
class ME as "MaisonEdition" <<Description d'entité>>
class A as "Auteur" <<Role>>
class EL as "ExemplaireLivre" <<Objet physique, contenue de Bibiliotheque, Produit ou service lié a un transaction>>{
  code: string
}
class R  as "Reservation" <<Transaction>> {
  noReservation:String
  create(m:Membre, exemplaire:Exemplaire)
}

class LL as  "List<:Livre>" {
  find(texte:string): List<Livre>
}
class ML as "Map<nom, :Livre>" {
  get(nom:String): Livre
}
class MX as  "Map<code:string, :Exemplaire>" {
  get(code:string): Exemplaire
}


C --> LL
LL -->"*" L
C-->ML
ML --> "*" L
L --> MX
MX --> "*" EL
C --> B


B -->"*" L: permet la recherche
M <--"*" R: est fait pour <
R --> EL:  reserve 
L "*"<-- A: sont écrit par <
L "*" <-- ME: edite <
B -- "*" M: offre des service à 
@enduml
```