---

<!-- .slide: id="abstract-factory" -->
### Le patron « Abstract Factory »

--

- Un niveau d’abstraction plus haut que « Factory Method »
- « Abstract Factory » retourne des objets d’un groupe de classes
- Application typique : supporter plusieurs interfaces utilisateur graphique (IUG)
  - p. ex.: Windows 9x, Motif (Linux), et Macintosh

--

## GUI Factory
- Deux degrés de liberté
- le type de Gui—Win9x, Motif, Mac
- les éléments dans le GUI—boutons, cases à cocher, etc.
- Depuis Java 1.2, il existe les classes « Pluggable Look and Feel » (PLAF)

--

### Référence
![Picture 2]()
![image](/assets/LOG210-08-04-patron-abstract-factory.pptx/image1.png)

<img width='100' height='100' data-src=''>Picture 2</img>

--

![Picture 3]()
![image](/assets/LOG210-08-04-patron-abstract-factory.pptx/image2.emf)

<img width='100' height='100' data-src=''>Picture 3</img>

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF