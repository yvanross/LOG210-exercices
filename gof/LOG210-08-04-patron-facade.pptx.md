---

<!-- .slide: id="facade" -->
# Patron "Façade"
- E. Gamma, R. Helm, R. Johnson et J. Vlissides.
- Design Patterns : Elements of Reusable Object Oriented Software
- . Addison-Wesley, 395 pages, 1995.

![Picture 4]()
![image](/assets/LOG210-08-04-patron-facade.pptx/image1.png)

<img width='100' height='100' data-src=''>Picture 4</img>

--
## Contexte / Problème
- besoin d’une interface commune
- implémentation peut changer
- ensemble d’implémentations différentes
- couplage non souhaitable à plusieurs composants dans le système

--
## Solution
- un seul point de contact au sous-système
- objet façade qui englobe le sous-système
- objet façade représente une seule interface
responsable de collaborer avec les composants du sous-système

--
## Exemple
- E. Gamma, R. Helm, R. Johnson et J. Vlissides.
- Design Patterns : Elements of Reusable Object Oriented Software
- . Addison-Wesley, 395 pages, 1995.

![Picture 4]()
![image](/assets/LOG210-08-04-patron-facade.pptx/image2.png)

<img width='100' height='100' data-src=''>Picture 4</img>

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF