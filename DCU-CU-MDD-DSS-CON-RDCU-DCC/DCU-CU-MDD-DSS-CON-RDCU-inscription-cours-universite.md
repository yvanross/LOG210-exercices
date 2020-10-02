# Système d'inscriptions à des cours
Une université désire un système permettant aux étudiants de gérer leurs inscriptions aux différents trimestres. Du côté administratif, l'université requiert l'admission des étudiants et l'organisation des trimestres. Le diagramme des cas d'utilisation ci-dessous (Figure 1) résume les fonctionnalités demandées par l’université.


```plantuml
@startuml
skinparam style strictuml
left to right direction
rectangle "Système d'inscription"{
(CU01 - S'inscrire au prochain trimestre) as CU01
(CU02 - Modifier son inscription) as CU02
(CU03 - Admettre un étudiant) as CU03
(CU04 - Planifier un trimestre) as CU04
}
Étudiant -- CU01
Étudiant -- CU02
Registraire -- CU03
AgentAdministratif -- CU04
@enduml
```


##CU01- S'inscrire au prochain trimestre
**Acteur principal :** l’Étudiant
****Préconditions :****
- La période d'inscription est en vigueur. 
- L'étudiant est authentifié à partir d’un poste internet (avec une adresse IP).

**Garanties en cas de succès (postconditions) :**
Une inscription est enregistrée. La comptabilité et les places disponibles dans les groupes-cours sont mises à jour.  

**Scénario principal (succès) :**
1. Un étudiant désire s'inscrire à des cours lors du prochain trimestre.
1. L'étudiant démarre une inscription.
1. Le système affiche les cours offerts pour lesquels l’étudiant a réussi les cours préalables.
1. L'étudiant sélectionne un cours.
1. Le système affiche les informations à propos du cours et les groupes-cours offerts.
1. L'étudiant sélectionne un groupe-cours.
1. Le système affiche l'horaire du groupe-cours.

Les étapes 6 et 7 sont répétées tant que l'étudiant ne s'inscrit pas à un groupe-cours.

8. L'étudiant s'inscrit au groupe-cours.

Les étapes 4 à 8 sont répétées tant que l'étudiant ne confirme pas son inscription.

9. L'étudiant confirme son inscription.
10. Le système demande à l'étudiant de saisir sa clé d’authentification comme confirmation finale.
11. L'étudiant saisit sa clé d’authentification.
12. Le système enregistre l'inscription.

**Scénarios alternatifs**
8a. L'étudiant a atteint la limite du nombre de cours auxquels il peut s'inscrire dans un trimestre.
  1. Le système affiche un message avertissant l'étudiant qu'il a atteint la limite de cours.
    1. Retour à 3.

11a. L’étudiant saisit une mauvaise clé d’authentification.
  1. Le système affiche un message que l’inscription n’a pas fonctionnée
  2. Fin de cas d’utilisation [NB : cette terminaison est une simplification pour l’exercice. La bonne fonctionnalité du système donnera à l’étudiant plusieurs tentatives pour saisir sa clé, puis éventuellement désactiver le compte de l’étudiant en cas de trop d’échecs, etc.]


## MDD Inscription a des cours avec catégorie de classe


```plantuml

@startuml
top to bottom direction
title MDD
package System {
class Universite <<Organisation>>
class Etudiant <<Role>>
class Inscription <<Transaction>>
class Cours <<Description d'entité>>{
  sigle: string
}
class Trimestre <<planification>>{
  String session
  Integer annee
  Date debutInscription
  Date finInscription
}
class GroupeCours <<Service>>
class Horaire <<Planification></Planification>>
Universite -- Cours: Offre des formations
Etudiant "1" - "*" Inscription: effectue
Inscription "1" -- "*" GroupeCours: est pour
Cours "1" -- "*" GroupeCours: sont décrit par <
GroupeCours "1" -- "1" Horaire: se donne selon
GroupeCours "*" -- "1" Trimestre: s'appliquent >
Cours "1" -- "*" Cours: est préalable >
}
@enduml
```



### DSS
```plantuml

@startuml
hide footbox
title Scénario de S'inscrire à un trimestre
'Dans un DSS, un actor est externe au système
'Truc PlantUML - “as E” définit E comme un synonyme de :Étudiant. 
'Truc PlantUML - il faut mettre les "" autour du nom :Étudiant, car cela commence avec deux points (:)
actor ":Étudiant" as E
'Système vu en tant que boîte noire. Le nom pourrait être “Système de vente NextGen” 
'  mais on se contente de “Système”.
'les deux points (:) indiquent une instance et sont expliqués dans 
'  le chapitre sur la notation des diagrammes de sequence UML
participant ":Système" as S
E->S: démarrerInscription(adresseIP)
'Cadre d’interaction pour représenter une boucle UML avec une expression booléenne servant de garde
'Truc PlantUML – tout ce qui suit “loop” est considéré comme une condition de la boucle (sytaxe est souple)
loop Inscription pas confirmée
  E->S: saisirCours(cours)
' Valeur(s) de retour au message précédent. Abstraction ne tenant pas compte de la présentation ni du medium. La ligne de retour est facultative si rien n’est retourné.
  E<--S: infos et groupes
  loop n'a pas ajouté groupe-cours
    E->S : saisirGroupeCours(groupeCours)
    E<--S : horaire du groupe
  end
  E->S: ajouterGroupeCours(groupeCours)
'Truc PlantUML – end signifie la fin de la boucle (ça ferme le cadre d’interaction)
end
E->S: terminerInscription
E<--S: demande d'authentification
E->S: finaliserInscription(clé)
@enduml
```

### Contrat CU01-démarrerInscription
**Opération :** démarrerInscription(adresseIP : String)
**Préconditions :** aucune
**Postconditions :**
- une instance ins d’Inscription a été créée
- ins.adresseIP est devenu adresseIP

### Contrat CU01-saisirCours(cours)
**Opération :** saisirCours(cours :String)
**Préconditions :** 
- une inscription est en cours

**Postconditions :**
- aucune 

### Contrat CU01-saisirGroupeCours
**Opération :** saisirGroupeCours(groupeCours :String)
**Préconditions :** 
- une inscription est en cours

**Postconditions :**
- Aucune

### Contrat CU01-ajouterGroupeCours
**Opération :** ajouterGroupeCours(groupeCours :String)
**Préconditions :** 
- une inscription est en cours
**Postconditions :**
- une association entre ins et GroupeCours a été formée sur une base de correspondance avec groupeCours.

### Contrat CU01-terminerInscription
**Opération :** terminerInscription
**Préconditions :** 
-  une inscription est en cours

**Postconditions :**
- aucune 

### Contrat CU01-finaliserInscription
**Opération :** finaliserInscription (clé :String)
**Préconditions :** 
- une inscription est en cours

**Postconditions :**
- une association entre ins et Étudiant a été formée
- ins.dateHeure est devenu la date et heure actuelle.
- une association entre ins et GrandLivre a été formée


### CU01-RDCU-demarrerInscription

Pour la réponse à cette question, nous commençons avec la première opération système que l’on trouve dans le DSS. C’est démarrerInscription :

N.B. La solution pour démarrerInscription sera présentée en étapes, pour mieux comprendre un processus de RDCU. Ce n’est pas un processus « propre » où on voit tout de suite la solution finale. La conception est souvent un processus « bâclé ». On décompose un problème en sous-problèmes et on les relie ensemble, par exemple. Les solutions pour les autres opérations système seront plus courtes, mais impliquent un processus similaire.

La première étape dans toute RDCU est de déterminer quel objet de la couche-domaine va recevoir l’opération système (dans ce cas, démarrerInscription) :

```plantuml
@startuml
skinparam style strictuml
title Réalisation de cas d'utilisation: démarrerInscription
-> ":?" : démarrerInscription(adresseIP)
@enduml
```

**GRASP Contrôleur :**
Quel est le premier objet en dehors de la couche présentation qui reçoit et coordonne (« contrôle ») les opérations système ?

Affectez une responsabilité à la classe qui correspond à l'une de ces définitions :
- Elle représente le système global (contrôleur de façade).
- un « objet racine »(contrôleur de façade).
- un équipement (contrôleur de façade).
  un sous-système (contrôleur de façade).
- Elle représente un scénario de cas d'utilisation dans lequel l'opération système se produit (contrôleur de session ou de cas d'utilisation).

```plantuml
@startuml
skinparam style strictuml
title Réalisation de cas d'utilisation: démarrerInscription
-> ":GestionnaireInscription" : démarrerInscription(adresseIP)
note left: GRASP Contrôleur de session
@enduml
```

En suivant le point 1 de Contrôleur, essayons de trouver un « objet racine » dans le modèle du domaine. Y a-t-il un objet représentant un équipement ou un sous-système? Dans l’exemple du livre, il y a une classe conceptuelle « Registre » qui est en effet un équipement. Cependant, dans notre modèle du domaine en annexe, il n’y a pas d’objet racine. Alors, nous devons suivre le point 2 pour déterminer l’objet contrôleur. C’est-à-dire utiliser un contrôleur de session. Appelons cet objet « GestionnaireInscriptions » puisque Gestionnaire est un nom fréquemment utilisé pour les contrôleurs de session et Inscriptions est l’objet du cas d’utilisation dans lequel on travaille en ce moment. 

Cette prise de décision donne le résultat suivant, qui est un diagramme de séquence UML démontrant l’opération système qui arrive sur le contrôleur. Toute RDCU commence par cette étape. Notez que la décision GRASP est annotée dans la note du diagramme :


Pour la suite de cette RDCU, il faut satisfaire toutes les postconditions du contrat correspondant à l’opération système. Le contrat est dans l’annexe, mais on le répète ici :

**Contrat C01 : démarrerInscription**
**Opération :** démarrerInscription(adresseIP : String)
**Préconditions :**
- aucune
**Postconditions :**
- une instance ins d’Inscription a été créée
- ins.adresseIP est devenu adresseIP

Les deux postconditions peuvent être considérées comme l’initialisation d’une instance de Inscription. Là, il s’agit de créer une instance de l’objet Inscription en passant l’adresse IP comme argument. Cela veut dire que quelque part dans la RDCU, il y aura un élément comme la figure suivante :

```plantuml
@startuml
skinparam style strictuml
participant "?"
create "ins:Inscription"
"?"-> "ins:Inscription" : create(adresseIP)
@enduml
```

Cependant, la classe qui instancie « ins :Inscription » n’est pas encore déterminée, car on voudrait suivre les principes GRASP avant de prendre une décision erronée. Alors, quel GRASP s’applique lorsqu’il s’agit de créer une instance? On peut poser la question autrement : qui prend la responsabilité de créer l’instance « ins »? 

**Rappelons le GRASP Créateur :**

**Qui crée ?** (Notez que Fabrique Concrète est une solution de rechange courante.)
Affectez à la classe B la responsabilité de créer une instance de la classe A si l'une des assertions suivantes est vraie :
1. B **P**ossède A
2. B **U**tilise étroitement A
3. B **C**ontient A
4. B **E**nregistre A
5. B agrège A
6. B a les données pour initialiser A


Dans notre cas, la classe A est « Inscription » et nous devons décider la classe B qui va l’instancier. Alors, y a-t-il des classes dans le modèle du domaine (question 4) qui répondent à une ou à plusieurs assertions de Créateur?

Qui « contient » ou « agrège » ou « a les données pour initialiser » ou « enregistre » ou « utilise étroitement » Inscription?

On voit dans le modèle du domaine que GrandLivre agrège/contient/enregistre des Inscriptions. Alors, il pourrait être un candidat pour le créateur. Les seules autres classes liées à Inscription sont Étudiant et GroupeCours. Étudiant agrège une inscription, mais pas de la même façon que GrandLivre. GroupeCours n’agrège pas Inscription (c’est le contraire). 

Conclusion : <s>GrandLivre</s> ControleurInscription est, selon le principe GRASP Créateur, la bonne classe pour instancier les nouvelles Inscription. On peut proposer cette partie de la RDCU, indiquée dans la figure suivante avec une annotation de notre décision :

```plantuml
@startuml
skinparam style strictuml
participant ":ControleurInscription" as gl
participant "ins:Inscription" as ins
create ins
gl -> ins : create(adresseIP)
note right: GRASP Créateur\n(Controleur agrège Inscription)
@enduml
```

Maintenant, il faut combiner les deux parties (le partie contrôleur et la partie créateur) pour compléter la RDCU :

```plantuml
@startuml
skinparam style strictuml
participant ":GestionnaireInscription" as Ctrlr
title Réalisation de cas d'utilisation: démarrerInscription
-> Ctrlr : démarrerInscription(adresseIP)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
Ctrlr -> ":GrandLivre" : ??????
participant ":GrandLivre"
note over "ins:Inscription": GRASP Créateur\n(GrandLivre agrège Inscription)
create "ins:Inscription"
":GrandLivre"-> "ins:Inscription" : create(adresseIP)
@enduml
```

Il y a juste un problème – le flot de contrôle doit passer du GestionnaireInscription au GrandLivre, indiqué par le message « ????? » au milieu de la figure. Nous devons proposer une méthode que GrandLivre va implémenter pour faire le travail d’instanciation d’Inscription. De plus, GestionnaireInscription devrait « voir » la référence ins, car cette information sera probablement utilisée plus tard dans une autre opération système. GestionnaireInscription gardera cette information pour la durée de la session.

Pour compléter la RDCU, on propose une méthode addInscription(adresseIP) implémentée dans GrandLivre. Voici la RDCU finale pour l’opération système. Notez que nous avons ajouté le principe GRASP Expert à la deuxième annotation, car la méthode addInscription est naturellement justifiée par Expert  :

```plantuml
@startuml
skinparam style strictuml
participant ":GestionnaireInscription" as Ctrlr
title Réalisation de cas d'utilisation: démarrerInscription
-> Ctrlr : démarrerInscription(adresseIP)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
Ctrlr -> ":GrandLivre" : ins = addInscription(adresseIP)
participant ":GrandLivre"
note over "ins:Inscription": GRASP Créateur\n(GrandLivre agrège Inscription)
create "ins:Inscription"
":GrandLivre"-> "ins:Inscription" : create(adresseIP)
@enduml
```
Pour terminer cette RDCU, nous pouvons faire une vérification des éléments :
- contrôleur GRASP a été annoté
- toutes les postconditions du contrat ont été satisfaites
- toutes les décisions ont été justifiées par (au moins) un GRASP

N.B. dans le cas d’utilisation, il y a mention des informations retournées par l’opération système : « 3. Le système affiche les cours offerts pour lesquels l’étudiant a réussi les cours préalables. »Cependant, la complexité de cette étape nuit à l’objectif pédagogique de cet exercice et donc elle serait ignorée.

[considérer les informations retournées comme un détail avancé]

Faisons les RDCU pour le reste des opérations systèmes.



### CU01-RDCU-saisirCours

Notez que l’on utilise toujours le même contrôleur GRASP pour toutes les opérations système dans le même cas d’utilisation. 

Bien qu’il n’y ait pas de postcondition dans le contrat de saisirCours, il faut que la conception tienne compte du bon comportement (la fonctionnalité spécifiée dans le cas d’utilisation). On voit bien dans le DSS que le résultat doit être l’affichage d’une liste de groupes offerts pour le cours en question. Pour réaliser ce comportement, il est nécessaire de rechercher des informations, grâce à la relation entre Cours et GroupeCours. 

On doit effectivement trouver la référence à une instance de Cours correspondant à l’argument cours qui est une String. Par exemple, si cours = « LOG210 », alors il faut repérer l’objet Cours pour lequel l’attribut titre = « LOG210 ». Larman fait référence à ce genre de recherche comme un idiome (ou patron de programmation) qui s’appelle « Transformation des identifiants en objets » à la page F.451 (ou « IDs to Objects » à la page A.460).

Pour comprendre l’utilisation de l’instance de Map<Cours>, voir la section « Recherche d’une DescriptionProduit » à la page 333, ainsi que la figure 17.7 à la page 334. 

La méthode Cours.getGroupes() retourne un Map<GroupeCours>, car c’est l’ensemble des GroupeCours associé à l’objet c :Cours.

```plantuml
@startuml
skinparam style strictuml
participant ":GestionnaireInscription" as Ctrlr
title Réalisation de cas d'utilisation: saisirCours
-> Ctrlr : saisirCours(cours)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
Ctrlr -> ":CatalogueCours" : groupes = getGroupes(cours)
note right: GRASP Expert (Catalogue et\nCours serait les experts de\ncours et des groupes)
":CatalogueCours" -> ":Map<Cours>" : c = chercher(cours)
":CatalogueCours" -> "c:Cours" : groupes = getGroupes
@enduml
```

L’explication qui suit est une parenthèse pour comprendre la conception avec un :Map. Elle ne fait pas partie d’une RDCU. Considérer la relation entre CatalogueCours, Cours et GroupeCours :

```plantuml
@startuml
skinparam style strictuml
hide empty methods
hide empty members
class CatalogueCours
class GroupeCours {
identificateur : String
}
class Cours {
titre : String
}
CatalogueCours "1" - "*" Cours : répertorie >
Cours "1" - "*" GroupeCours : est-dispensé-dans >
@enduml
```

Pour donner un exemple concret où il y a 3 cours dans le catalogue, on utilise un diagramme d’objet en UML :

```plantuml
@startuml
skinparam style strictuml
object ":CatalogueCours" as cat
object "c1:Cours" as c1 {
  titre = "LOG121"
}
object "c2:Cours" as c2 {
  titre = "LOG210"
}
object "c3:Cours" as c3 {
  titre = "LOG240"
}
cat -- c1
cat -- c2
cat -- c3
@enduml
```

Alors, lorsqu’on agrège des objets, dans la conception on considère l’utilisation d’une collection comme une List ou une Map. On pourrait même utiliser un simple tableau. Lorsqu’on doit repérer ces objets par une clé unique (p.ex. le titre du cours), il est pratique d’utiliser une Map. Si vous avez oublié ces notions, il est important de les revoir dans le tutoriel de Java ou dans le livre de LOG121 ou même INF111. 


```plantuml
@startuml
skinparam style strictuml
object ":CatalogueCours" as cat
object "c1:Cours" as c1 {
  titre = "LOG121"
}
object "c2:Cours" as c2 {
  titre = "LOG210"
}
object "c3:Cours" as c3 {
  titre = "LOG240"
}
object ":Map<Cours>" as map
cat - map
map -- c1
map -- c2
map -- c3
@enduml
```

### CU01-RDCU-saisirGroupeCours

Il n’y a toujours pas de postcondition dans le contrat de saisirGroupeCours, mais il doit y avoir l’affichage de l’horaire pour le groupe-cours en question. 

```plantuml
@startuml
skinparam style strictuml
participant ":Gestionnaire\nInscription" as Ctrlr
title Réalisation de cas d'utilisation: saisirGroupeCours
-> Ctrlr : saisirGroupeCours(groupeCours)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
Ctrlr -> ":CatalogueCours" : horaire =\ngetHoraire(groupeCours)
note right: GRASP Expert (Catalogue et\nCours serait les experts de\ncours et des horaires)
":CatalogueCours" -> ":Map<Cours>" : c =\nchercher(cours)
note right: Notez que la valeur de cours\nsera décortiquée de groupeCours,\np.ex. "LOG210" de "LOG210-01"
":CatalogueCours" -> "c:Cours" : horaire = getHoraire(groupeCours)
note right: GRASP Expert (GroupeCours\nserait l'expert des horaires)
"c:Cours" -> ":Map\n<GroupeCours>" : gc =\nchercher(groupe)
"c:Cours" -> "gc:\nGroupeCours" : horaire =\ngetHoraire
@enduml
```


### CU01-RDCU-ajouterGroupeCour

La postcondition contient la phrase « sur une base de correspondance avec groupeCours » ce qui veut dire une recherche de l’objet correspondant à l’argument groupeCours . N’oubliez pas que nous ne pouvons pas utiliser les références aux objets du domaine comme arguments sur les opérations système, car on est limité aux types primitifs (afin de permettre un changement de couche de présentation facilement). 

Notez que ins est toujours « visible » car elle a été stockée par le contrôleur GRASP.

```plantuml
@startuml
skinparam style strictuml
participant ":Gestionnaire\nInscription" as Ctrlr
title Réalisation de cas d'utilisation: ajouterGroupeCours
-> Ctrlr : ajouterGroupeCours(groupeCours)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
note left of Ctrlr : GRASP Expert justifie\ntoutes les autres méthodes\ndans ce diagramme
Ctrlr -> ":CatalogueCours" : gc=\ngetGroupeCours\n(groupeCours)
":CatalogueCours" -> ":Map<Cours>" : c=chercher(cours)
":CatalogueCours" -> "c:Cours" : gc=\ngetGroupeCours(groupe)
"c:Cours" -> ":Map\n<GroupeCours>" : gc=\nchercher\n(groupe)
Ctrlr -> "ins:Inscription" : ajouterGroupeCours(gc)
@enduml
```

### CU01-RDCU-terminerInscription

Une opération sans postcondition, elle indique la sortie de la boucle. Nous n’avons rien à faire dans la couche domaine, alors il n’y a pas besoin de faire un diagramme de séquence UML pour cette opération. Cependant, ça sera le même contrôleur GRASP qui s’occupe d’enclencher la demande d’authentification dans la couche de présentation.

### CU01-RDCU-finaliserInscription

Cette opération système contient trois postconditions, alors on doit être sûr de les satisfaire.

Normalement on vérifie la clé pour une bonne fonctionnalité dans le cas d’utilisation. 

Notez que e et ins ont été stockés dans le contexte de la session par GestionnaireInscription (contrôleur GRASP). 

```plantuml
@startuml
skinparam style strictuml
participant ":Gestionnaire\nInscription" as Ctrlr
title Réalisation de cas d'utilisation: finaliserInscription
-> Ctrlr : finaliserInscription(clé)
note left of Ctrlr : GRASP Contrôleur de session\n(aucun objet racine dans\nle modèle du domaine)
note left of Ctrlr : GRASP Expert justifie\ntoutes les autres méthodes\ndans ce diagramme
Ctrlr -> "e:Étudiant" : estValide=\nestValid(clé)
alt estValide
Ctrlr -> "ins:Inscription" : setÉtudiant(e)
Ctrlr -> "ins:Inscription" : setDateHeure(now)
Ctrlr -> ":GrandLivre" : ajouterInscription(ins)
else !estValide
create CléNonValideException
Ctrlr --> CléNonValideException : create
end
@enduml
```


### DCL a faire