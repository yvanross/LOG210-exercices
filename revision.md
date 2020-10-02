# Révision 


# Question de révision de Larman

Review Questions from Larman

Les réponses sont affiché avec un font blanc. Sélectionner le texte pour
voir celle-ci.

**Chapter 2:**

> \- What is *iterative development*?

La croissance et l'affinement successifs d'un système par le biais
d'itérations multiples, le feed-back et l'adapdation cycliques.

> \- What is the benefit of short iterative cycles?

Feedback rapide et adaptation

> \- What are the benefits of iterative development?

Diminution des échecs, amelioration de la productivité et de la qualité.
Gestion précoce des risques élevés. Feedback, implication des
utilisateurs et adaptation précoces. Complexité géré, Possibilité
d'exploiter méthodiquement les lecon tirées d'une iteration.

> \- What is the *waterfall life-cycle*?

Méthode on l'on tente de défénir la plus grande partie des
specifications, voire toutes, avant de programmer

> \- What is "waterfall thinking"? What is wrong with it?
>
> L'idée qu'on peut écrire tous les cas d'utilisation ou realiser tous
> les modèles OO détaillé avant de commencer à programmer et un exemple
> de raisonnement incorrect. C'est l'une des principals raison d'échec
>
> \- What is *risk-driven* iterative development?
>
> Les objectifs des premières iterations sont choisis afin d'identifer
> et d'atténuer les risques les plus importants et construire les
> fonctionnalités visibles qui compte le plus pour le client
>
> \- What is *client-driven* iterative development?

Notre première priorité est de satisfaire le client en lui livrant
rapidement et de facon continue un logiciel de qualité. Accepter les
changements des besoins, meme en cours de développpement. Livrer
fréquemment. Experts métier et developpeurs doivent travailler ensembles
quotidiennement pendant toute la durée du projet.

> \- What is an *agile* process?

Processus qui prévilégie: les individus et les interactions advantage
que les processus etles outil; les logiciels fonctionnels advantage que
l'exhautivité de la documentation; la collaborationavec le client
advantage que la négociation de contrats; la réponse au changement
advantage que l'application d'un plan.

> \- What is the "secret of modeling" (its primary purpose)?

L'objectif de la modélisation (des diagrammes UML) est avant tout de
comprendre, pas de documenter.

> \- Does an agile process mean there is no modeling?

Non. Cela signifie qu'on génère seulement les artefact requis pour
comprendre le système.

> \- Identify some current agile processes.

Inception, Élaboration, Construction et Transition.

> \- What are the UP disciplines and how do they map to the traditional
> life-cycle?

Exigences: Modèle de cas d'utilisation et specifications supplémentaires

Modelisation métier: Modèle du domaine,

Conception: Modèle de conception DCC

Implémentation: programmation et construction du système

Environnement: Choix des outils et personalisation du processus.

> \- What is an *artifact*?

Tout document permettant d'apporter une comprehension au système

> \- Contrast a *heavy* process with an *agile* process.

Chapter 3:

> \- Identify the typical architectural layers (subsystems).

Interface usilisateur, couche logique applicative, autre couches et
composantes( service technique)

Chapter 5:

> \- Define *requirements*.

Condition auquels un système ou un projet doivent satisfaires

> \- What does it mean to manage requirements?

D'effectuer un travail systèmatique de recherché, de documentation,
d'organisation et de suivi des besoins évolutive du système (RUP) dna un
context oules sohaits des parties intéressés ne sont pas toujours
explicites et changent inévitablement.

> \- What are the types of requirements? (FURPS+)

Fonctionnalité, Aptitude à l'utilisation, Fiabilité, Performance,
Possibilité de prise en charge, Implémentation, interface, exploitation,
conditionnement, aspects juridiques.

> \- True or false: Requirements are object-oriented.
>
> false
>
> \- What is meant by *functional* requirements?

Les requis en terme de fonctions, capatités et de sécurité

> \- What are the requirements *artifacts*?

Modèle de cas d'utilisation, specifications supplémentaires, Glossaire,
Visition, Règles métier

Chapter 6 - Use Case Modeling

> \- Define the term *use case*.

C'est un artefact représentant les acteurs et les cas d'utilisation ansi
que les relation les unissant.

> \- Who is the \"guru\" of use case(s)?

L'acteur principal

> \- What is an *actor*?

Entité qui a un comportement, comme une personne (identifiée par un
role)

> \- Give examples of actors.

Un caissier, un système, une entreprise

> \- True or false: Use cases are object-oriented.

non

> \- A use case helps capture system \_\_\_\_\_\_\_\_\_\_\_\_\_.

requirement

> \- What is a *scenario*?

C'est une suite spécifique d'actions et d'intéractions entre un ou
plusieurs acteurs et le système. Histore de la facon dont on utilise le
sysème

\- What is the relationship between a use case and a scenario?

Un use case est une collection de scenario de réussite ou d'échec qui
décrit la facon don't un ou plusieurs acteurs utilisent un système pouir
atteindre un but.

> \- Identify three ways to format/express a use case.

Abrégé  scenario de base dans un paragraphe.

Informel  différents scenarios sont décrits dans plusieurs paragraphe.

Détaillé  toutes les étapes et les variatnes sont indiquées en detail,
avec les prédondition et guaranties en cas de succèes.

> \- What must be specified in a \"fully dressed\" use case?

toutes les étapes et les variatnes sont indiquées en detail, avec les
prédondition et guaranties en cas de succèes.

> \- What is an extension/alternate flow?

Elle indique tous les autres scenarios ou branchement possibles, tant en
cas de succèes qu'en cas d'échec.

> \- Give examples of special requirements.

Besoin non fonctionnel, un attribute de qualité ou une contrainte.

> \- What are the three kinds of steps in a scenario?
>
> \- What does \"essential UI-free style\" mean?

Dans le style essential, on rédige le scenario au niveau des intentions
de l'utilisateur et des responsabilités du systèe au lieu de decrier des
actions concretes. Il demeure exempt de ldétails sur la technique et les
mécanismes, en particulier ceux qui sont lies au L'IHM"

> \- What techniques are used to find use cases?

Adopter une perspective centre sur les acteurs et les buts.

> \- What is the \"boss test\"?

Votre patron vous demande : À quoi avez vous passé la journée?. Vous
répondez "je me suis connecté". Votre patron est t-il content?

> \- What is the \"EBP (PME) test\"?

Processus métier élémentaire: Tâche effectuée par une personne en un
lieu et un tmeps donnés, en réponse à un évènement, et qui ajoute rune
valeur commercial measurable et laisse les données dans un état
coherent.

> \- What is a use case diagram?

Représentation des noms des cas d'utilisation, ceux des acteurs et les
relations qui existent entre eux.

> \- What are the components of a use case diagram?

Acteur, les cas d'utilisation, système

Chapter 7 - Identifying Other Requirements

> \- What goes into the Supplementary Specification?

Les états, la documentations, le packageing, le support, les licences,
etc.

> \- What is a Vision?

Les specifications de haut niveau élaborées dan le modèle de cas
d'utilisation et dans les specifications suplémentaires ainsi que
l'étude d'opportunité du projet. Vrève vue d'ensemble qui permet de
dévouvrir rapidement les grandes idées d'un projet.

> \- What is the 4-step sequence for developing a Vision along with use
> cases?

Rédiger un bref préprojet de la Vision

Identifier les buts des utilisateurs et les cas d'utilisation
correspondant par leur nom

Rédifer certains cas d'utilisation en detail et commencer les
Spécifications Supplémentaires

Affiner la vision en résumant les informations receuillies.

> \- Comment on the author\'s \"freeze and sign off\" discussion.

Chapter 9 - Domain Models

> \- Define the term *domain model*.

Représentation visuelle des classes conceptuelles ou des objets du monde
reel dans un domaine donné. (modèle conceptual, modèle object du
domaine, modèle objet d'analyse.)

> \- What is a *conceptual class*?

Une idée, une shoes oui un objet qu'on peut considéré en terme de
symbole, d'intension et d'extension.

Symbole: mot ou image qui représente un classe conceptuelle

Intension: Définition d'une classe conceptuelle.

Exension: L'ensemble des exemples auxquels la classe conceptuelle
s'applique.

> \- Describe the difference in the way a problem is decomposed using
> structured analysis vs. using object-oriented analysis.
>
> \- What notation is used to illustrate a domain model?
>
> UML
>
> \- How does the term *abstraction* relate to modeling?
>
> \- What is the difference between a *domain model* and a *domain
> layer*?
>
> \- What is the \"representational gap\"?

Réduire le décalage de preprésentation en nommant les classes
logicielles de la couche domaine en s'insperant des noms du modèle du
domaindes avec des objets disposant d'informations et de responsabilités
familières au domaine.

> \- What are two techniques for finding conceptual classes?

Utiliser une liste de categories.

Identifier les groups nominaux.

> \- What are the four steps to building a domain model?

Tracer un diagramme de classe en mode esquisse

Utiliser un outils pour maintenir le modèle (photo, UML)

Inclure les rapports, recu dans le glossaire

Penser comme un cartographe  employé les termes du domains.

> \- What is a *description class*? Why use a description class?

Classe qui contient des informations qui décrivent quelque chose
d'autre.

Quand il est nécessaire de disposer de la description d'un produit ou
d'un service, indépendamment de l'existance actuelle de ces produitsou
de ces services.

Quand la suppression d'instances d'une entité qu'elle décrit entraine la
perte d'une information qui doit être memorise mais a été incorrectement
associée à l'entité en question.

Quand elle réduit la redondance ou la duplication des inforamtions.

> \- How does one determine whether a concept is a conceptual class or
> an attribute?

Si non pensons a une entité X en termes alphanumérique dans le monde
reel, alors X est probablement un attribute.

> \- What is an *association*?

C'est une relation entr des instances de classe qui indique un
connection significative ou intéressante.

> \- What is a *role*? (3 parts to a role)

Les extrémités des associations sont appelées roles. Nom, multiplicité,
navigabilité (fleche).

> \- What is an *attribute*?

C'est la valeur d'une données logique d'un objet.

Notation: visibilité nom: type multiplicité = défaut {propriété}

> \- What is a data type? How is it different from a class in this
> context?

Nombres, booléens, caractères, chaines de caractères, enumeration...

C'est un ensemble de valeur dont l'identité propre n'a pas de
signification dans le context de notre modèle. Les types de données sont
généralement immuables.

> \- What is a *foreign key*? Why is its use discouraged in the domain
> model?

C'est un attribute qui relie deux classes ensemble par une clé. On veut
représenter les liens entre les classes par des association.

> \- What is a *derived attribute*?

C'est un attribute qui est calculé à partir des informations continues
dans le modèle du domaine

Chapter 10 - System Sequence Diagram

> \- What does a system sequence diagram show?

Il illustre les évènements d'entrées/sorties associés aux systèmes
concerné. Il constitue la sources des contrats d'opération.

> \- Describe the notation used to draw an SSD.

:acteur, :system, lignes de vies, Messages avec paramêtres (opérations),
valeur de retour, cadre d'intéraction (loop, alt)

> \- How does one express a loop in an SSD?

Cadre identifé avec loop en haut a droite + \[condition\]

> \- How does one build an SSD? On what artifact is the SSD based?

Par l'étude d'un scenario d'un cas d'utilisation

> \- Where in the development cycle would one draw SSD\'s?

L'élaboration

> \- What are the types of events the system must react to?

Evènements généré par l'utilisateur (l'acteur)

Chapter 11 - Operation Contracts

> \- What is an operation contract?

Description des changements détaillés subis par les objets d'un modèle
du domaine et qui resulte d'une opèration du système.
Création/destruction d'instance, creation/destruction d'association ,
modifification d'attribut

> \- What is the purpose of operation contracts?

Ils fournissent des details sur l'effet des operations systèmes
impliquées dans le cas d'utilisation.

> \- What is the structure of an operation contract?

Opération, reference croisées, preconditions, postconditions.

> \- Where does one find operations in order to generate operation
> contracts

Dans le diagramme de sequence sytème

> \- What are the types of state changes that can be described in
> postconditions?

Création/destruction d'instance, creation/destruction d'association ,
modifification d'attribut

> \- What is the relationship between a system event and a system
> operation?

Systems operation will realise the system events.

Chapter 13 (12F) - Logical Architecture

> \- What is the logical architecture?

L'architecture logique définit les packages dans lesquels s'inséreront
les classes logicielles en tenant compte des contraintes arthitecturales
documentées dans les specifications supplémentaires.

> \- What is a layer?

C'est un regroupement à très forte granulatiré de classes, package et
sous-systèmes qui a une responsabilité de cohesion pour un aspect majeur
du système.

> \- What are the typical layers in an object-oriented system?

Présentation, logique applicative et objets du domaine, service
technique

> \- What is the primary benefit of structuring a system with layers?

Réduction du couplage et des dépendances. Encapulation et décomposition
de la complexité. On peut remplacer certaine couches par de nouvelle
implementation. Facilite la réutilisation et le développement en équipe.

> \- What is the model-view separation principle?

Ne pas coupler directement des objets de l'IHM avec d'autres objets du
modèle du domaine.

Ne pas placer la logique applicative dans les methods d'un objet de
L'IHM.

> \- In an object-oriented system what does one find in the model? in
> the view?

Model: logique application

View: fenêtres, pages web, applets, les états.

Chapter 14 (13F) - On To Object Design

> \- What type of diagram is commonly used to express a static model?

Diagrammes de classes conceptuelle et logicielle.

> \- What type of diagram is commonly used to express a dynamic model?

Diagrammes de sequence, diagrammes de communication

> \- What are CRC cards?

Classe-Responsabilité-Collaboration offrent une technique de
modélisation orientée texte

> \- What does CRC stand for?

Classe-Responsabilité-Collaboation

> \- What are CRC cards used for?

Modelisation des classes logicielles

Chapter 15,(14F) - UML Interaction Diagrams (Notation)

> \- What are the two different types of interaction diagrams?

Diagramme de sequence

Diagramme de communication

> \- What is an advantage of each type of interaction diagram over the
> other?

Sequence: indique clairement la sequence et l'ordonnancement des
message. Consomme trop d'espace horizontale

Communication: économique en termes d'espace, permet l'ajout d'objets
dans les deux dimensions. Lecture des sequences de message plus
difficile.

> \- Notations:

messages

returns

activation box

message to self

object creation

life lines

conditional message

iteration

iteration over a collection

message to a class (static call)

synchronous vs. asynchronous calls

Chapter 16 (15F)- UML Class Diagrams

> \- How does a design class diagram differ from the class diagram used
> for the domain model?

On y indique les methods de chaque classes

> \- What are the two options for showing attributes in a design class
> diagram and how does one decide which one to use?

Texte et ligne d'association

> \- What is generalization and how is it drawn in a UML class diagram?

Relation taxonomique entre un classificateur plus généraleet un
classificateur plus spécifique. Chaque instance du classificateur
spécifique est également une instance indirecte du classificateur
general.

> \- Give an example of generalization.
>
> \- What is composition and how is it drawn in a UML class diagram?

Une instance de la partie A appartient à seulement une instance
composite à la fois. La partie doit toujorus appartenir a un tout
composite. L'élément composite est responsible de la
creation/destruction de sys composantes.

> \- Give an example of composition.

Main avec ses doigts.

> \- What is a dependency relationship and how is it drawn in a UML
> class diagram?

Relation de dépendance indique quu'un element client a connaissance d'un
autre element fournisseur et que toute modification du fournisseur peut
affecter le client. Représenté par une fleche pointillé entre les deux
classes.

> \- Give an example of a dependency relationship.

Client-\>fournisseur

> \- What is the difference between an operation and a method?

Opération: MDD, method DCC

> \- Where does one find operations in the various artifacts we have
> covered in this course?

DSS

Chapter 17 (16F) - GRASP - Designing Objects with Responsibilities

> \- What is the fundamental activity when doing object-oriented design?

Application de patron de conception

> \- What is a responsibility?

Abstraction de ce que les objets doivent faire.

> \- What are the two general types of responsibilities? Give examples
> of each.

Responsabilité de faire

Responsabilité de savoir

> \- What is a \"design pattern\"?

Répertoire de principes généraux et de solution idiomatiques qui les
guident lorsqu'ils créent des logiciels.

> \- Who is \"GoF\"?

Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides

> \- What does GRASP stand for?

General responsibility assignment software pattern.

> \- Name the 9 GRASP patterns.

Créateur, expert en information, faible couplage, controleur, forte
cohesion, polymorphisme, protection de variation, indirection,
Fabrication pure

> \- How does one apply the *Information Expert* pattern? Give an
> example.

Affecteur la reponsabilité à la classe qui détient l'information pour
s'acquiter de la responsabilité

> \- How does one apply the *Creator* pattern? Give an example.

La responsabilité de créer une classe incombe è la classe qui agrège,
contient, enregistre, utilise étroitement ou dispose des données
d'initialisation de la classe à créer

> \- What is *coupling*?

Affecter les reponsabilité de sorte que la relation entre les classe
reste failbe.

> \- What are the the benefits of *low coupling*?

Minimise l'impact des modifications d'une classe

> \- What is *cohesion*?

Affecter les responsabilité de sorte que la responsabilité de la classe
demeure forte

> \- What are the the benefits of *high cohesion*?

On s'assure qu'une classe n'a qu'une seule responsabilité ce qui
facilite la mise à jour du code

> \- How does one apply the *Controller* pattern? Give an example.

Affecter la responsabilité à une classe façade représnetant le système
globale, un objet racide, un équipement un sous-système majeure ou bien
un controlleur de session représentant un scenario de cas d'utilisation

> \- What are the two types of Controllers?

De façade ou de session

> \- How does one decide which type of Controller to use?

Façade: système globale, objet racine, équipement, sous-système majeure.

Session: un scenario de cas d'utilisation

> \- What is a *bloated controller*?

Un controlleur qui a une faible cohesion puique nous lui avons assigné
trop de responsabilité différentes.

> \- What is the connection between the system sequence diagrams and the
> Controller(s)?

Les operation du DSS sont implémenté par les contrôleur.

Chapter 18 (19F) - Object Design Examples with GRASP

> \- What is a *use case realization*?

C'est une description de la facon don't les cas d'utilisation sont
realises dans le modèle de conception, en termes d'objets qui
collaborent.

> \- What is an *initial domain object*?

Les operations système des DSS deviennent les messages initiaux pour les
objets contrôleur de la couche domaine.

> \- Why should one wait to do initialization design late?

Lors de l'impémentation, codez d'abord au moins un cas d'utilisation
d'initialisation. Mais , Durant la modélisation considérerz-le en
dernier, après avoir découvert ce qui doit réellement être créé et
initialisé. Puis concevez le cas d'initialisation pour prendre en charge
les besoins de réalisations des autres cas d'utilisation.

