# Système de caisse enregistreuse

```plantuml
@startuml
title Diagramme des cas d'utilisation
left to right direction
package system {
 usecase "Traiter une vente" as V
 usecase "Traiter les retours" as R
 usecase "Mise en plateau" as MP
 usecase "Analyse activité" as A
 usecase "Gérer la sécurité" as S
 usecase "Gérer les usager" as U
}
Client --> V
Client --> R
Caissier --> V
Caissier --> R
Caissier --> MP
Gérant --> V
Gérant --> R
SystemVente --> A
AdministrateurSystem --> S
AdministrateurSystem --> U

V --> ServiceAutorisationPaiement
V --> CalculateurTaxe
V --> SystemeCompatabilité
MP --> SystemeRessourcesHumaines
@enduml
```

## Glossaire
**plateau (plateau d’argent)**
- « Support plat muni de rebords et de compartiments, qui se place à l'intérieur d'un tiroir-caisse et qui sert à garder séparément et à rendre facilement accessibles les différents billets de banque et pièces de monnaie. » [granddictionnaire.com]

**tiroir-caisse**
- Tiroir dans lequel se place le plateau d’argent confié à un caissier.

## CU03-Mise en plateau (Cash in)
**Acteur principal :** Caissier
****Préconditions :****
La caisse est libre et son tiroir-caisse est vide (il n’y a pas de plateau dedans).

**Garanties de succès (postconditions)**
Le caissier est authentifié. Le plateau du caissier est inséré dans le tiroir-caisse et son identificateur est enregistré. Le montant d’argent du plateau est enregistré. L’heure de l’arrivée du caissier est enregistrée.

**Scénario principal (succès)**
1. Le Caissier arrive à la caisse avec son plateau d’argent.
1. Le Caissier saisit son identifiant et son mot de passe.
1. Le Système authentifie le Caissier.
1. Le Système ouvre le tiroir-caisse et demande au Caissier de poser son plateau dans le tiroir-caisse.
1. Le Caissier pose son plateau dans le tiroir-caisse.
1. Le Système reconnaît l’identificateur du plateau.
1. Le Système demande au Caissier de rentrer le montant d’argent du plateau.
1. Le Caissier rentre le montant d’argent du plateau.
1. Le Système demande au Caissier de fermer le tiroir-caisse.
1. Le Caissier ferme le tiroir-caisse.


Pour voir comment un plateau-argent peut être enlevé d’un tiroir-caisse, regarder cette vidéo sur YouTube : https://goo.gl/9HdKNq

## MDD's

```plantuml
@startuml
title: Version initiale du MDD
skinparam style strictuml
hide empty members
hide methods

package P1 {
    class "GrandLivre" as GL
    class "Catalogue\nProduits" as CP
    class "Spécification\nProduit" as SP {
      descriptif
      prix
      codeArticle
    }

    class "Ligne\nArticles" as LA {
    quantité
    }
    class "Article" as A
    class "Magasin" as M {
      nom
      adressee
    }
  GL "1" - "1" M : Enregistre-pour >
}


package P2 {

class "Caisse" as C {
  identifiant
}
class "MisePlateau" as MP {
  montant
  date
  heure
}
class "Plateau\nArgent" as PA {
  identifiant
}
class "Caissier" as Ca {
  identifiant
  motDePasse
}

C "1" -- "0..1" MP : Catpurée-dans <
C "0..1" -- "1" PA : Est-dans <
C "1" -- "1" Ca : Travaille-à <
MP "1" -- "1" Ca : Effectue <
MP "1" -- "1" PA : Enregistre-mise-de <
Ca "0..1" -- "1" PA : Maintenu-par <

}

package P3 {
    class "PaiementCash" as PC {
      montant
    }
    
    class "Client" as Cl
    
    class "Vente" as V {
      date
      heure
    }
}

LA "*" -- "1" SP : Décrit-par >
LA "0..1" - "1..*" A : Enregistre-vente-de >
LA "1..*"- "1" V : Contenu-dans >
GL "1" -- "*" V : Enregistre >
GL "1" -- "*" MP : Enregistre >
CP "1" - "*" M : Utilisé-par >
CP "1" - "1..*" SP : Répertoirie >
SP "1" - "*" A : Décrit >
M "1" - "*" A : Stocke >
M "1" - "*" PA : Possède >
M "1" - "*" Ca : Emploie >
M "1" - "*" C : Contient >
V "1" -- "1" PC : Payé-par >
V "1" -- "1" Cl : Effectué-par >
V "0..1" - "1" C : Capturée-dans >

' layout tricks
P1 -[hidden]down- P3
'P2 -[hidden]left- P3
skinparam packageStyle rect
skinparam package {
  borderColor Transparent
  fontColor Transparent
}
note right of PA : Il y a un double lien\n entre la caisse et le plateauArgent.\n  Pouvez vous l'expliquer?
note right of Ca : Il y a un double lien entre Caisse et Caissier.\nPouvez vous l'expliquer?
note right of PA : Il y a un double lien entre Caissier et PlateauArgent
@enduml
```

### nettoyage du MDD pour enlever les liens/classes inutiles/redondants
```plantuml
@startuml
skinparam style strictuml
hide empty members
hide methods

class "Catalogue\nProduits" as CP <<Catalogue>> 
class "Spécification\nProduit" as SP <<Description d'entité>>{
  string descriptif
  float prix
  string codeArticle
}

class "Ligne\nArticles" as LA <<Ligne de transaction>> {
integer quantité
}
class "Article" as A <<Objet physique, produit d'une transaction>>
class "Magasin" as M <<Role d'une organisation>> #green {
  string nom
  string adressee
}

class "Caisse" as C <<Equipement, conteneur>> #green{
  identifiant
}
class "MisePlateau" as MP <<Transaction>> #green{
  float montant
  Date date
  Heure  heure
}
class "Plateau\nArgent" as PA << objet physique>> #green{
  string identifiant
}
class "Caissier" as Ca <<Role>> #green{
  string identifiant
  string motDePasse
}

class "PaiementCash" as PC <<Transaction>>{
  float montant 
}

class "Client" as Cl <<Role>>

class "Vente" as V <<Transaction>>{
  date
  heure
}

C "1" -down- "0..1" MP : Catpurée-dans <
MP "0..1" -up- "1" Ca : Effectue <
MP "0..1" -up- "1" PA : Enregistre-mise-de <

LA "0..1" -up- "1..*" A : Enregistre-vente-de >
LA "1..*" -- "1" V : Contenu-dans >
CP "1" -- "*" M : Utilisé-par >
CP "1" -- "1..*" SP : Répertoirie >
SP "1" -left- "*" A : Décrit >
M "1" -right- "*" A : Stocke >
M "1" -- "*" PA : Possède >
M "1" -- "*" Ca : Emploie >
M "1" -- "*" C : Contient >
V "1" -- "1" PC : Payé-par >
V "1" -- "1" Cl : Effectué-par >
V "*" -left- "1" MP : Capturée-dans >
@enduml
```

```plantuml
@startuml
skinparam style strictuml
title: DSS - CU03 - Mise en plateau
actor ":Caissier" as C
participant ":System" as S

C -> S: creerMiseEnPlateau()
C <<-- S: formulaire demande identifiant et mot de passe

C -> S: authentifier(string identifiant, string motDePasse)
C <<-- S: confirmation, ouverture du tirroir caisse

C -> S: poserPlateau(identifiant)
C <<-- S: confirmation, demande du montant

C -> S: saisirMontant(float montant)
C <<-- S: confirmation, demande de fermeture du tirroir caisse

C -> S: fermerTirroir()
C <<-- S: option pour caissier


@enduml
```


###  Contrat CU03-créerMisePlateau
**Opération :**	créerMisePlateau ()
**Références croisées :**	Cas d’utilisation : Cash In
**Préconditions :**
- Aucune
  
**Postconditions :**
- une instance mp de MisePlateau a été créée.

### Contrat CU03-authentifier
**Opération :**	authentifier (identifiant : String, mdp : String)
**Références croisées :**	Cas d’utilisation : Cash In
**Préconditions :**
- Il existe une mise plateau en cours.

**Postconditions :**
- mp a été associé à un Caissier, sur la base de correspondance avec identifiant.
- ca.ouvert est devenu vrai
- 
### Contrat CU03-poserPlateau
**Opération :**	poserPlateau (identifiant : String)
**Références croisées :**	Cas d’utilisation : Cash In
**Préconditions :**
- Il existe une mise plateau en cours.

**Postconditions :**
- mp a été associé à un PlateauArgent, sur la base de correspondance avec identifiant.

### Contrat CU03-saisirMontant
**Opération :**	saisirMontant(montant : Float)
**Références croisées :**	Cas d’utilisation : Cash In
**Préconditions :**
- Il existe une mise plateau en cours.
  
**Postconditions :**
- mp.montant est devenu montant.

### Contrat CU03-fermerTiroir
**Opération :**	fermerTiroir()
**Références croisées :**	Cas d’utilisation : Cash In
**Préconditions :**
- Il existe une mise plateau en cours.
  
**Postconditions :**
- mp.date est devenue la date actuelle.
- ca.ouvert est devenu faux
- mp.heure est devenue l’heure actuelle.


### RDCU CU03-créerMisePlateau

```plantuml
@startuml
skinparam style strictuml
participant ":Caisse" as C
participant "mp:MisePlateau" as mp
-> C : créerMisePlateau()
note right : Par contrôleur\n(Caisse est un\néquipement)
create mp
C --> mp : mp = create()
note over C, mp : Créateur (Caisse agrège MisePlateau)
note over C #FFEEEE
N.B. GrandLivre est aussi
un candidat pour créateur
puisqu'il stocke toutes les
MisePlateau.
Un avantage d'utiliser
GrandLivre est que Caisse 
aura une responsibilité de
moins. Les contrôleurs
prennent rapidement beau-
coup de responsabilités.
end note
@enduml
```

### RDCU CU03-authentifier-V1

```plantuml
@startuml
skinparam style strictuml
participant ":Caisse" as C
participant ":Magasin" as m
participant "c:Caissier" as c
participant "mp:MisePlateau" as mp
-> C : authentifier\n(identifiant : String,\nmdp : String)
note right : Par contrôleur\n(Caisse est un\néquipement)
C -> m : c = authentifierCaissier(identifiant,mdp)
note right : Expert (Magasin connaît\ntous les Caissiers)\net par Transformation\ndes identifiants\nen objets (p.F451/A460)
m -> ":Map<Caissier>" : c = rechercher(identifiant)
m -> c : valide = estValide(mdp)
note right : Expert (Caissier\nconnaît son mdp)
alt c!=null
C -> mp : setCaissier(c)
note over mp: Expert (mutateur d'attribut)
end
@enduml
```

### RDCU CU03-poserPlateau

```plantuml
@startuml
skinparam style strictuml
participant ":Caisse" as C 
participant ":Magasin" as m
participant ":Map<PlateauArgent>" as mapP
participant "mp:MisePlateau" as mp
-> C : poserPlateau\n(identifiant : String)
note right : Par contrôleur\n(Caisse est un\néquipement)
C -> m : p =\ngetPlateauArgent\n(identifiant)
note right : Expert (Magasin connaît\ntous les PlateauArgent)\net par Transformation\ndes identifiants\nen objets (p.F451/A460)
m -> mapP : p =\nrechercher(identifiant)
C -> mp : setPlateauArgent(p)
note over mp: Expert (mutateur d'attribut)
@enduml
```

### RDCU CU03-saisirMontant

```plantuml
@startuml
skinparam style strictuml
participant ":Caisse" as C
participant "mp:MisePlateau" as mp
-> C : saisirMontant\n(montant : Monnaie)
note right : Par contrôleur\n(Caisse est un\néquipement)
C -> mp : setMontant(montant)
note right : Expert (mutateur d'attribut)
@enduml
```


### RDCU CU03-fermerTiroir

```plantuml
@startuml
skinparam style strictuml
participant ":Caisse" as C
participant "mp:MisePlateau" as mp
-> C : fermerTiroir()
note right : Par contrôleur\n(Caisse est un\néquipement)
C -> mp : setDateHeure(now)
note right : Expert (mutateur d'attribut)
@enduml
```

### DCL à faire


# CU04 - Traiter une vente

```plantuml
@startuml
skinparam Style strictuml

participant ":Caisse" as Caisse
participant "attenteVente:AttenteVente" as AttenteVente
participant "attenteVente2:AttenteVente" as AttenteVente2
participant "creationVente:CreationVente" as CreationVente
participant "attentePaiement:AttentePaiement" as AttentePaiement
participant "{abstract}\n:EtatVente" as EtatVente

-> Caisse: creerNouvelleVente()
note right of Vente: Etat initiale AttenteVente
Caisse -> Caisse : IEtatVente attenteVente = getState()
activate Caisse
opt etat == null 
Caisse -> AttenteVente**: IEtatVente attenteVente = create()
end 
deactivate Caisse

Caisse -> AttenteVente: IEtatVente etat = creerNouvelleVente()
AttenteVente -> CreationVente**: IEtatVente creationVente = create()
Caisse -> Caisse: setState(creationVente)

-> Caisse: saisirArtiche(codeArticle, quantite)
Caisse -> Caisse : IEtatPaiement attentePaiement = getState()
Caisse -> CreationVente: IEtatVente nouvelEtat = saisirArtiche(codeArticle, quantite)
Caisse -> Caisse : setState(nouvelEtat)

-> Caisse: terminerVente()
Caisse -> Vente : getState()
Vente -> CreationVente: terminerVente()
AttenteVente -> AttentePaiement**: IEtatVente attentePaiement = create()
Vente -> Vente: setState(attentePaiement)

-> Vente: creerPaiement(montant)
Vente -> Vente: getState()
Vente -> AttentePaiement: IEtatVente attenteVente = creerPaiement(montant)
AttentePaiement -> AttenteVente2**: IEtatVente attenteVente2 = create()
Vente -> Vente: setState(attenteVente2)

note right of Vente: Appel d'une opération dans le mauvais état -> génération d'une exception
-> Vente: creerPaiement(montant)
Vente -> Vente: attenteVente = getState()
Vente -> AttenteVente2: IEtatVente attenteVente2 = creerPaiement(montant)
AttenteVente -> EtatVente: IEtatVente attenteVente2 = creerPaiement(montant)
EtatVente -> Exception**: create("Erreur operation invalide")


@enduml
```