---

<!-- .slide: id="iterateur" -->
# Le patron « Iterator »


--

## « Iterator » : Synopsis
- Permet l'encapsulation de l'itération dans une hiérarchie de classe
    - Mécanique de parcours d'un agrégat est cachée au client
    - Permet des itérations polymorphes
    - Permet différents types de parcours pour un même type d'agrégat

--

## Exemple
- Télécommande
![telecommande](/assets/LOG210-08-04-patron_iterateur.pptx/telecommande.png)

--
## Exemple
- Patients
![patient](/assets/LOG210-08-04-patron_iterateur.pptx/patient.png)

--

## « Iterator »: Motivation
- Une classe a besoin d’accès au contenu d’une collection sans devenir dépendante de la classe qui est utilisée pour implémenter la collection
- Une classe a besoin d’une façon uniforme (polymorphique) d’accéder au contenu de plusieurs collections

--

## «Iterator»: Contexte
On veut créer des classes qui permettent de voir l’inventaire d’un entrepôt
![iterator-contexte](/assets/LOG210-08-04-patron_iterateur.pptx/iterator-contexte.png)

--

## « Iterator » : Solution
![iterator-solution](/assets/LOG210-08-04-patron_iterateur.pptx/iterator-solution.png)

--

## «Iterator»: Conséquences
- Permet de parcourir un agrégat sans connaître sa structure interne
- Permet de parcourir de différentes manières un même agrégat
- Permet d’accéder à une collection d’objets sans en connaître la source

--

## «Iterator» : Conséquences (suite)
- L'agrégat peut être obligé d'exporter des méthodes uniquement pour que les itérateurs puissent fonctionner
- Possible d’avoir plusieurs types d’objet itérateur pour la même collection

--

## « Iterator » : Utilisation dans l’API de Java
- Les classes dans le paquetage **java.util**  suivent ce patron
- L’interface **Collection**  joue le rôle de « CollectionIF »
- Quelques classes qui implémentent **Collection**
    - HashSet, TreeSet
    - ArrayList , LinkedList

--

## « Iterator »
### Implémentation en Java
- Dans les collections Java
    - Interface Iterator
- Classe qui implémente cette interface est une classe interne («inner  class») de la collection concrète
    - Une classe dans une classe
    - Peut accéder à tous les membres de la classe enveloppante

--

## Exemple : InventoryIterator
```java
public class InventoryCollection {
     ...
     /** Return an Iterator for this object.  */
     public InventoryIteratorIF iterator() {
         return new InventoryIterator();
     }
     private class InventoryIterator implements InventoryIteratorIF {
         public boolean hasNextInventoryItem() {
             ...
         }
         public InventoryItem getNextInventoryItem() {
             ...
         }
         public boolean hasPrevInventoryItem() {
             ...
         }
         public InventoryItem getPrevInventoryItem() {
             ...
         }
     } // class InventoryIterator
     ...
 } // class InventoryCollection
```
--

## Exemple: InventoryIterator (suite)
```java
 public interface InventoryIteratorIF {
     public boolean hasNextInventoryItem() ;
     public InventoryItem getNextInventoryItem() ;
     public boolean hasPrevInventoryItem() ;
     public InventoryItem getPrevInventoryItem() ;
 }
 /**
  * Instances of this class describe an inventory item
  */
 public class InventoryItem {
     //...
 }

```

--

## Références
[Grand98]	–	Patterns in Java, Vol. 1
[GoF95]	–	Design Patterns

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF
