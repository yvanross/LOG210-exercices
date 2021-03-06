
# Étude de cas jeBouquine

La société (fictive!) jeBouquine a décidé récemment de rejoindre les
rangs des grands libraires francophones en ligne. Les rayons déjà
ouverts sur le site web sont très divers: Informatique, Sciences et
techniques, Psychologie, Décoration et Jardinage. La librairie
jeBouquine assure également la distribution en langue anglaise d'une
large sélection d'ouvrages des plus grands éditeurs anglais et
américains. Par exemple, on trouve dans le rayon informatique des titres
venant de chez Addison-Wesley, McGraw-Hill, O'Reilly, Wiley, Wrox Press,
etc.

L'objectif fondamental du futur site
[www.jeBouquine.com](http://www.jebouquine.com) est de
permettre aux internautes de rechercher des ouvrages par thème, auteur,
mot-clé, etc., de se constituer un panier virtuel, puis de pouvoir les
commander et les payer directement sur le Web.

## Diagramme de cas d'utilisation

TODO

## Cas d'utilisations


### CU01-Maintenir le catalogue

**Acteur principal**

Le Libraire.

**Acteurs secondaires**

Les deux systèmes Nouveautés et Gestion des stocks.

**Objectifs**

Le Libraire veut pouvoir contrôler la mise à jour automatique du
catalogue des ouvrages présentés sur le site web.

**Préconditions**

-   Le Libraire s'est authentifié sur l'intranet (voir le cas
    > d'utilisation S'authentifier).

-   La version courante du catalogue est accessible.

**Postconditions**

Une nouvelle version du catalogue est disponible.

**Scénario nominal**

1.  Le système Nouveautés alimente le site avec les nouveaux ouvrages.

2.  Le système Gestion des stocks met à jour les données qui concernent
    > le prix et l'état du stock.

3.  Le Libraire valide la mise à jour du catalogue.

**Alternatives**

**1-2a** Le Système détecte un dysfonctionnement des systèmes externes
de mise à jour.

1.  Le Système signale le dysfonctionnement au Libraire.

2.  Le Libraire invalide la mise à jour partielle ou erronée et revient
    > à la version précédente du catalogue. Il prévient également le
    > Webmaster pour qu'il engage des actions de maintenance. Le cas
    > d'utilisation se termine en échec.

**3a** Le Libraire détecte des erreurs ou des incohérences parmi les
nouvelles informations.

1.  Le Libraire modifie toutes les informations erronées.

2.  Le Libraire valide la mise à jour du catalogue.

**3b** Le Libraire veut ajouter d'autres informations.

1.  Le Libraire exécute le cas d'utilisation Maintenir les informations
    > éditoriales.

2.  Le Libraire valide la mise à jour du catalogue.

**Exigences supplémentaires**

Le catalogue est mis à jour quotidiennement.

### CU02- Chercher des ouvrages

**Acteur principal**

L'Internaute (qu'il soit déjà client, ou simple visiteur)

**Objectifs**

L'Internaute veut trouver le plus rapidement possible un ouvrage précis
dans l'ensemble du catalogue. Il veut également pouvoir flâner comme il
le ferait dans une vraie bibliothèque et chercher des livres avec des
critères variés.

**Préconditions**

Le catalogue est disponible (voir le cas d'utilisation « Maintenir le
catalogue »).

**Postconditions**

L'Internaute a trouvé l'ouvrage précis qu'il cherchait, ou un ouvrage
qui l'intéresse, voire plusieurs.

**Scénario nominal**

1.  L'Internaute lance une gipomy rapide à partir de mots-clés: un
    > thème, un titre, le nom d'un auteur, etc.

2.  Le Système affiche une page de résultat. Les ouvrages sont classés
    > par défaut par date de parution, le plus récent en premier.

3.  L'Internaute sélectionne un ouvrage.

4.  Le Système lui présente une fiche détaillée pour l'ouvrage
    > sélectionné. On y trouvera en particulier:\
    > une image (pour la majorité des ouvrages),\
    > ses titre, sous-titre, auteur(s), éditeur, date de parution,
    > nombre de pages, langue,\
    > son prix et sa disponibilité,\
    > des éventuels commentaires de lecteurs déjà clients,\
    > la table des matières détaillée, des extraits de chapitres, etc.

**Alternatives**

**1a** L'Internaute n'a pas d'idée préconçue et préfère flâner dans les
rayons de la librairie virtuelle. Pour cela, le Système lui propose un
ensemble de pages telles que: *nouveautés, meilleures ventes, sélection
du libraire* (par thème).

1.  L'Internaute navigue dans ces pages et peut enchaîner sur l'étape 3
    > du scénario nominal.

**1b** L'Internaute choisit d'effectuer une recherche avancée.

1.  L'Internaute accède à un formulaire spécialisé lui permettant de
    > combiner plusieurs types de recherche: par sujet, titre, auteur,
    > éditeur, langue, etc. Il peut également saisir directement un
    > numéro ISBN, un code éditeur, etc.\
    > Il peut saisir seulement le début significatif d'un mot en
    > terminant par«\*». Le moteur de recherche cherchera tous les mots
    > commençant ainsi.\
    > Les suffixes de pluriel sont supprimés automatiquement pendant la
    > recherche. Ainsi, une recherche sur «programme» permettra de
    > trouver également «programmer» et «programmes».\
    > L'Internaute peut utiliser des opérateurs logiques entre les mots
    > de sa recherche. L'opérateur «ET» («AND») est utilisé par défaut.\
    > Par exemple, la recherche sur le titre «UML NON C++», combinée à
    > la recherche sur l'éditeur «CampusPress OU Eyrolles» retournera
    > les ouvrages dont le titre contient le mot «UML» mais pas le mot
    > «C++» et qui sont édités par CampusPress ou Eyrolles.

**2a** Le Système n'a pas trouvé d'ouvrage correspondant à la recherche.

1.  Le Système signale l'échec à l'Internaute et lui propose d'effectuer
    > une nouvelle recherche. Le cas d'utilisation redémarre à l'étape 1
    > du scénario nominal.

**2b** Le Système a trouvé de très nombreux ouvrages.

1.  Le Système signale le nombre d'ouvrages à l'Internaute et lui
    > affiche une première page de résultats. Les autres pages sont
    > accessibles directement ou par des symboles Suivante et
    > Précédente.

2.  L'Internaute navigue dans ces pages et enchaîne éventuellement sur
    > l'étape 3 du scénario nominal. Il peut également reclasser les
    > ouvrages obtenus par différents critères: titre, auteur, langue,
    > disponibilité, etc.

**3a** L'Internaute n'est pas intéressé par les résultats.

1.  L'Internaute revient à l'étape1 du scénario nominal pour lancer une
    > nouvelle recherche.

2.  L'Internaute abandonne la recherche. Le cas d'utilisation se termine
    > en échec.

**1** L'Internaute est intéressé par le résultat et met un ouvrage dans
lepanier.

1.  Le système affiche le panier de l'internaute (voir le cas
    > d'utilisation « Gérer son panier »).

**Exigences supplémentaires**

-   La recherche doit être la plus rapide possible: 95% des requêtes
    > doivent aboutir en moins de 3s.

-   Les résultats de la recherche doivent être pertinents, c'est-à-dire
    > correspondre à la requête dans au moins 99% des cas.

-   Le formulaire de recherche rapide doit être toujours visible et donc
    > se situer dans la partie supérieure de toutes les pages, quelle
    > que soit la résolution d'écran de l'Internaute.

### CU03-Gérer son panier

**Acteur principal**

L'Internaute (qu'il soit déjà client, ou simple visiteur).

**Objectifs**

Lorsque l'Internaute est intéressé par un ouvrage, il faut qu'il puisse
l'enregistrer dans un panier virtuel. Ensuite, il doit pouvoir ajouter
d'autres livres, en supprimer ou encore en modifier les quantités avant
de passer commande.

**Préconditions**

Néant.

**Postconditions**

Néant.

**Scénario nominal**

1.  L'Internaute enregistre les ouvrages qui l'intéressent dans un
    > panier virtuel (voir le cas d'utilisation « Chercher des
    > ouvrages »).

2.  Le Système lui affiche l'état de son panier. Chaque ouvrage qui a
    > été préalablement sélectionné est présenté sur une ligne, avec son
    > titre, son auteur et son éditeur. Son prix unitaire est affiché,
    > la quantité est positionnée à «1» par défaut, et le prix total de
    > la ligne est calculé. Le total général est calculé par le Système
    > et affiché en bas du panier, avec le nombre d'articles.

3.  L'Internaute continue ses achats (voir le cas d'utilisation
    > « Chercher des ouvrages »).

**Alternatives**

**2a** Le panier est vide.

1.  Le Système affiche un message d'erreur à l'Internaute («Votre panier
    > est vide») et lui propose de revenir à une recherche d'ouvrage
    > (voir le cas d'utilisation « Chercher des ouvrages »).

**4a** L'Internaute modifie les quantités des lignes du panier, ou en
sup-prime.

1.  L'Internaute revalide en demandant la mise à jour du panier.

2.  Le cas d'utilisation reprend à l'étape 2 du scénario nominal.

**4b** L'Internaute demande un devis pour commander par courrier.

1.  Le Système fournit un devis imprimable à joindre au règlement
    > récapitulant la commande et le total à payer.

**1** L'Internaute souhaite commander en ligne.

1.  Le Système l'amène sur la page d'identification.

**2a** L'Internaute s'identifie en tant que Client (voir le cas
d'utilisation « S'authentifier »).

**2b** L'Internaute Visiteur demande à créer un compte client (voir le
cas d'utilisation « Créer un compte client »).

**Exigences supplémentaires**

-   Le calcul du total doit toujours être exact.

-   Le panier de l'Internaute est sauvegardé pendant toute la durée de
    > sa visite sur le site web.

### CU04- Effectuer une commande

**Acteur principal**

Le Client.

**Objectifs**

À tout moment, le client doit pouvoir accéder au formulaire du bon de
commande, dans lequel il peut saisir ses coordonnées et les informations
nécessaires au paiement et à la livraison.

**Préconditions**

Le panier du client n'est pas vide et il s'est identifié.

**Postconditions**

-   Une commande a été enregistrée et transmise au service Commandes

-   Une transaction cryptée a été réalisée avec le système externe de
    > Paiement sécurisé et sauvegardée.

**Scénario nominal**

1.  Le Client saisit l'ensemble des informations nécessaires à la
    > livraison, à savoir:\
    > les coordonnées de l'adresse de facturation (nom, prénom,
    > adresse postale complète, téléphone),\
    > les coordonnées de l'adresse de livraison si elle est différente
    > de l'adresse de facturation (nom, prénom, adresse postale
    > complète, téléphone).

2.  Le Système affiche un récapitulatif des adresses indiquées et du
    > panier à commander.

3.  Le Client sélectionne le paiement par carte bancaire et valide sa
    > commande. Il doit pour cela fournir un numéro de carte de crédit
    > avec son type, sa date de validité et son numéro de contrôle.

4.  Le Système envoie les informations cryptées au système externe de
    > Paiement sécurisé.

5.  Le Paiement sécurisé autorise la transaction.

6.  Le Système confirme la prise de commande au Client.

7.  Le Système envoie la commande validée au Service clients de
    > jeBouquine.

8.  Le Système enregistre la commande.

**Alternatives**

**1-3a** Le Client annule sa commande.

1.  Le Système revient sur l'affichage du panier et le cas d'utilisation
    > se termine en échec.

**1** Le Client choisit un paiement différé (chèque, etc.).

1.  Le Système confirme la prise de commande à l'Internaute et lui
    > indique la démarche à suivre pour la terminer.

2.  Le Système enregistre la commande dans un état «non finalisée».

**4a** Le Système détecte que les informations sur la carte sont
incomplètes ou erronées (date de validité dépassée, etc.).

1.  Le Système demande au client de modifier ou compléter les
    > informations sur la carte.

2.  Le cas d'utilisation reprend à l'étape3 du scénario nominal.

**5a** Le Paiement sécurisé n'autorise pas la transaction ou ne répond
pas.

1.  Le Système indique au Client que le paiement par carte bancaire a
    > échoué et propose de choisir un autre type de paiement.

2.  Le cas d'utilisation reprend à l'étape3 du scénario nominal.

**Exigences supplémentaires :**

-   Pour garantir la sécurisation et la confidentialité des échanges, il
    > est impératif que l'envoi des données se fasse de manière cryptée
    > (protocole SSL).

-   Les seules cartes bancaires acceptées sont les Visa,
    > Eurocard-Mastercard et AmericanExpress.


