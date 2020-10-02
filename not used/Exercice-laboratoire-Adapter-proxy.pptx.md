---
theme : beige
transition: slide
highlightTheme: monokai
logoImg: logo.png
slideNumber: true
title: Exercices

---

## Exercice Disponibilité #1
- Proposer une exigence (raisonnable) du laboratoire pour la fiabilité du mécanisme de calcul des horaires
- p.ex. 	pour tolérer une panne d'une partie de la solution.
- Imaginer une conception qui puisse répondre ‡ cette exigence.
- Y a-t-il des patrons GoF?

---

## Exercice Disponibilité #2
- Proposer une exigence (raisonnable) du laboratoire pour la disponibilité du mécanisme de sauvegarde des horaires,
- p.ex. 	pour tolérer une panne d'une partie de la solution.
- Imaginer une conception qui puisse répondre ‡ cette exigence.
- Y a-t-il des patrons GoF?

---

## Rappel – adaptateurs
![larman/F23.1](/assets/larman/F23.1.png)

fig. F23.1, A26.1

---

## Rappel – adaptateurs
- FabriqueDeServices retourne un adaptateur pour accéder  aux variantes de services BD Produits

![fabriqueService](/assets/06-Exercice-laboratoire-Adapter-proxy.pptx/fabriqueService.png)

---

## Rappel – adaptateurs
- FabriqueDeService  retourne  un adaptateur pour  accéder à la BD Produits

![localCache](/assets/06-Exercice-laboratoire-Adapter-proxy.pptx/localCache.png)

---


## Design de recouvrement
![larman/F30.1, A35.1](/assets/larman/F30.1.png)

---

## Design de recouvrement (Création)
![larman/F30.2, A35.2](/assets/larman/F30.2.png)

---

## Design de recouvrement (enterItem)
![F30.3, A35.3](/assets/larman/F30.3.png)

---

## Design de recouvrement (enterItem…)
![larman/F30.4, A35.4](/assets/larman/F30.4.png)

---

## Patron Proxy (GoF)
- Problème
    - l’accès direct à un objet est impossible (ou est indésirable). Que faire?
- Solution
    - Utiliser un objet proxy qui est un substitut à un objet
    - Le proxy implémente la même interface
    - Cela ajoute un niveau d’indirection

---

## Proxy
![proxy](/assets/06-Exercice-laboratoire-Adapter-proxy.pptx/proxy.jpeg)

ref: Design Patterns, Gamma, Helm, Johnson &amp; Vlissides, 1995


---

## Patron Proxy (GoF)
![larman/F30.12, A35.12](/assets/larman/F30.12.jpeg)

---

## Les Proxy dans PoS
![larman/F30.13, A35.13](/assets/larman/F30.13.png)

---

## Cohérence du cache
- Ajout réservation
- Modification réservation
- Destruction réservation
