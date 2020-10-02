---
theme : beige
transition: slide
highlightTheme: monokai
logoImg: logo.png
slideNumber: true
title: Exercice diagrammes d’interaction

---

# LOG210
## Exercice diagrammes d’interaction

---

## Révision du pattern Observateur
- Référence: Freeman, Eric; Robson, Elisabeth; Bates, Bert; Sierra, Kathy (2004-10-25). “Head First Design Patterns.” O'Reilly Media.

![image5](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image5.png){width=85%}{style=border:none}

---


## Révision du pattern Observateur
![addObserver](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/addObserver.jpeg)
![image9](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image4.png)

![subject-addObserver](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image4.png){width=45%}
![class-subject](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/class-subject.png){width=45%}

---

## Révision du pattern Observateur
- Faire  un diagramme d’interaction pour la dynamique démontrée ici (4 messages, chacun envoyé à un objet)

![image11](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image11.png){width=45%}{style=border:none}
![image12](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image12.png){width=45%}{style=border:none}

---

## Révision du pattern Observateur
- Faire  un diagramme d’interaction pour la dynamique démontrée ici (boucle avec objets de type ArrayList```<Observer>```)

![image11](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image11.png){width=45%}{style=border:none}
![ds-update](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/ds-update.png){width=45%}{style=border:none}

---
## Révision du pattern Observateur

![remove](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/remove.png){width=30%}{style=border:none}
![left](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/left.png){width=15%}{style=border:none}
![removed](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/removed.png){width=30%}{style=border:none}

![removeObserver](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/removeObserver.png)

---

## Révision du pattern Observateur
- L’objet Mouse ne reçoit pas le message « 14 » parce qu’il n’implémente plus l’interface « Observer »
    - Vrai
    - Faux
    
![image19](/assets/06-chp14F-Exercice_Diagrammes_interaction_+_Observer-Fuhrman_7.pptx/image19.png){style=border:none}


