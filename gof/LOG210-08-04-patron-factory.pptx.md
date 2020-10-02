---

<!-- .slide: id="factory" -->
# Patron « Factory Method » 

--

## Synopsis
- Lorsqu'un algorithme a besoin de créer un objet « A » dont la classe concrète est variable suivant le contexte Factory Method propose la délégation de l’instanciation de « A »

--
## Synopsis (suite)
- Une classe est destinée pour la réutilisation avec des types arbitraires par exemple un framework
- Elle doit pouvoir instancier des objets d’autres classes, sans dépendre de ces dernières
  - Le choix de la classe à instancier est délégué à un autre objet (la factory)
- On fait référence au nouvel objet via une interface commune

--

## Exemple très simple
- La méthode toString()
  - cela retourne un nouvel objet
  - on ne fait pas de « new »
  - on ignore comment l’objet est créé

--

## Exemple très simple
- Forme f;
- …
 // pour UTILISER l’objet,
 // quel que soit son type
 f.dessine();
- On exploite le polymorphisme afin de séparer le code spécifique de certaines méthodes du reste du système.
- Le polymorphisme est bien pour l’utilisation d’un objet, mais cela n’aide pas toujours pour sa création.

--

## Contexte Exemple #1 (suite)
- Le client qui crée l’objet dépend de l’interface de l’objet crée, par ex:
<code>
Forme f = new
Cercle(x,y,r);
</code>

UtilisateurForme
Forme
dessine()
Cercle
dessine()
Carré
dessine()
Rectangle
dessine()
CréateurForme
</code>


--

## Contexte Exemple #1 (suite)
- Cette dépendance pose des problèmes potentiels.
- Utilisation de « new » dans plusieurs modules du système
- Impact important si le format du constructeur change
- Si on rajoute une nouvelle sous-classe
- doit rajouter le nouveau constructeur quelque part
- peut-être à plusieurs endroits
- Quel que soit l’endroit où on crée un objet de l’une des sous-classes dépend (trop) de l’interface de son constructeur (couplage)

--

##Contexte Exemple #2
- Contexte :
- Concevoir un Framework pour les applications de bureautique [Grand2002] 
- AbstractDocument
- getTitle
- ...
- MyDocument
- newDocument
- openDocument
- ...
- Application
- newDocument
- openDocument
- ...
- Edits
- *
- 1
- «interface»
- DocumentIF
- getTitle
- newDocument
- openDocument
- ...

--

## Contexte Exemple #2 (suite)
- Comment créer un document dans l’application sans avoir une dépendance directe entre les deux classes?
- AbstractDocument
- getTitle
- ...
- MyDocument
- newDocument
- openDocument
- ...
- Application
- newDocument
- openDocument
- ...
- Edits
- *
- 1
- «interface»
- DocumentIF
- getTitle
- newDocument
- openDocument
- ...
- Creates

--

## Forces
- Une classe doit être capable d’initier la création d’objets sans avoir les dépendances sur la classe de l’objet créé
- L’ensemble des classes qu’une classe « utilisateur » pourrait instancier n’est pas statique
- il y a le potentiel d’avoir de nouvelles classes

--

## Solution
- Contexte de l’exemple #2



---


## Solution, Exemple #3
**Contexte** : Paiement par carte de crédit
- Deux configurations possibles pour le système « PointOfSale »
  - BancOne
  - Wells Fargo
- le traitement dépend de la configuration
- BancOneCCFactory
  - createProcessor( ) :CreditCardProcessorIF
- PointOfSale
- «interface»
  - CreditCardProcessorIF
  - processCharge
  - processCredit
  - ...
- WellsCC
  - operation1
  - operation2
  - ...
- Uses
- «interface»
- CreditCardProcessorFactoryIF
- createProcessor( ) :CreditCardProcessorIF
- Requests-creation
- requestor
- creator
- *
- Creates
- *
- BancOneCC
- operation1
- operation2
- ...
- WellsCCFactory
- createProcessor( ) :CreditCardProcessorIF
- 3
- Creates



---

## Solution générale
- ProductIF – tous les objets créés avec ce patron doivent implanter cette interface
- ConcreteProduct1… - classes instanciées par le Factory
- FactoryIF – interface indépendante de l’application permettant d’avoir plusieurs Factory si nécessaire
- Factory – classe spécifique à l’application qui instancie les objets selon le « descriminator »

![Picture 7]()
![image](/assets/LOG210-08-04-patron-factory.pptx/image1.png)

<img width='100' height='100' data-src=''>Picture 7</img>





---

## Conséquences
- Deux variantes
- méthodes dans une classe de base redéfinit dans les sous-classes pour créer le type approprié
  - exemple : toString()
- méthode permettant de créer différents types d’objets selon le contexte
  - exemple : createDocument()


--

Conséquences
- La classe « CreationRequester » est indépendante des classes d’objets « ConcreteProduct » créés.
- L’ensemble des classes « ConcreteProductX » peut changer dynamiquement.
- La logique du Factory peut être difficile à comprendre pour le programmeur qui maintient le code (celui qui n’a pas fait la conception).


--

## Implémentation
- Si toutes les classes « ConcreteProduct » sont connues à l’avance, la méthode « createProduct » est simple :
<code>
 Image createImage (String ext) {
   if (ext.equals("gif"))
     return new GIFImage();
   if (ext.equals("jpg"))
     return new JPGImage();
   // ...
 }
</code>

--

##Implémentation (suite)
- Si les classes « ConcreteProduct » ne sont pas connues à l’avance, la méthode « createProduct » est plus compliquée (utilise réflexion) :
<code>
public static final Shape createShape(String id) {
  if(!factories.containsKey(id)) {
   try {

 Class factoryClass  = Class.forName("c05.shapefact2." + id);

factories.addFactory(id,
factoryClass.newInstance()
);
  } catch(Exception e) {
   throw new RuntimeException("Bad shape creation: " + id);
 }
 return ((ShapeFactory)factories.get(id)).create();
}
</code>


--

## Utilisation dans l’API de Java
- La méthode «getContent» de la classe «URLConnection» retourne l’objet qui correspond au contenu de l’URL (image GIF, etc.)
- http://java.sun.com/j2se/1.3/docs/api/java/net/URLConnection.html#getContent()

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF
