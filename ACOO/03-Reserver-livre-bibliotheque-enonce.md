# Réserver un livre à la bibliotheque

# Diagramme de cas d'utlisation
![](03-Reserver-livre-bibliotheque/DCU.svg)
# Cas d’utilisation - Réserver un livre de la bibliothèque
**Parties prenantes et intérêts :** 
 - Le **Membre**. Il veut un moyen de recherche exact et rapide et ne veut pas que la Bibliothèque mémorise des informations sur ses recherches (confidentialité). Il veut pouvoir réaliser des réservations aisément, obtenir un service rapide en fournissant un minimum d’efforts. Il veut également une preuve de réservation.
 - La **Bibliotheque**. Elle veut enregistrer correctement les réservations et satisfaire les souhaits des membres. 

**Préconditions :** Le Membre est identifié et authentifié

**Acteur principal :** Membre
1. Le membre choisit la fonction « recherche » et saisit du texte décrivant le livre 1. (par exemple, une partie du titre, « UML »).
1. Le système affiche une liste de livres (le titre, l’auteur et l’année) 1. correspondant à la recherche, par exemple, « UML2 et les design patterns, Craig 1. Larman, 2005 » et « UML par la pratique, Pascal Rocques, 2009 ».
1. Le membre choisit un livre parmi les résultats, par exemple, « UML2 et les design 1. patterns, Craig Larman, 2005 ».
1. Le système affiche les informations détaillées du livre (le titre, l’auteur, le 1. numéro ISBN, la maison d’édition, le numéro de l’édition et l’année) ainsi que la 1. liste de tous les exemplaires du livre indiquant s’ils sont disponibles ou pas, 1. par exemple, deux exemplaires du livre « UML2 et les design patterns », un avec 1. l’identificateur d’exemplaire « 1 » qui est disponible et un avec 1. l’identificateur d’exemplaire « 2 » qui n’est pas disponible.
1. Le membre réserve un exemplaire du livre qui est disponible.
1. Le système confirme la réservation en affichant un numéro de réservation avec le 1. nom du membre et le code de l’exemplaire du livre.

**Extensions (scénarios alternatifs) :**
2. Aucun livre ne correspond au texte de la recherche. 
- Le système affiche un message indiquant qu’aucun livre n’a été trouvé.
- Le membre lance une nouvelle recherche.
4. Tous les exemplaires ne sont pas disponibles. 
- Le système affiche toutes les informations du livre et des exemplaires, mais un message indique qu’il n’est pas possible de réserver, faute d’exemplaires disponibles.
- Le membre lance une nouvelle recherche.
