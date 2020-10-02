---

<!-- .slide: id="commande" -->
# Le patron « commande »

--

## Commande - Synopsis
- Encapsule une requête dans un objet
- Les clients peuvent facilement traiter différentes requêtes
- emmagasiner les requêtes pour traitement ultérieur (queue, séquencement)
- garder une trace des requêtes (log)
- supporter l'annulation des requêtes (undo, redo, play)

--
## Exemple de contexte
- Application de traitement de texte
- Commandes
  - qui peuvent être annulées
  - qui sont liées à des menus ou boutons

---

## Contexte (suite)

![Picture 4]()
![image](/assets/LOG210-08-04-patron-commande.pptx/image1.png)

<img width='100' height='100' data-src=''>Picture 4</img>

--

## Forces
- Contrôler les commandes
  - mise en séquence
  - sélection
  - timing
  - Pouvoir annuler (undo) et répéter (redo) les commandes
  - grouper des commandes (agrégation)

--

## Forces (suite)
- Maintenir un journal (log) des commandes exécutées
- annuler plusieurs commandes (multiple undo)
- annuler les commandes d'une transaction cancellée en cours de traitement
- reprise en cas de panne
- langages de script, macros clavier

--

## Solution

![Picture 4]()
![image](/assets/LOG210-08-04-patron-commande.pptx/image2.png)

<img width='100' height='100' data-src=''>Picture 4</img>

---

## Conséquences
- L’objet qui lance une commande est différent que l’objet qui exécute la commande
- Mettre une requête dans un objet
- permet de manipuler une requête aussi facilement qu'un objet
- Rajouter de nouvelles commandes est normalement facile

--

## Implémentation
![Picture 1031]()
![image](/assets/LOG210-08-04-patron-commande.pptx/image3.wmf)

<img width='100' height='100' data-src=''>Picture 1031</img>

--
## Implémentation (suite)
- Décider quelles sont les commandes
- S’il y a un grand nombre de commandes les classifier dans une hiérarchie (comme des classes/sous-classes)

---
## Implémentation (suite)
- Comment annuler (undo) une commande?
- information additionnelle requise
- objet(s) que la commande affecte
- arguments de l'opération
- valeurs originales
- etc.
- Voir [Grand98] pour plus de détails

---
## Commande
- Java API usage
  - javax.swing.AbstractAction
  - actionPerformed()
    - demande l'exécution
- Client : menu ou bouton
- Commande : sous-classe de AbstractAction
- Receiver : encapsulé dans la commande
- 
---

## Commande
- Exemple de code
- abstract class Command
- {
-   abstract public void execute();
-   abstract public void undo();
- }

---

## Exemple de code (suite)
- class OpenCommand extends Command
- {
-   private Application app;
-   private Document doc;
-   public OpenCommand(Application a) {
-     app = a;
-   }
- ...



---

## Exemple de code (suite)
- class OpenCommand extends Command
- {
- ...
-   public void execute() {
-     String name = UI
- .
- getFileName();
-     doc = new Document(name);
-     app.add(doc);
-     doc.open();
-   }
- ...

--

- Exemple de code (suite)
- class OpenCommand extends Command
- {
- ...
-   public void undo() {
-       doc.close();
-       app.remove(doc);
-   }
- }

--

## Patrons associés
  - Factory
    - pour faire une couche entre l'interface usager et les classes Commande
  - Composite
    - pour les commandes composées de plusieurs commandes

--

## Patrons associés (suite)
- Memento / Snapshot
  - pour le undo
- Prototype
  - pour les commandes qui doivent être copiées avant d'être mise dans un journal

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF