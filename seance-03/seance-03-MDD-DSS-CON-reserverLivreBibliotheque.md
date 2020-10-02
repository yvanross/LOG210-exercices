# Réserver un livre à la bibliotheque
https://drive.google.com/file/d/1wclLv1Zt32XfMATWVzaEcqPBaql8ULXd/view

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


