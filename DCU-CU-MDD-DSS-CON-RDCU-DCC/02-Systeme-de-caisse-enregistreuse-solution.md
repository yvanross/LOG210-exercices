# Système de caisse enregistreuse

### Diagramme des cas d'utilisation

```plantuml
@startuml
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

# UC03 : Mise en plateau
Acteur principal : Caissier
- **Préconditions :**
La caisse est libre et son tiroir-caisse est vide (il n’y a pas de plateau dedans).
- **Garanties de succès (postconditions)**
Le caissier est authentifié. Le plateau du caissier est inséré dans le tiroir-caisse et son identificateur est enregistré. Le montant d’argent du plateau est enregistré. L’heure de l’arrivée du caissier est enregistrée.

#### Scénario principal (succès)
1. Le Caissier arrive à la caisse avec son plateau d’argent.
1. Le Caissier saisit son identifiant et son mot de passe.
1. Le Système authentifie le Caissier.
1. Le Système ouvre le tiroir-caisse et demande au Caissier de poser son plateau dans le  tiroir-caisse.
1. Le Caissier pose son plateau dans le tiroir-caisse.
1. Le Système reconnaît l’identificateur du plateau.
1. Le Système demande au Caissier de rentrer le montant d’argent du plateau.
1. Le Caissier rentre le montant d’argent du plateau.
1. Le Système demande au Caissier de fermer le tiroir-caisse.
1. Le Caissier ferme le tiroir-caisse.

Pose hypothèse qu'une caisse à seulement un tirroir caisse.

## Interface usagé

## MDD
```plantuml

@startuml
title MDD avec catégorie de classe
top to bottom direction

class Caissier <<Role>> {
  identifiant: integer
  motDePasse:string
}

class Caisse <<Equipement, objet physique>> {
  tirroirCaisseFermer:Bool
}
class Plateau <<Objet physique>> {
  identifiant: int
}

class MiseEnPlateau <<Transaction>> {
  dateArrive: Datetime
  dateDepart: Datetime
  montant: float
} 

Caissier -- "*" MiseEnPlateau : effectue
MiseEnPlateau -- Plateau: est fait dans un
MiseEnPlateau -- Caisse: est réalisé sur un 


@enduml
```

<!-- LOG210-04 seance-02-->
<!-- LOG210-03 seance-02 -->

## DSS
```plantuml
@startuml
title: Miser en plateau
skinparam style strictuml
Actor ":Caissier" as C
Participant ":Systeme" as S

C -> S: demarrerMiseEnPlateau()
C <-- S: formulaire [demande identifiant et mdp]

C -> S: authentifier(identifiant:string, mdp:string)
C <-- S: ouvrir tiroir caisse, demande de poser plateau

C -> S: poserPlateau(identifiant: string)
C <-- S: Formulaire demande montant

C -> S: crediterPlateau(montant:float)
C <-- S: demander de fermer le tiroir caisse

C -> S: fermerTiroirCaisse()
C <-- S: option menu principal ?


@enduml
```

## Contrat

 ## Operation: demarrerMiseEnPlateau()

- Précondition
  - 
- Postcondition

## Operation: authentifier(identifiant:string, mdp:string)
- Précondition
  - ca:Caisse existe (puique la transactions se fait sur cette caisse)
  
- Postcondition
  - c.tirroirCaisseOuvert est devenu true

## Operation: poserPlateau(identifiant:string)
- Précondition
  
- Postcondition
  - Une instance mp:MiseEnPlateau a été créée
  - mp.dateArrivé est devenu maintenant
  - Une associatation entre Caissier et mp:MiseEnPlateau a été créée sur la base de correspondance avec Caissier.identifiant == identifiant et Caissier.mdp == mdp
  - Une association entre ca:Caisse et mp:MiseEnPlateau a été créée
  - Une association entre Plateau et Mp:MiseEnPlateau à été créée sur la base de correspondance avec Plateau.identifiant == identifiant

## Operation: crediterPlateau(montant:string)
- Précondition
  - mp:MiseEnPlateau existe
- Postcondition
  - mp.montant est devenu montant

## Operation: fermerTiroirCaisse()
- Précondition
  - 
- Postcondition
  - c.tirroirCaisseOuvert est devenu false

## RDCU's

### RDCU - demarrerMiseEnPlateau
Question pour trouver le controleur de facade:
  - objet racine, équipement, systeme globale, sous-système
  - 
```plantuml
@startuml
skinparam style strictuml
Participant "c:Caisse" as C

note right of C: Controleur de facade de type équipement
 -> C: demarrerMiseEnPlateau()
 
 
@enduml
```
### RDCU authentifier
```plantuml
@startuml
skinparam style strictuml
Participant "c:Caisse" as C
Participant "MC:Map<identifiant:string, :Caissier>" as MC
Participant "ca:Caissier" as CA
 
-> C: authentifier(identifiant:string, mdp:string)

C -> MC: ca = get(identifiant:string)
C -> CA: caissier = authentifier(mpd:string)
opt "caissier != null"

note right of C: expert en information, mutateur d'attribut
C->C: OuvrirTirroirCaisse()
end


@enduml
```

### RDCU PoserPlateau
```plantuml
@startuml
skinparam style strictuml
Participant "c:Caisse" as C
Participant "mp:MiseEnPlateau" as MP
Participant "MPL:Map<identifiant:string, :Plateau>" as MPL
Participant "plateau:Plateau" as P


-> C: PoserPlateau(identifiant: string)
note right of C: Createur (PUCE), Caisse enregistre mp\nfaible couplage en passant les paramètres c et ca\nForte cohesion puisque mp est une transaction

 C-> MPL: plateau = get(identifiant:string)

 C --> MP**: create(c:Caisse, ca:Caissier,plateau:Plateau)
 MP -> MP: setDateArrive()

@enduml
```
### RDCU crediterPlateau
```plantuml
@startuml 
skinparam style strictuml
Participant "c:Caisse" as C
Participant "mp:MiseEnPlateau" as MP

-> C: crediterPlateau(montant:float)
note right of C: exper en information, mutateur d'attribut
C->MP: setMontant(montant:float)


@enduml
```
### RDCU fermerTirroirCaisse
```plantuml
@startuml
skinparam style strictuml
Participant "c:Caisse" as C


->C: fermerTirroirCaisse()
note right of C: expert en information, mutateur d'attribut
C->C: fermetureDuTiroirCaisse()

@enduml
```

## DCL/DCC
```plantuml
@startuml
title Mise en plateau
class Caisse <<Equipement>> {
  demarrerMiseEnPlateau()
  authetifier(identifiant: string, mdp:string)
  poserPlateau(identifiant:string)
  crediterPlateau(montant:float)
  fermerTiroirCaisse() 
  - fermetureDuTiroirCaisse() 
  - OuvrirTiroirCaisse()
}
class Plateau <<ObjectPhysique,Contenue de TirroirCaisse>> {
  identificateur: String
}
class Caissier <<Role>> {
identifiant: String
motDePasse:String
authentifier(identifiant:string, motDePasse:string): Caissier
}


class MiseEnPlateau<<Transaction>> {
    Montant: Double
    heureDebut: Datetime
    heureFin:DateTime
    - setDateArrive()
    setMontant(montant:float): void
    MiseEnPlateau(c:Caisse, ca:Caissier,p:Plateau): MiseEnPlateau
}

class "Map<identifiant:string, :Plateau>" as MPL {
  get(identifiant:string): Plateau
}
class "Map<identifiant:string, :Caissier>" as MC{
  get(identifiant: string): Caissir
}

MiseEnPlateau "*" -- "1" Plateau: utilise
MiseEnPlateau "*" -- "1" Caissier: est réalisé par
MiseEnPlateau "*" -- "1" Caisse: s'effectue sur 
Caisse --> MPL
Caisse --> MC
MPL -- "*" Plateau
MC -- "*" Caissier

@enduml
```

<!--LOG210-03 fait en classe-->