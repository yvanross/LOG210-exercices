## Étude de cas 
### Système d'échange de livres universitaires
Le Bureau du Développement Durable (BDD) de l'Université a mis en place un système d'échange de livres aux fins de développement durable et pour réduire les coûts pour les étudiants (les clients du système). La version initiale est rudimentaire et ne permet que deux fonctionnalités :

### CU01 - Ajouter un livre à échanger

Acteur principal : Client (étudiant)

**Préconditions :**

Le Client est identifié (par son nom d'utilisateur) et authentifié par son mot de passe.

**Scénario principal (succès)**
1.	Le Client démarre un nouvel ajout de livre. 
2.	Le Client entre le code ISBN du livre, ainsi que le code de sa condition. 
3.	Le Système enregistre le livre et présente sa description (titre, nombre de pages, auteurs, maison d'édition, no d'édition ). 

Le Client répète les étapes 2 à 3 jusqu'à ce qu'il ait saisi tous les livres à échanger. 

4.	Le Système présente la liste de livres que possède le Client. 

**Cas alternatifs**

3a. Le système affiche un message d'erreur puisque le livre n'existe pas.

```plantuml
@startuml
title MDD CU01 - Ajouter un livre à échanger

class BDD <<Organisation>>{

}
class C as "Client" <<Role>> {
  string nomUtilisateur
  string motDePasse

}
class L as "Livre" <<Objet physique>>{
  condition condition

}
class DL as "DescriptionLivre" <<Description d'entité>>{
  string isbn
  string titre
  int nombrePages
  int noEdition
}

class A as "Auteur" {
  string nom
}

class ME as "MaisonEdition" {
  string nom

}
BDD "1" -- "*" DL: gère >
BDD "1" -- "*" C: offe un service au membre >
C "1" -- "*" L: possède >
L "*" -- "1" DL: sont décrit >
A "1" -up- "*" DL: écrit des livres décrit par >
ME "1" -up- "*" DL: édite les libres décrit par >
@enduml
```

```plantuml
@startuml
skinparam style strictuml
title DSS CU01 - Ajouter un livre à échanger

Actor ":Etudiant" as E
participant ":System" as S

E -> S: demarrerAjoutLivre()
E <<-- S: formulaire pour entrer le code ISBN et la condition du livre

loop tant que le client n'a pas entré tous ses livres à échanger
E -> S: ajouterLivre(isbn:string, codeCondition:string)
E <<-- S: description livre, formulaire précédent
end

E -> S: terminerAjoutLivre()
E <<-- S: [livre du client]

@enduml
```

#### Contrats CU01-demarrerAjoutLivre

**Opération:** demarrerAjoutLivre()
**Préconditions:**
**PostConditions:**
- Aucune


#### contrat CU01-ajouterLivre 
**Opération:** ajouterLivre(tring isbn, string codeCondition)()
**Préconditions:**
- c:Client existe puisque le client doit être authentifié pour avoir accès à cette fonctionnalité

**PostConditions:**
- Une instance l:Livre a été créée
- Une association a été créé entre l:Livre et c:Client (précondition)
- Une association a été crée entre l:Livre et la classe DescriptionLivre sur la base de correspondance entre DescriptionLivre.isbn == isbs (paramètre)
- l.codeCondition est devenu codeCondition (paramètre)


#### Contrat CU01-terminerAjoutLivre
**Opération:** terminerAjoutLivre()
**Préconditions:**
***PostConditions:**
- Aucune


# RDCU's

## RDCU - demarrerAjoutLivre
```plantuml
@startuml
skinparam style strictuml
participant "ctrl:Bdd" as S
note left of S: controleur de façade de type objet racine

 -> S: demarrerAjoutLivre()
activate S
deactivate S
@enduml
```

## RDCU CU01 -  ajouterLivre()
```plantuml
@startuml
skinparam style strictuml
participant "ctrl:Bdd" as S
note left of S: controleur de façade de type objet racine

participant "c:Client" as C
note left of C: est visible par le controleur puisque c'est une précondition

participant "l:Livre" as L

participant "ll:List<Livre>" as LL
note left of LL: est visible par le client\npuisqu'il possède une liste de livre

 -> S: ajouterLivre(isbn:string, codeCondition:string)
activate S

note right of S: postcondition: Une association a été crée entre l:Livre et la classe DescriptionLivre\nsur la base de correspondance entre DescriptionLivre.isbn == isbs (paramètre)\nAjoute d'une association entre le BDD et DescriptionLivre

participant "mdl:Map<isbn,DescriptionLibre>" as MDL
note left of MDL: bdd gère les DescriptionLivre
note right of S: Expert en information\nbdd a une visibilité sur mdl
S -> MDL: descriptionLivre = get(string isbn)

note right of S: postcondition: Une instance l:Livre a été créée\npostcondition: l.codeCondition est devenu codeCondition (paramètre)\n\npatron créateur par défaut\npuisque PUCE ne donne aucune option valable

note right of S: Expert en information\nctrl possède les paramètre\ctrl a un visibilité sur Client\nClient possède la liste de livre
S -> C: ajouterLivre(descriptionLivre:DescriptionLivre, codeCondition:string)

note right of C: Patron createur\nClient possède les livres
C --> L**: create(descriptionLivre:DescriptionLivre, string codeCondition)

note right of C: postcondition: Une association a été créé entre l:Livre et c:Client (précondition)
note right of C: Patron expert\nClient a une visibilité sur la ll\nll est une liste de livre
C -> LL: add(l:livrre)

deactivate S
@enduml
```

## RDCU CU01 -  terminerAjoutLivre()
```plantuml
@startuml
skinparam style strictuml

participant "ctrl:Bdd" as S
note left of S: controleur de façade de type objet racine

participant "c:Client" as C
note left of C: est visible par le controleur puisque c'est une précondition


 -> S: terminerAjoutLivre()
 activate S
 note right of S: Expert en information\BDD a une visibilité sur e\ne possède ll
S->C: ll =  getLivres()



 deactivate S

@enduml
```

#### CU02 - Proposer un échange de livres 
Acteur principal : Client (étudiant)

****Préconditions :****
Le Client est identifié (par son nom d'utilisateur) et authentifié par son mot de passe.

Scénario principal (succès) 

1.	Le Client démarre une nouvelle proposition d'échange de livres. 
2.	Le Système présente une liste d'autres Clients dans le système ainsi que le(s) livre(s) qu'ils ont à échanger. 
3.	Le Client sélectionne un autre Client (le Client Proposé) à qui il veut proposer un échange. 
4.	Le Système présente la liste de livres que possède le Client Proposé et une liste de livres que possède le Client. 
5.	Le Client ajoute à la proposition d'échange un livre. Si c'est un de ses livres, alors c'est à offrir dans la proposition. Sinon c'est un livre du Client Proposé et c'est à recevoir dans la proposition. Le Client répète l'étape 5. jusqu'à ce qu'il soit satisfait de la proposition. 
6.	Le Système présente le nombre total de livres à offrir et à recevoir et demande au Client de confirmer la proposition. 
7.	Le Client confirme et le Système enregistre sa proposition d'échange avec la date et l'heure. 
8.	Le Système envoie un courriel au Client Proposé pour l'informer de la proposition d'échange. 


```plantuml
@startuml
title: MDD CU01 et CU02
skinparam style strictuml
hide empty members
hide empty methods
class Client {
 nomUtilisateur : String
 MotDePasse : String
 courriel : AdresseCourriel
}
class Livre {
 idLivre : integer
 condition : CodeCondition
}
class DescriptionLivre {
    string isbn
  string titre
  int nombrePages
  int noEdition
}


class A as "Auteur" {
  string nom
}

class ME as "MaisonEdition" {
  string nom

}
class "Bureau\nDéveloppement\nDurable" as BDD
Client "1" -- "*" Livre : veut-échanger >
BDD "1" -- "*" DescriptionLivre : permet-\nd'échanger >
BDD "1" -- "*" Client : fournit-\nservice-à >
Livre "*" -- "1" DescriptionLivre : est-décrit-par >
class "PropositionÉchange" as PE <<Transaction>>{
  dateHeure : DateHeure
}
PE "1" -- "1..*" Livre : offre >
PE "1" -- "1..*" Livre : reçoit >
PE "1" -- "1" Client : est-proposée-par >
PE "1" -- "1" Client : est-proposée-à >

A "1" -up- "*" DescriptionLivre: écrit des livres décrit par 
ME "1" -up- "*" DescriptionLivre: édite les libres décrit par 

legend left
CodeLivre, CodeCondition, DateHeure, AdresseCourriel, etc. sont les types de données.
end legend
@enduml

```


```plantuml
@startuml
skinparam style strictuml
title CU02 - Proposer un échange de livres
actor ":Client" as c
participant ":Système" as s
c->s : démarrerPropositionÉchange()
s-->c : étudiants et livres à échanger

c-> s: choisirClient(nomUtilisateur : String)
s-->c : liste de livres de l'étudiant choisi et du client

loop reste des livres à proposer
  opt Client veut recevoir un livre
    c->s: proposerLivreRecevoir(idLivre : integer)
  end opt
  opt Client veut offrir un livre
    c->s: proposerLivreOffrir(idLivre : integer)
  end opt
end loop

c->s: terminerProposition()
s-->c: nombre livres a offrir et a recevoir

c->s: confirmerÉchange()
s-->c: resumé de l'échange
@enduml
```


#### CU02-Contrat-demarrerPropositionÉchange

**Opération :** demarrerPropositionÉchange()

**Préconditions :**
Une instance c de Client existe
Une instance bdd de BureauDeveloppementDurable existe


**Postconditions :**
Une instance p de PropositionEchange a été créée
Une association **"est-proposé-par"** a été créée entre l’instance p :PropositionEchange et c :Client

#### CU02-Contrat-choisirClient 

**Opération :** choisirClient(nomUtilisateur : string)

**Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Une assocation **"est-proposé-a"** entre p :PropositionEchange et client a été créée sur la base de correspondance avec le parametre idEtudiant
 
#### CU02-Contrat-proposerLivreRecevoir

**Opération :** proposerLivreRecevoir(idLivre :CodeLivre)

 **Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Une association **"recoit"** a été créée entre p :PropositionEchange et Livre sur la base de correspondance avec le paramètre idLivre


#### CU02-Contrat-proposerLivreOffrir

**Opération :** proposerLivreOffrir(idLivre :CodeLivre)

 **Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Une association **"offre"** a été créée entre p :PropositionEchange et Livre sur la base de correspondance avec le paramètre idLivre

#### CU02-Contrat-terminerProposition 

**Opération :** terminerProposition()

**Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
p.dateHeure est devenu maintenant
 
#### CU02-Contrat-confirmerEchange 

**Opération :** confirmerEchange()
**Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Aucune

## RDCU-CU02-démarrerPropositionÉchange()
```plantuml
@startuml

skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "proposeur:Client" as CP
note left of CP: controleur le voit puisque c'est une précondition
participant "pe:PropositionEchange" as PE
participant "llo:List<Livre>" as LLO
participant "llr:List<Livre>" as LLR
participant "lpe:List<PropositionEchange>" as LPE
note left of LPE: Client a une liste de proposition d'échange
participant "client[i]:Client" as LC


->CTRL : démarrerPropositionÉchange()
activate CTRL
  
  note right of CTRL: patron expert en information\nbdd voit proposeur\nproposteur possède une liste de porposition
  CTRL -> CP: createPropositionEchange()

  note right of CP: Patron Createur\n bdd enregistre pe
  CP -> PE**: create()

  note right of PE: liste de livre a recevoir\nPatron createur\npe contient la liste de livre
  PE->LLR**: create()

  note right of PE: liste de livre a offrir\nPatron createur\npe contient la liste de livre
  PE->LLO**: create()
  
note right of CP: Patron expert en information\nClient possède une nouvelle propositionEchange\nClient possède une liste de propositionEchange\nPostCondition: une association a été créée entre Client et propositionEchange
  CP -> LPE: add(pe)
    note right of CTRL: traitement du retour d'information\nBdd possède une liste de client sur lequel il veut itérer
  loop i < nbClient
    note right of CTRL: Expert en information\nbdd connait les clients\nChaque client connait sa liste de livre
    CTRL ->  LC: [Livre] = getLivres()
  end
  <<--CTRL : étudiants et livres à échanger
deactivate CTRL
@enduml
```

## RDCU-CU02-choisirClient()
```plantuml
@startuml

skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "mc:Map<nomUtilisateur,Client>" as MC
note left of MC: BDD a une visibilité sur plusieurs clients
participant "proposeur:Client" as CP
note left of CP: controleur le voit puisque c'est une précondition
participant "pe:PropositionEchange" as PE

participant "clientProposeA:Client" as CPA

note right of CTRL: Meme controleur que l'opération précédente puisque l'opération fait partie du même DSS
-> CTRL: choisirClient(nomUtilisateur : String)
  activate CTRL
  note right of CTRL: Expert en information\nbdd possède mc
  CTRL->MC: clientProposeA = get(nomUtilisateur:string)
  
  note right of CTRL: Expert en information\nBDD connait le client proposeur\nProposeur connait la propositionEchange
  CTRL->CP:   offrirAClient(clientProposeA:Client)

  note right of CTRL: Expert en information\nClient proposeur connait la propositionEchange\npe est une transaction qui identifie le client auxquel on veut offrir des livres
  CP->PE:   offrirAClient(clientProposeA:Client)
  
  note right of CTRL: Expert en information!\nbdd connais proposeur\nproposeur possède des livres
  CTRL->CP: [LivreAProposer] = getLivres()
  
  note left of CP: Expert en information!\nbdd connais clientProposerA\nclientProposerA possède des livres
  
  CTRL -> CPA: [livreARecevoir] = getLivres()
  <<--CTRL: : liste de livres de l'étudiant choisi et du client
deactivate CTRL
@enduml
```

## RDCU-CU02-proposerLivreRecevoir
```plantuml
@startuml
skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "proposeur:Client" as CP
note left of CP: controleur le voit puisque c'est une précondition
participant "pe:PropositionEchange" as PE
participant "clientProposeA:Client" as CPA
participant  "mlc:Map<isbn,Livre>" as MLC
participant "llr:List<Livre>" as LLR

->CTRL: proposerLivreRecevoir(isbn : string)
activate CTRL
note right of CTRL: Expert en information\nbdd connait le client proposeur\nLe client proposeur connait la proposition d'échange
CTRL -> CP :ajouterLivreARecevoir(idLivre:string)

note right of CP: Expert en information\nproposeur a une visibilité sur pe\npe connait le clientProposéA\nclientProposeA connait ses livres 
CP -> PE: ajouterLivreARecevoir(idLivre:string)

note right of PE: Expert en information\npe connait le clientProposéA\nclientProposeA connait ses livres
PE->CPA: livre = ajouterLivreARecevoir(idLivre:string)

note right of CPA: Expert en information\nclientProposeA possède des livres
CPA -> MLC: livre = get(idLivre:string)

note right of PE: Expert en information\n pe possède la liste llr
PE -> LLR: add(Livre livre)
deactivate CTRL
@enduml
```

## RDCU-CU02-proposerLivreOffrir
```plantuml
@startuml
skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "proposeur:Client" as CP
note left of CP: controleur le voit puisque c'est une précondition
participant  "mlc:Map<isbn,Livre>" as MLC
participant "pe:PropositionEchange" as PE
participant "llo:List<Livre>" as LLO
->CTRL: proposerLivreOffrir(isbn : CodeLivre)
activate CTRL

note right of CTRL: Expert en information\nbdd connait client proposeur\nclient proposeur connait la proposition d'échange
CTRL -> CP:ajouterLivreAOffrir(idLivre:string)

note right of CP: Expert en information\nClient possède une map de livre
CP -> MLC: livre=get(idLivre)

note right of CP: Expert en information\nclient proposeur connait la proposition d'échange\npe possède une liste de livre a offrir llo
CP -> PE:ajouterLivreAOffrir(Livre livre)

note right of PE: Expert en information\n pe possède la liste llo
PE -> LLO: add(Livre livre)
deactivate CTRL
@enduml
```

## RDCU-CU02-terminerProposition()
```plantuml
@startuml
skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "proposeur:Client" as CP
note left of CP: controleur le voit puisque c'est une précondition
participant "pe:PropositionEchange" as PE
participant "llo:List<Livre>" as LLO
participant "llr:List<Livre>" as LLR

->CTRL: terminerProposition()
activate CTRL

note right of CTRL: Expert en information\nbdd connait le client proposeur\nClient proposeur connait la proposition d'échange
CTRL -> CP: [nbLivreAOffrir, nbLivreARecevoir] = terminerProposition()

note right of CP: Expert en information\nClient proposeur connait la proposition d'échange\npe possède les listes de livres
CP->PE:[nbLivreAOffrir, nbLivreARecevoir] = terminerProposition()

note right of PE: Expert en information, pe possède la liste de livre
PE->LLR: nbLivreARecevoir = getSize()

note right of PE: Expert en information, pe possède la liste de livre
PE->LLO: nbLivreAOffrir = getSize()

note right of PE: Expert en information, mutateur d'attribut
PE -> PE: setDateTime()

<<--CTRL: nombre livres a offrir et a recevoir
deactivate CTRL
@enduml
```

## RDCU-CU02-terminerProposition()
```plantuml
@startuml

skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
->CTRL: confirmerÉchange()
activate CTRL
<<--CTRL: resumé de l'échange
deactivate CTRL

@enduml
```


# Diagramme de classe logiciel CU01 et CU02

```plantuml
@startuml
skinparam style strictuml
class "Client" as C {
  nomUtilisateur : String
  MotDePasse : String
  courriel : AdresseCourriel
  PropositionEchange = createPropositionEchange()
  offrirAClient(clientProposeA:Client)
  [LivreAProposer] = getLivres()
  ajouterLivreARecevoir(idLivre:string) 
  ajouterLivreAOffrir(idLivre:string)
  [nbLivreAOffrir, nbLivreARecevoir] = terminerProposition()
  ajouterLivre(descriptionLivre:DescriptionLivre, codeCondition:string)
}
class "Livre" as L {
 idLivre : integer
 condition : CodeCondition
 Livre(descriptionLivre:DescriptionLivre, string codeCondition)
}

class "DescriptionLivre" as DL {
  string isbn
  string titre
  int nombrePages
  int noEdition
}

class "PropositionÉchange" as PE <<Transaction>>{
  dateHeure : DateHeure
  PropositionEchanbge()
  offrirAClient(clientProposeA:Client)
  ajouterLivreARecevoir(idLivre:string)
  ajouterLivreAOffrir(idLivre:string)
  nbLivreAOffrir, nbLivreARecevoir] = terminerProposition()
  - setDateTime()

}


class "Auteur" as A {
  string nom
}

class ME as "MaisonEdition" {
  string nom

}
class "Bureau\nDéveloppement\nDurable" as BDD{
  string démarrerPropositionÉchange()
  string choisirClient(string nomUtilisateur )
  string proposerLivreRecevoir(string idLivre)
  string proposerLivreRecevoir(string idLivre)
  string terminerProposition()
  string confirmerÉchange()
}

class "mc:Map<nomUtilisateur,Client>" as MC{
  Client get(string nomClient)
}
class "lpe:List<PropositionEchange>" as LPE{
  add(PropositionEchange propositionEchange)
}
class "llo:List<Livre>" as LLO{
  add(Livre livre)
  integer getSize()
}
class "llr:List<Livre>" as LLR{
  add(Livre livre)
  integer getSize()
}


class "mlc:Map<isbn,Livre>" as MLC{
  add(Livre livre)
  Livre get(string)
}

class "mc:Map<string,DescriptionLivre>" as MDL{
  DescriptionLivre get(string isbn)
}

BDD "1" --> "1" MC
MC "1" --> "*" C
C "1" --> "1" LPE 
LPE "1" --> "*" PE
PE "1" --> "1" C 
PE "1" --> "1" LLO
LLO "1" --> "*" L
PE "1" --> "1" LLR
LLR "1" --> "*" L


BDD "1" --> "1" MDL
MDL "1" --> "*" DL
DL "1" <-- "*" L 

A "1" <-up- "*" DL
ME "1" <-up- "*" DL
C "1" -->"1" MLC
MLC "1" -->"*" L

@enduml

@enduml
```




