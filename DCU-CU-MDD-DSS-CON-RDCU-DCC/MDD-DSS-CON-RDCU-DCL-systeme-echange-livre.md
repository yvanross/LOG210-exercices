## Étude de cas 
### Système d'échange de livres universitaires
Le Bureau du Développement Durable (BDD) de l'Université a mis en place un système d'échange de livres aux fins de développement durable et pour réduire les coûts pour les étudiants (les clients du système). La version initiale est rudimentaire et ne permet que deux fonctionnalités :

### CU01 - Ajouter un livre à échanger

Acteur principal : Client (étudiant)

****Préconditions :****

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





```plantuml
@startuml
skinparam style strictuml
title RDCU CU01 - Ajouter un livre à échanger

participant "ctrl:ControleurAjoutLivre" as S
participant "c:Client" as E
note right of E: est visible par le controleur puisque c'est une précondition
participant "l:Livre" as L
participant "ll:List<Livre>" as LL
note right of LL: est visible par l'étudiant\npuisque l'étudiant possède une liste de livre

note left of S: controleur de session
 -> S: demarrerAjoutLivre()
activate S
deactivate S



 -> S: ajouterLivre(isbn:string, codeCondition:string)
activate S
note left of L: postcondition: Une instance l:Livre a été créée\npostcondition: l.codeCondition est devenu codeCondition (paramètre)\n\npatron créateur par défaut\npuisque PUCE ne donne aucune option valable
 S --> L**: create(string isbn, string codeCondition)

note right of S: postcondition: Une association a été créé entre l:Livre et c:Client (précondition)

 note left of L: Non cohésif\nAjoute du couplage
 S ->L: <s>ajouterClient(c:Client)</s>


note left of E: Expert en information\nControleur à une visibilité sur e\nControleur possède l\ne possèle ll
S -> E: ajouterLivre(l:livre)
note left of LL: Expert en information\ne possède ll
E->LL: add(l:Livre)


note right of S: postcondition: Une association a été crée entre l:Livre et la classe DescriptionLivre sur la base de correspondance entre DescriptionLivre.isbn == isbs (paramètre)\nAjoute d'une association entre le BDD et DescriptionLivre

participant "bdd:BDD" as B
note left of B: bdd est un objet racine visible par le controleur
note left of B: Expert en information\nContrleur a une visibilité sur bdd\nbdd a une visibilité sur une mdl
S -> B: descriptionLivre = getDescriptionLivre(string isbn)

participant "mdl:Map<isbn,DescriptionLibre>" as MDL
note left of MDL: Expert en information\nbdd a une visibilité sur mdl
B -> MDL: descriptionLivre = get(string isbn)

note left of L: Expert en information\forte cohesion c'est le livre qui doit connaitre sa description
note left of L: Pour respecter faible couplage\n il faudra déplacer getDescriptionLivre au dessus du create l:Livre \net passer al descriptionLivre en paramàtre du create l:livre
S -> L: <s>ajouterDescription(descriptionLibre:DescriptionLivre)</s>


deactivate S


 -> S: terminerAjoutLivre()
 activate S
 note left of E: Expert en information\nctrl a une visibilité sur e\ne possède ll
S->E: ll =  getLivres()



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
BDD "1" - "*" Client : fournit-\nservice-à >
Livre "*" -- "1" DescriptionLivre : est-décrit-par >
class "PropositionÉchange" as PE <<Transaction>>{
  dateHeure : DateHeure
}
PE "1" -- "1..*" Livre : offre >
PE "1" -- "1..*" Livre : reçoit >
BDD "1" - "*" PE : enregistre >
PE "1" - "1" Client : est-proposée-par >
PE "1" - "1" Client : est-proposée-à >

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
Une association a été créée entre l’instance p :PropositionEchange et c :Client
Une association a été créée entre l’instance bdd :BureauDeveloppement et p :PropositionEchange

#### CU02-Contrat-choisirClient 

**Opération :** choisirClient(nomUtilisateur : string)

**Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Une assocation entre p :PropositionEchange et client a été créée sur la base de correspondance avec le parametre idEtudiant
 
#### CU02-Contrat-proposerLivre

**Opération :** proposerLivre(idLivre :CodeLivre, estOffert :boolean)

 **Préconditions :**
Une instance c de Client existe
Une instance p de PropositionEchange existe

**Postconditions :**
Une association a été créée entre p :PropositionEchange et Livre sur la base de correspondance avec le paramètre idLivre

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


```plantuml
@startuml
title RDCU-CU02-Proposer un échange de livres
skinparam style strictuml
participant "bdd:BDD" as CTRL
note left of CTRL: controleur de façade objet racine
participant "proposeur:Client" as O
participant "pe:PropositionEchange" as PE
participant "mc:Map<nomUtilisateur,Client>" as MC
participant "client[i]:Client" as LC
participant "clientProposeA:Client" as CPA
participant "llo:List<Livre>" as LLO
participant "llr:List<Livre>" as LLR


->CTRL : démarrerPropositionÉchange()
activate CTRL
  note left of PE: Patron Createur\n bdd enregistre pe
  CTRL -> PE**: create(Client proposeur)
  note left of LLR: liste de livre a recevoir\nPatron createur\npe contient la liste de livre
  PE->LLR**: create()
  note left of LLO: liste de livre a offrir\nPatron createur\npe contient la liste de livre
  PE->LLO**: create()
  loop i < nbClient
    note left of LC: Expert en information\nbdd connait les clients\nChaque client connait sa liste de livre
    CTRL ->  LC: [Livre] = getLivres()
  end
  <<--CTRL : étudiants et livres à échanger
deactivate CTRL


-> CTRL: choisirClient(nomUtilisateur : String)
  activate CTRL
  note left of MC: Expert en information\nbdd possède mc
  CTRL->MC: clientProposeA = get(nomUtilisateur:string)
  note left of PE: Expert en information\nbdd est le créateur de pe\npe est une transaction qui identifie le client auxquel on veut offrir des livres
  CTRL->PE:   offrirAClient(clientProposeA:Client)
  note left of O: Expert en information!\nbdd connais proposeur\nproposeur possède des livres
  CTRL->O: [LivreAProposer] = getLivres()
  note left of O: Expert en information!\nbdd connais clientProposerA\nclientProposerA possède des livres
  CTRL -> CPA: [livreARecevoir] = getLivres()
  <<--CTRL: : liste de livres de l'étudiant choisi et du client
deactivate CTRL

->CTRL: proposerLivreRecevoir(idLivre : string)
activate CTRL
note left of PE: Expert en information\nbdd connait pe\npe possède une liste de livre a recevoir llr
CTRL -> PE :ajouterLivreARecevoir(idLivre:string)
note left of LLR: Expert en information\n pe possède la liste llr
PE -> LLR: add(idLivre)
deactivate CTRL

->CTRL: proposerLivreOffrir(idLivre : CodeLivre)
activate CTRL
note left of PE: Expert en information\nbdd connait pe\npe possède une liste de livre a offrir llo
CTRL -> PE:ajouterLivreAOffrir(idLivre:string)
note left of LLO: Expert en information\n pe possède la liste llo
PE -> LLO: add(idLivre)
deactivate CTRL

->CTRL: terminerProposition()
activate CTRL
note left of PE: Expert en information\nbdd est le créateur de pe\npe possède les listes de livres
CTRL -> PE: [nbLivreAOffrir, nbLivreARecevoir] = terminerProposition()
note left of LLR: Expert en information, pe possède la liste de livre
PE->LLR: nbLivreARecevoir = getSize()
note left of LLR: Expert en information, pe possède la liste de livre
PE->LLO: nbLivreAOffrir = getSize()
note left of PE: Expert en information, mutateur d'attribut
PE -> PE: setDateTime()

<<--CTRL: nombre livres a offrir et a recevoir
deactivate CTRL

->CTRL: confirmerÉchange()
activate CTRL
<<--CTRL: resumé de l'échange
deactivate CTRL

@enduml
```





