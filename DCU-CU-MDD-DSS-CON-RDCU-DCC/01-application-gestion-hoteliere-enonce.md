
# Application de gestion hotelière
Le propriétaire d’un petit hôtel désire se doter d’une application pour gérer les réservations et les séjours de ses clients. Il ne veut pas que l’application s’occupe de la facturation. La figure 1 illustre les tâches accomplies par un commis à la réception. Vous devez analyser et concevoir une application permettant de noter les réservations, démarrer les séjours et transférer les séjours de chambre.
# Diagramme de cas d'utilisation

![DCU](https://www.plantuml.com/plantuml/svg/TL0x3i8m3DrpYYSMfafyTWGgCmlb024rRI1jAZjXGTm7pj6BaLP2AWERt_FxMDvAq1nYux3FJyhH9I1uiAtgWD8ocM1zgpfjRheYp7PTvwpH0ucIK96CO-q3ETk_c6PuA4GXeoN9yzDYcHtIaX5R0fCGtrFVQ9yFb51q15FhvZoOjU3mwr_zzHCw5yLIP87qxwkFF0OSVmFMMS6wbKl_vZ7cgnq2fhs5Wdggt3UD5MJP9Xqo0SSfADIMsZ8zxGC0 "DCU")
# CU01-Cas d'utilisation «Noter une réservation»
**Pré(s) condition(s) :**
•	Le commis est authentifié.
**Post condition(s) :**
•	Une réservation est inscrite dans le système.
**Acteur principal:**
•	Le commis à la réception (commis).

**Scénario principal**
1.	Un client appelle à l'hôtel pour placer une réservation.
2.	Le commis démarre une nouvelle réservation.
3.	Le commis entre:
i.	La date d'arrivée;
ii.	La date de départ;
iii.	Le nom de la catégorie de chambre;
iv.	La quantité de chambres.
6.	Le système affiche toutes les informations entrées.
7.	Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
8.	Le système enregistre la réservation et affiche le numéro de confirmation.
9.	Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**
*. En tout temps, le commis annule la réservation.
1.	Le système supprime la réservation.
2.	Fin du cas d'utilisation.

3a. Il n'y a pas assez de chambres de la catégorie choisie pour la période entrée.
1.	Le système affiche un message d'avertissement.
2.	Le système affiche les disponibilités de toutes les catégories pour la période entrée.
3.	Le commis communique les disponibilités au client.
4.	Retour à 3.

#### CU01-Réservation simple
Jean Hernandez appelle à l'hôtel pour réserver une chambre.
Le commis entrera:
Le 2011-06-01 comme date d'arrivée
Le 2011-06-02 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation en entrant le nom du client et communiquera le numéro de confirmation à monsieur Hernandez.

## Interfaces usagé

## CU01-Modèle du domaine

## Diagramme de séquence système

## Contrats

## RDCU's

## Diagramme de classe


# CU02 - Noter une réservation avec plusieurs chambres
**Pré(s) condition(s) :**
- Le commis est authentifié.
  
**Post condition(s) :**
- Une réservation est inscrite

**Acteur principal:**
- Le commis à la réception (commis).

**Scénario principal**
1. Un client appelle à l'hôtel pour placer une réservation.
1. Le commis démarre une nouvelle réservation.
1. Le commis entre:
   1. La date d'arrivée;
   2. La date de départ;
   3. Le nom de la catégorie de chambre;
   4. La quantité de chambres.
1. Le système inscrit les informations à la réservation.

Les étapes 3 et 4 sont répétées tant que le client n'indique pas qu'il a terminé.

5. Le commis termine la réservation.
1. Le système affiche toutes les informations entrées.
1. Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
1. Le système enregistre la réservation et affiche le numéro de confirmation.
1. Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**
*. En tout temps, le commis annule la réservation.
  1. Le système supprime la réservation.
  2. Fin du cas d'utilisation.

3a. Il n'y a pas assez de chambres de la catégorie choisie pour la période entrée.
  1. Le système affiche un message d'avertissement.
  1. Le système affiche les disponibilités de toutes les catégories pour la période entrée.
  1. Le commis communique les disponibilités au client.
  1. Retour à 3.




#### CU02-Réservation d'affaires
Jean Hernandez appelle à l'hôtel pour réserver deux chambres identiques, mais pour des périodes légèrement différentes. Son collègue, Patrice Retardataire, arrivera une journée après Jean.
Le commis entrera d'abord:
2011-08-02 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-08-03 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.

#### CU03-Réservation budgétaire
Jean Hernandez planifie des vacances avec son fils. Il appelle à l'hôtel pour réserver deux chambres de catégorie différente pour la même période.
Le commis entrera d'abord:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Standard" comme catégorie de cham¬
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.


## Interfaces usagé

## Évolution du Modèle du domaine


Cette version sous entends que les Catégories sont les même pour tous les Hotels.  Si ce   n’étais pas le cas, on associe Hotel à Catégorie et on enlève l’association entre Hotel et Chambre.

Catégorie peut être traité comme une classe de description ou un catalogue selon le sens par lequel nous utilisons les classes.  
Plusieurs chambres sont décrite par une catégorie (Classe de description)
Une Catégorie (Catalogue) contient plusieurs Chambre.




## Diagramme de séquence système

## Contrats

## RDCU's


## Diagramme de classe

# CU03-Transférer un séjour de chambre
**Précondition(s) :**
- Le commis est authentifié.

**Postcondition(s) :**
- Le séjour se poursuit dans une autre chambre.

**Acteur principal :** Le commis à la réception

**Scénario principal**
1. Un client désire occuper une chambre différente pour le reste de son séjour.
1. Le commis entre le numéro de chambre dans laquelle le client séjourne.
1. Le système affiche le séjour ainsi que toutes les chambres disponibles de la même catégorie.
1. Le commis informe le client des chambres disponibles puis sélectionne celle que le client préfère.
1. Le système modifie la ligne courante du séjour et inscrit une nouvelle ligne au séjour pour la nouvelle chambre.
1. Le commis remet la clé de la chambre au client et lui indique l'emplacement de la chambre dans l'hôtel.

**Scénarios alternatifs**
3a. Il ne reste plus de chambres disponibles dans la catégorie réservée.
Le système affiche les chambres disponibles pour toutes les catégories.
Retour à 4


## Évolution du MDD

## DSS 

## Contrat's 


## RDCU's

## DCU

# Autre exercoces

### CU01-Exercices-Notez une réservation
1. Représentez le fait qu’un Client est responsable d’une Réservation.
1. Représentez le fait qu’une Réservation peut avoir plusieurs Ligne de Réservation.
1. Représentez le fait qu’une Catégorie de chambre regroupe plusieurs Chambres.
1. Est-il nécessaire d’associer un Client à une Chambre? Justifiez la réponse.
1. Représentez le fait qu’un Client désire occuper une Chambre d’une catégorie précise 1. durant la première fin de semaine de mois de juillet. Justifiez les associations à 1. l’aide d’un verbe exprimant la raison d’être de l’association. Indiquez les 1. attributs des classes conceptuelles.
2. Représentez le fait qu’un Commis a confirmé la Réservation à l’aide des 1. informations personnelles (nom et numéro de téléphone) du Client. Justifiez les 1. associations à l’aide d’un verbe d’action. Indiquez les attributs nécessaires.
3. Bâtissez le modèle du domaine partiel du système de l’hôtel. Justifiez les 1. associations à l’aide d’un verbe. Indiquez tous les attributs pertinents


### CU01-CU02-Exercices-RDCU

1. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une réservation. Annotez votre solution des principes GRASP.
 
2. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une ligne de réservation. Annotez votre solution des principes GRASP.
 
3. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’associer une ligne de réservation à une catégorie de chambre. Annotez votre solution des principes GRASP.
 
4. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de stocker une réservation. Annotez votre solution des principes GRASP.
 
5. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de repérer une réservation à partir de son numéro de confirmation. Annotez votre solution des principes GRASP.
 
 1. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de créer un client tout en l’associant à une nouvelle réservation. Annotez votre solution des principes GRASP.
 
6. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de détruire une réservation appartenant à un client. Annotez votre solution des principes GRASP.
 
7. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’imprimer une facture incluant l’information sur une réservation, ses lignes de réservation et les catégories de chambres associées.  Annotez votre solution des principes GRASP.

