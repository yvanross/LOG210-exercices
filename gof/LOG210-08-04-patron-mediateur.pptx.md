---

<!-- .slide: id="mediateur" -->
# Patron "Médiateur"

--

## « Mediator »
- Communication entre plusieurs classes devient difficile à gérer, couplage élevé
- Classe « médiatrice », elle seule, connaît la complexxté de chaque classe
- Communication entre les classes à travers la classe médiatrice

--

- Exemple : programme simple (pourtant complexe)

![Picture 13]()
![image](/assets/LOG210-08-04-patron-mediateur.pptx/image1.png)

<img width='100' height='100' data-src=''>Picture 13</img>

--

##Exemple : simplifié avec une classe médiatrice
- Mediator.java
- {ExempleMediator}

![Picture 4]()
![image](/assets/LOG210-08-04-patron-mediateur.pptx/image2.png)

<img width='100' height='100' data-src=''>Picture 4</img>





--

## ordre d’initialisation
- Programme principal crée le médiateur
- Passe le médiateur à tous les collègues dans leur constructeur
  - CopyButton, KidList, KTextField, etc.
- Chaque collègue s’inscrit chez le médiateur



--

## méthodes
- Chaque opération, ex : move, clear, select
- Inscription (ex : registerText)

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF
