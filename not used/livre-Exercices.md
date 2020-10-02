---
theme : "sky"
transition: "convex"
highlightTheme: "github"
title: "Séance 1"
slideNumber: True
textAlign: 'left'
center: false
documentclass: book
lang: fr
# export_on_save:
    # pandoc: true
date: \today
pagesize: letter
output:
    pdf_document:
        template: default.latex
        toc: true
        toc_depth: 3
        path: "Log210-Exercices.pdf"

---

##### LOG210 Livre Exercices







# Système d'échange de livre

**Étude de cas :** Système d'échange de livres universitaires

Le Bureau du Développement Durable (BDD) de l'Université a mis en place
un système d'échange de livres aux fins de développement durable et pour
réduire les coûts pour les étudiants (les clients du système). La
version initiale est rudimentaire et ne permet que deux fonctionnalités
: Les vrais échanges se font par les étudiants (sans l'intervention du
système). Les cas d'utilisation sont détaillés ici.

## Cas d'utilisation


### CU01 - Ajouter un livre à échanger

**Acteur principal** : Client (étudiant)

**Préconditions** :

Le Client est identifié (par son nom d'utilisateur) et authentifié.

**Scénario principal (succès)**

1\. Le Client démarre un nouvel ajout de livre.

2\. Le Client entre le code ISBN du livre, ainsi que le code de sa
condition.

3\. Le Système enregistre le livre et présente sa description. Le Client
répète les étapes 2 à 3 jusqu'à ce qu'il ait saisi tous les livres à
échanger.

4\. Le Système présente la liste de livres que possède le Client.

### CU02 - Proposer un échange de livres

**Acteur principal** : Client (étudiant)

**Préconditions** :

Le Client est identifié (par son nom d'utilisateur) et authentifié.

**Scénario principal (succès)**

1\. Le Client démarre une nouvelle proposition d'échange de livres.

2\. Le Système présente une liste d'autres Clients dans le système ainsi
que le(s) livre(s) qu'ils ont à échanger.

3\. Le Client sélectionne un autre Client (le Client Proposé) à qui il
veut proposer un échange.

4\. Le Système présente la liste de livres que possède le Client Proposé
et une liste de livres que

possède le Client.

5\. Le Client ajoute à la proposition d'échange un livre. Si c'est un de
ses livres, alors c'est à offrir dans la proposition. Sinon c'est un
livre du Client Proposé et c'est à recevoir dans la proposition.

Le Client répète l'étape 5 jusqu'à ce qu'il soit satisfait de la
proposition.

6\. Le Système présente le nombre total de livres à offrir et à recevoir
et demande au Client de

confirmer la proposition.

7\. Le Client confirme et le Système enregistre sa proposition d'échange
avec la date et l'heure.

8\. Le Système envoie un courriel au Client Proposé pour l'informer de
la proposition d'échange.

11.2 Modèle du domaine


### Version 1

![](http://www.plantuml.com/plantuml/img/ZLFDQjmm4BxhAGPV0cMzaAiF8Trre85I0g6tN1Hhl2iYIs96NbXA7Y1lqLlPP-YX1pzGNw5ZhVSdJGgzoDRecs_c-pIwvgGfzPrJlt_-uYVheoRT0QUjGrd9DlbmRGq2TZ5jeSFk4ObVXz8w65QDqyomT1PzWcyAVEY-9kiiwuGzGGNtGkXN-U1iruIUoAAJq4T3o8pBAQAU9yxFTaCuKafHdsnhjLIeO1aCvgEHn1kRRF1JU7dO7pbgv8Pi76D7EaapU7k_-7BM3fWJy1G-i1IBdb3t3xuUTXjq8KRif2NPzwGV7HQW6HPrhIORYii2oXAA3yKaee8DzgaSTirQ-nKIN2c1luUBIE9i-U3DnRle39xALD2APzwES4RQs0RBuRkWzsGZScINj3SsL82SIYCbIDBb_YLhqdf78GREDWul-mwolhkRR9wHU_qaDpjor8T_SKgE3t8kv_CpHQ5jvNlrRm3Xy2FOz4Qb94YRdd1bPIZFAV9wD65K4dFJmmudBV-3p5OvNA4tuB1DwZXPizVJD3i9dVqzhJF0rCo1WnHmo92sKLPv9IPuBrLuhlRyOnbrBOiyhJy0){width="6.5in"
height="4.625in"}

## Diagramme de séquence système

### CU01 - Ajouter un livre à échanger

![](http://www.plantuml.com/plantuml/img/NP0zJWGn38NxdCBQYfKO2TeKguMfa13DYWE4n093VaQs1sblGycUWO9Y3iGLI390GHF9xyNVUybUrB7EAPglZqzveJmvTWb4Zn7hoUIxgQHr7kylBc60g-SoApBC6IAzCiBo1il9FxdyY6oSryAmiMCapBe19-1DfIfvcbpMQXsEeijxmcwAySDEm49OJian8tV-RIEVROs9fKp0A8eGKDR4lnstLbalappageqbuCtX-kuSVCc1b4gsJHj_fwsHOTZv5edYcQOc6im1MfRfR0iLcoZ_QzCNRIsnrlbf0s46tvzhzXLJF-mR){width="5.013888888888889in"
height="3.3333333333333335in"}

### CU02- Proposer un échange de livres

![](http://www.plantuml.com/plantuml/img/ZL9BJiCm4Dtx52Csj8jAY6KMLQMA7HA8YWCOnsr7n7OqdbJg4NeBbkGCB5ZuG5o1YVEX82JO97RcpNjltcGLMHCthb8VR-_n6NsjIJk8VAoiF0bDBZAotDUFLzUmW7iATOYMeF6GMhFNVcUXj53XWMnKsd0Wk2ZM5LhF5w0Z62MqZ0PhxLbAcsFazEfiBaPb5ii81PIfTPh8KY-0ZC6dKyy_cwkuM2oDm5BBJOb25C7o80hfPR92gYE4M83P1un8DmD-XcKw3MVXsSXqVlV5Ms7aipdowN8I6yWwoR81asTJgWgX1W7dndXcfXuoKW2XPkYpW8DjME367WBc-7A3O02w38gfxRRx_Z00nNU-YyTrA6q-pwN9-h8Z_qKYRBVq3u6x3FkBldjtS-POXO8jEVJVjZHkfm0Vt1DD4UhHYQIcfy578XFy5ibP-hdaeekqSQaTTz2NrKgioD_u2G00){width="4.5in"
height="5.5in"}

## Contrats d'opération

### CU01-Contrat-demarrerAjoutLivre

**Opération** : demarrerAjoutLivre()

**Préconditions** :

-   Une instance c de Client existe

-   

**Postconditions**:

-   Aucune

### CU01-Contrat-ajouterLivre

**Opération** : ajouterLivre(isbn : CodeISBN, condition : CodeCondition)

**Préconditions** :

-   Une instance c de Client existe

-   Une instance bdd de BureauDeveloppementDurable existe

**Postconditions**:

-   Une instance l de Livre a été créée

-   L.identifiant a été initialisé à une valeur unique

-   L.condition est devenu égale au paramètre condition

-   Une association entre l :Livre et DescriptionLivre aété créée sur la
    > vase de correspondance avec le paramètre isbn.

-   Une association entre l :Livre et bdd a été créée

-   Une association entre l :Livre et c :client a été créée

### CU01-Contrat-terminerAjoutLivre

**Opération** : terminerAjoutLivre()

**Préconditions** :

-   Une instance c de Client existe

**Postconditions**:

-   Aucune

### CU02-Contrat-demarrerPropositionÉchange

**Opération** : demarrerPropositionÉchange()

**Préconditions** :

-   Une instance c de Client existe

-   Une instance bdd de BureauDeveloppementDurable existe

-   

**Postconditions**:

-   Une instance p de PropositionEchange a été créée

-   Une association a été créée entre l'instance p :PropositionEchange
    > et c :Client

-   Une association a été créée entre l'instance bdd
    > :BureauDeveloppement et p :PropositionEchange

### CU02-Contrat-choisirEtudiant 

**Opération** : choisirEtudiant(idEtudiant : string)

**Préconditions** :

-   Une instance c de Client existe

-   Une instance p de PropositionEchange existe

**Postconditions**:

-   Une assocation entre p :PropositionEchange et client a été créée sur
    > la base de correspondance avec le parametre idEtudiant

### CU02-Contrat-proposerLivre

**Opération** : proposerLivre(idLivre :CodeLivre, estOffert :boolean)

**Préconditions :**

-   Une instance c de Client existe

-   Une instance p de PropositionEchange existe

**Postconditions**:

-   Une association a été créée entre p :PropositionEchange et Livre sur
    > la base de correspondance avec le paramètre idLivre

### CU02-Contrat-terminerProposition 

**Opération** : terminerProposition()

**Préconditions** :

-   Une instance c de Client existe

-   Une instance p de PropositionEchange existe

**Postconditions**:

> p.dateHeure est devenu maintenant

### CU02-Contrat-confirmerEchange 

**Opération** : confirmerEchange()

**Préconditions** :

-   Une instance c de Client existe

-   Une instance p de PropositionEchange existe

**Postconditions**:

-   Aucune

## Réalisation des cas d'utilisation


### RDCU-demarrerAjoutLivre

### RDCU-ajouterLivre

![](/assets/exercices.gddoc.docx/image78.png){width="6.5in" height="4.305555555555555in"}

Gracieuseté de Kevin Charbonneau

[[https://www.lucidchart.com/invitations/accept/23cd4f38-c942-4a72-aef1-0dff0c2a7768]{.underline}](https://www.lucidchart.com/invitations/accept/23cd4f38-c942-4a72-aef1-0dff0c2a7768)

### RDCU-terminerAjoutLivre

### RDCU-demarrerPropositionEchange

### RDCU-ChoisirEtudiant

### RDCU-proposerLivre

### RDCU-terminerProposition

### RDCU-confirmerEchange

[[1]{.underline}](https://n-xovwktmtjsnaxyc2mwes2xu7pohqedmdm6zjw5q-1lu-script.googleusercontent.com/userCodeAppPanel#)

# Diagramme d'activités

## Recette de cuisine

Diagramme d'activité d'une recette de cuisine

Référence : UML2 par la pratique, 6^e^ Édition, Pascal Roques.

Recette simpliﬁée : commencer par casser le chocolat en morceaux, puis
le faire fondre. En parallèle, casser les œufs en séparant les blancs
des jaunes. Quand le chocolat est fondu, ajouter les jaunes d'œuf.
Battre les blancs en neige jusqu'à ce qu'ils soient bien fermes. Les
incorporer délicatement à la préparation chocolat sans les briser.
Verser dans des ramequins individuels. Mettre au frais au moins 3 heures
au réfrigérateur avant de servir.

**Représentez** **par** **un** **diagramme** **d'activité** **la**
**recette** **de** **la** **mousse** **au** **chocolat...**

**Proposez** **d'abord** **une** **version** **simple,** **en**
**supposant** **que** **vous** **avez** **des** **ressources**
**illimitées,** **puis** **une** **version** **avec** **deux**
**personnes.** **Complétez** **ensuite** **le** **diagramme** **en**
**ajoutant** **soit** **des** **ﬂots** **d'objets.**

Le diagramme d'activité simple est donné par la ﬁgure suivante. Nous
supposons avoir des ressources illimitées, donc nous parallélisons au
maximum. Notez l'utilisation des barres d'embranchement (*fork*) et de
jointure (*join*), permettant de représenter précisément le parallélisme
dans les ﬂots de contrôle de l'activité. Notez également l'utilisation
du symbole graphique UML 2 pour l'action «Attendre 3h » qui est de type
: *accept* *time* *event*.

![](/assets/exercices.gddoc.docx/image18.png){width="5.15625in" height="7.375in"}

**Figure** **6-25.**

*Exemple* *de* *diagramme* *d'activité* *simple*

Si nous supposons maintenant que nous avons deux ressources, un chef et
un

apprenti, nous pouvons répartir les actions dans deux partitions.

![](/assets/exercices.gddoc.docx/image57.png){width="5.8125in" height="7.46875in"}

Nous allons maintenant compléter ce diagramme en ajoutant des ﬂots
d'objets. Le nom d'un état peut être mis entre crochets et placé avec le
nom du type.

![](/assets/exercices.gddoc.docx/image1.png){width="5.125in" height="5.864583333333333in"}

**Réf: Modélisation** **dynamique** **:** **exercices** **corrigés**
**et** **conseils** **méthodologiques**

 

## Système de gestion de remplacement de ressource

Dans le cadre du développement d'une application de gestion des horaires
du personnel, notre client veut valider le processus de demande de
remplacement qui doit être implanté dans le système. Il vous demande
donc de convertir les exigences suivantes en diagramme pour faciliter et
motiver les discussions entourant ce processus.

Le demandeur ouvre son calendrier mensuel, sélectionne la journée ou il
a besoin d'être remplacer et effectue la demande de remplacement. Le
système envoie la demande par sms et courriel au superviseur qui devra
accepter ou refuser la demande de remplacement.

En cas de refus, le système transfère la réponse du superviseur à
l'employé. Dans un cas positif, le système identifie les employés qui
sont disponibles et leur envoie un courriel pour leur demander s'ils
sont intéressés par le remplacement.

Les employés intéressés par le remplacement peuvent répondre directement
en cliquant sur le lien approprié dans leurs courriels. Un second lien
est aussi disponible dans le courriel pour que les personnes puissent
indiquer qu'ils ont bien reçu le message mais qu'ils ne sont pas
intéressés. Ce second lien permettra au client de valider le temps de
réponse de la solution proposé.

Dans le cas ou le remplacement doit avoir lieu dans un délai de moins de
24 heures, les messages sont aussi envoyés par SMS. L'employé peur alors
confirmer sa disponibilité en répondant au SMS. Le superviseur de
l'employé reçoit la demande de remplacement par SMS et/ou courriel.
Lorsque plusieurs personnes sont intéressées, le système applique les
règles d'affaire de l'entreprise pour sélectionner la bonne personne.
Toutefois, étant donnée que l'application en est encore à l'étape
d'évaluation par le client, le système enverra ses résultats d'analyse
au superviseur et c'est lui qui fera la confirmation finale en
approuvant le choix de la personne qui fera le remplacement.

Toutes les personnes ayant accepté le remplacement recevront alors la
confirmation s'ils ont été choisis ou non pour le remplacement. Advenant
qu'il n'y ait aucune personne intéressée ou disponible par le
remplacement, le système enverra l'horaire complet de la journée au
superviseur qui pourra planifier le déplacement de ses employés pour
combler les besoins.

## Ordinateur de plongé

Réaliser un diagramme d'activité pour le fonctionnement d'un ordinateur
de plongée qui calcul la profondeur du plongeur basé sur la pression de
l'eau et sa température.

Losqu'il n'est pas en mode de plongé, le compteur de profondeur d'eau
mesure la pression en continue à chaque 2 secondes. Lorsque le plongeur
entre dans l'eau, le traqueur de plongé change son mode d'opération pour
le mode plongé. Il vérifie alors la profondeur à chaque 500
milli-secondes en lisant le capteur de pression et en mesurant la
température de l'eau à l'aide d'un thermostat électronique qui fournie
une lecture au 30 secondes. Lorsque le plongeur remonte trop rapidement
le traqueur de plongée génère un alarme sonore. Le trackeur de plongé
redevient en mode d'attente lorsque le plongeur sort de l'eau. A tout
moment, le plongeur peut désactiver le module de mesure de température
et sortir du mode de plongé

![](/assets/exercices.gddoc.docx/image77.png){width="6.5in" height="7.916666666666667in"}

## Retour de voiture loué


Esquissez le diagramme d'activités lors de la réception de voitures
louées (après la location) dans une compagnie. Pour le diagramme, faites
att ention à la **notation UML**: cela comprend les objets (pour la
voiture et pour la facture), le début et la fin de l'activité, les
débranchements, les jointures, les décisions et les fusions.

-   Les rôles sont le \_\_\_\_\_\_ le \_\_\_\_\_\_\_\_ (qui gère la
    > documentation et le paiement de la location) et \_\_\_\_\_\_ (qui
    > gère le traitement des voitures avant la prochaine location).

    -   Le client rend la voiture et les clés.

    -   Le réceptionniste note le kilométrage et le niveau d'essence
        > pour calculer la facture.

    -   Le client paye sa location, selon le montant sur la facture et
        > part après.

    -   L'agent inspect la voiture pour la proprété. Si elle n'est pas
        > assez propre, alors l'agent doit laver, rincer et sécher
        > l'extérieur et nettoyer l'intérieur. Ce travail devrait
        > commencer le plus vite possible, après que le réceptionniste
        > ait finit de noter les informations pour la facture.

Pour la solution, voir la page suivante.

![](http://www.plantuml.com/plantuml/img/PP31IWD138RlUOhSR4_Unr8HGH6ab1MyzJ3iPjlGQMR9P2g5VI3tEVR5dArIBLx2aFpvvykVzYoTLt_0PAT0fIhNbWy1qcMoyz9yA9kHe6acCBOYNUHbHHQpOaDuZ6nP2KFCuq2Bsxo4_Z4mYVMGpAk1gqWQlIZleA_6eQREE8fmCkh1lV-ua64TnY5jmAsYaUAUGpoCdwP-Eqr1-4W-OtD3AP7KnQsDkWVtF0uo3besMbz_V-EUlb-RNo2tzgShoRe0iXQaX-rPC9cXtteMS2-IEgedY0ivjpZhD7PAztEqNObb5ZFFWK8Yd4cKEQ1xzSU_E-WgBg1NdRSImEwwjIApEC6nM3c4AHUi4XotKyNpbV-3InQxBm00){width="6.5in"
height="5.569444444444445in"}

![](http://www.plantuml.com/plantuml/img/PP31IWD138RlUOhSR4\_Unr8HGH6ab1MyzJ3iPjlGQMR9P2g5VI3tEVR5dArIBLx2aFpvvykVzYoTLt\_0PAT0fIhNbWy1qcMoyz9yA9kHe6acCBOYNUHbHHQpOaDuZ6nP2KFCuq2Bsxo4\_Z4mYVMGpAk1gqWQlIZleA\_6eQREE8fmCkh1lV-ua64TnY5jmAsYaUAUGpoCdwP-Eqr1-4W-OtD3AP7KnQsDkWVtF0uo3besMbz\_V-EUlb-RNo2tzgShoRe0iXQaX-rPC9cXtteMS2-IEgedY0ivjpZhD7PAztEqNObb5ZFFWK8Yd4cKEQ1xzSU\_E-WgBg1NdRSImEwwjIApEC6nM3c4AHUi4XotKyNpbV-3InQxBm00]{.underline}](http://www.plantuml.com/plantuml/img/PP31IWD138RlUOhSR4_Unr8HGH6ab1MyzJ3iPjlGQMR9P2g5VI3tEVR5dArIBLx2aFpvvykVzYoTLt_0PAT0fIhNbWy1qcMoyz9yA9kHe6acCBOYNUHbHHQpOaDuZ6nP2KFCuq2Bsxo4_Z4mYVMGpAk1gqWQlIZleA_6eQREE8fmCkh1lV-ua64TnY5jmAsYaUAUGpoCdwP-Eqr1-4W-OtD3AP7KnQsDkWVtF0uo3besMbz_V-EUlb-RNo2tzgShoRe0iXQaX-rPC9cXtteMS2-IEgedY0ivjpZhD7PAztEqNObb5ZFFWK8Yd4cKEQ1xzSU_E-WgBg1NdRSImEwwjIApEC6nM3c4AHUi4XotKyNpbV-3InQxBm00)

## Processus d\'achat sur le Web

Modéliser à l'aide d'un diagramme d'activités en utilisant la
représentation sous forme de couloirs d'activités, un processus d'achat
faisant intervenir un client désireux de se procurer un produit et un
fournisseur désireux de lui vendre le produit. Le client choisit son
produit par catalogue. Il achemine sa commande via le site Web du
fournisseur et indique son no. de carte de crédit. Le fournisseur
analyse ses commandes et expédie dans la journée même toutes les
commandes dont la date de livraison désirée est égale à la date du jour
et il y joint le bon de facturation. À la réception du produit, le
client confirme son paiement via le site Web ou si le produit est
défectueux, avise le fournisseur, via le site Web qu'il lui retourne le
produit. En cas de défectuosités, le client retourne le produit au
fournisseur et lors de la réception du colis, le fournisseur lui expédie
un accusé de réception. Si le client garde le produit, il doit en
autoriser le paiement via le site Web (voir solution Sylvie).

Ébauche de solution

![](http://www.plantuml.com/plantuml/png/RL5BSiCW3Drp2YtZAzYB9isqwruW2s94hGw8Z80qcV65V0vVh7AJoQVJ7GYzB-jSh9GQWnctWP3BQ7udfjqEYJ8972IvIWMSvGozBJQapugTQJVzW94O1VeKesM7W0KuwP8K1BtsCa-EIcVC-9wgCEMCLKRblW9soi8sdFC3IUuCULW5Eegbd1ZSFAcFUG9RlvJ53PLU6YW3CgpEc1lJlfqEYz0pIVkwO16yxKiLMoZnpc3822jEZJ78ZlmzTNlDUL6\_XPudZuh7UdgMt1nfCUtliU0VZBeGBCiEtjwxlsLyNEQFvhGWzYHnGLd2g0xr810GCccttxZlp5eJwCVz0000]{.underline}](http://www.plantuml.com/plantuml/png/RL5BSiCW3Drp2YtZAzYB9isqwruW2s94hGw8Z80qcV65V0vVh7AJoQVJ7GYzB-jSh9GQWnctWP3BQ7udfjqEYJ8972IvIWMSvGozBJQapugTQJVzW94O1VeKesM7W0KuwP8K1BtsCa-EIcVC-9wgCEMCLKRblW9soi8sdFC3IUuCULW5Eegbd1ZSFAcFUG9RlvJ53PLU6YW3CgpEc1lJlfqEYz0pIVkwO16yxKiLMoZnpc3822jEZJ78ZlmzTNlDUL6_XPudZuh7UdgMt1nfCUtliU0VZBeGBCiEtjwxlsLyNEQFvhGWzYHnGLd2g0xr810GCccttxZlp5eJwCVz0000)

## Procédure de paiement sécurisé


À l\'aide de l\'information du site
[[http://www.paiementsecurise.net/fonctionnement.html]{.underline}](http://www.paiementsecurise.net/fonctionnement.html)
modéliser la procédure de paiement sécurisé pour un site de e-commerce.

## compression de HuffMan 


Modéliser l'algorithme de compression de HuffMan telle qu\'expliquée sur
le site http://tcharles.developpez.com/Huffman/

![](/assets/exercices.gddoc.docx/image90.jpg){width="6.5in"
height="4.875in"}
![](/assets/exercices.gddoc.docx/image16.jpg){width="6.5in"
height="4.875in"}

# Diagrammes d'état

## Diagramme d'état d'un vidéoprojecteur


Référence : UML2 par la pratique, 6^e^ Édition, Pascal Roques.

Modélisez le comportement du vidéoprojecteur lors d'une session de
formation.

Commencez par identiﬁer les états et transitions « nominaux ». Ajoutez
les

périodes de préchauffage et de refroidissement de la lampe. Représentez

ensuite le fait qu'il faut appuyer successivement deux fois en moins de
5 s sur

le bouton power pour interrompre la vidéo projection. Envisagez enﬁn la
panne de la lampe...

Commençons par identiﬁer le scénario nominal d'utilisation du vidéo
projecteur : le brancher, puis l'allumer (bouton power), puis connecter
l'ordinateur. Ensuite, l'éteindre, puis le débrancher. Ensuite nous
ajoutons la possibilité de l'éteindre alors qu'il est allumé ou
connecté, puis celle de le débrancher intempestivement.

![](/assets/exercices.gddoc.docx/image92.png){width="5.802083333333333in"
height="3.5416666666666665in"}

Ajoutons le comportement suivant : si l'on éteint le vidéoprojecteur
sans le

déconnecter de sa source, il repassera directement dans l'état
*Connecté* quand on le rallumera. Les deux états *Allumé* et *Connecté*
intègrent chacun une activité durable : respectivement la projection
d'un écran bleu ou de la source d'entrée.

![](/assets/exercices.gddoc.docx/image93.png){width="5.8125in" height="3.5104166666666665in"}

Ajoutons maintenant les activités continues de préchauffage et de
refroidisse-

ment de la lampe. Il est donc nécessaire d'introduire deux états
supplémentai-

res autour de l'état *Éteint*.

Comment sortir de ces états supplémentaires : soit en utilisant un
événement

de changement (when) testant la température de la lampe, soit plus
simple-

ment une transition automatique. Nous utiliserons cette dernière
solution,

plus simple et n'obligeant pas à spéciﬁer les températures visées.

Vériﬁons que nous avons pris en compte tous les scénarios : d'abord le
com-

portement nominal en début de session de formation : *Débranché* 
brancher

 *Éteint*  power  *Préchauffage*  \[source absente\]  *Allumé*
 connecter

source  *Connecté*.

Puis, à la pause, le formateur éteint le projecteur :

*Connecté*  power  *Refroidissement*  *Éteint*. Ensuite, de retour
dans la salle,

il rallume le projecteur et n'a pas besoin de reconnecter la source :
*Éteint* 

power  *Préchauffage*  \[source présente\]  *Connecté*.

![](/assets/exercices.gddoc.docx/image101.png){width="6.5in" height="4.611111111111111in"}

Pour éviter de perdre trop de temps lors d'un appui intempestif sur
power dans l'état *Connecté*, les vidéoprojecteurs modernes demandent
une conﬁrmation sous la forme d'un deuxième appui sur power en moins de
5 s.

On ajoute un événement temporel after (délai) qui va nous servir ici, à
associé un nouvel état transitoire d'attente de conﬁrmation.

![](/assets/exercices.gddoc.docx/image79.png){width="6.5in" height="4.611111111111111in"}

En fait, la conﬁrmation pour éteindre le video projecteur est également
obligatoire depuis l'état *Prêt*. On peut donc introduire un super-état
englobant *Prêt* et *Connecté*, mais il faut alors utiliser un
pseudo-état *History* (H) pour savoir dans quel sous-état revenir quand
la temporisation tombe.

![](/assets/exercices.gddoc.docx/image28.png){width="6.5in" height="5.166666666666667in"}

## Guichet automatique bancaire

Faire un diagramme d'états en UML qui correspond au système décrit par
les cas d'utlisation suivants (format bref):

**S'authentifier.** Le Client arrive à un guichet automatique bancaire,
car il désire effectuer une transaction sur son compte. Le Client
introduit sa carte bancaire et le système attend qu'il saisisse le NIP
de la carte. Si le NIP est valide pour la carte, alors le système est
prêt pour accepter d'autres actions. Sinon, le système enregistre la
mauvaise tentative et demande de nouveau au Client de saisir son NIP. À
tout moment que le système possède la carte du Client, ce dernier peut
annuler la session pour récupérer sa carte.

**Gérer guichet**. L'Administrateur démarre le système et le système
attend l'introduction d'une carte bancaire du Client. Quand le système
est dans cet état, l'Administrateur peut aussi l'éteindre.

![](http://www.plantuml.com/plantuml/img/ZP0n3i8m34NtdC9iW8IwTq15J2oeU-aGDHPOQbFakDofNACNmw52ZH03w__lszykWbYMeMjDjQrXjzl3GGIzEwgAa8ERniuo8vj4Nx3pgLI8l73l1c9yssRn8bdoz1IbWgL07DNAqnqUjYM7zHUSZaq2g_KIsTIGNJnwnYi5qMemZSqDcv-JFdTOxuTMqGn2pq8y5vsh_KkdZ4RYmtBTBKZUCPf2pVZ85m00){width="4.930555555555555in" height="4.361111111111111in"}

## Téléphone intelligent


Faire un diagramme d'états en UML modélisant les états d'un téléphone
intelligent. Considérer une dynamique simplifiée, avec seulement trois
états correspondant aux images suivantes:

Pour simplifier encore le modèle, le bouton en haut à droite sert pour
éteindre et pour allumer l'écran. Le téléphone est initialement éteint.
Vous pouvez ignorer l'autre bouton rond au centre en bas. On peut
brancher l'alimentation pour charger le téléphone à tout moment, mais le
bouton n'a aucun effet sur l'écran lorsque le téléphone est connecté à
l'alimentation. Lorsque l'on débranche l'alimentation, l'écran est
toujours éteint.

![](http://www.plantuml.com/plantuml/img/SoWkIImgAStDuOhMYbNGrRLJEDoPN9IOTxYp93KphuGBXOSaxvYJKvfxUAM2bK9YSabcVbvUQf5JVcb9VXuNgZo6YJXrODeHb9gSaLYKdWhKaWJa9cUa5ZdcPEQcvfKaWWp0QHDn-k2gi3anvV1Ah5eTKlDIW8450000){width="6.416666666666667in"
height="4.194444444444445in"}

 

## Bank Automated Teller Machine (ATM)


ATM is initially turned off. After the power is turned on, ATM performs
startup action and enters Self Test state. If the test fails, ATM goes
into Out of Service state, otherwise there is triggerless transition to
the Idle state. In this state ATM waits for customer interaction.

The ATM state changes from Idle to Serving Customer when the customer
inserts banking or credit card in the ATM\'s card reader. On entering
the Serving Customer state, the entry action readCard is performed.
Note, that transition from Serving Customer state back to the Idle state
could be triggered bycancel event as the customer could cancel
transaction at any time.

![](/assets/exercices.gddoc.docx/image20.png){width="6.5in" height="5.236111111111111in"}

## Caisse enregistreuse - Diagramme d'état vers diagramme de classe


![](/assets/exercices.gddoc.docx/image68.jpg){width="6.130208880139983in" height="4.597656386701662in"}
-

![](/assets/exercices.gddoc.docx/image109.jpg){width="4.701388888888889in" height="3.526042213473316in"}


# Diagramme de déploiement

## Application WEB

Faire un diagramme de déploiement décrivant le système suivant:

> *Pour une application Web, il y a trois types de clients : 1) le
> client PC qui utilise un fureteur moderne pour accéder au serveur Web
> via http, 2) le client qui utilise une app AppGéniale sur Android 5.1
> pour accéder au serveur Web via SOAP/http et 3) le client qui utilise
> une app AppGéniale sur iOS 8 pour accéder au serveur Web via
> SOAP/http.*
>
> *Côté serveur Web, l'application est hébergée dans le nuage, avec sur
> Amazon Web Service EC2 sur Linux. L'application Signup est un ensemble
> de fichiers HTML et JavaScript et ça roule avec Node.js, un moteur V8
> JavaScript Engine et une base de données DynamoDB.*

![](/assets/exercices.gddoc.docx/image105.png){width="6.5in" height="2.888888888888889in"}

Gracieuseté de Kevin Charbonneau

![](https://www.lucidchart.com/invitations/accept/cc1ca66e-4734-43c2-aa08-7ba372b09045)

## CarSharing application


Three entity classes are used in a collaboration - CarSharer, Journey
and Address. Each of these classes will be implemented by a (.java)
source file. these classes are used across a number of use cases and are
grouped together into a CarSharing component as Java (.class) files.
Here we are just dealing with the source files. There are two other
classes MCSUserInterface and MCSControl. Each of these will eb
implemented by a (.java) file. The MCSControl component has a dependency
on the CarSharing component and on the MCCSUserInterface Component.

A)  Draw a component diagram showing the source ocde dependencies. The
    > .class file are grouped together into two Java archive (.jar)
    > files. The MCSControl.class component will need to read a
    > configuration file (MCS.ini) and display a help file (MCS.hlp)
    > when required. The MCSControl (.class) file also has dependencies
    > on the MCSUserInterface (.java) file and the CarSharing (.jar)
    > components.

> ![](/assets/exercices.gddoc.docx/image23.png){width="4.947916666666667in" height="3.25in"}

ref: U0812 \@Peter LO 2010

> B\) Re-draw the component diagram to show the run-time component
> dependencies.
>
![](/assets/exercices.gddoc.docx/image73.png){width="4.458333333333333in" height="3.7395833333333335in"}
>
> ref: U0812 \@Peter LO 2010
>
> C\) Draw a deployment diagram given that the nodes are three client
> PCs, a server and a printer. The communications protocol between the
> clients and server is TCP/IP; and between the server and the printer
> is a standard parallel printer protocol. The MCS.jar user interface
> and the control objects will run on the clients. The CarSharing.jar
> will run on the server. Server will also provide initialisation file
> MCS.ini and an help file named MCS.help.

![](/assets/exercices.gddoc.docx/image91.png){width="5.916666666666667in" height="3.5833333333333335in"}

> ref: U0812 \@Peter LO 2010

## Web server deploiement


Draw a deployment diagram to show how a Web browser (Netscape) and a Web
server (Apache) are located on different machines and the use HTTP as
communication protocol.

> ![](/assets/exercices.gddoc.docx/image31.png){width="5.208333333333333in"
> height="1.4479166666666667in"}

ref: U0812 \@Peter LO 2010

 

# Affinement du modèle du domaine

## Vente de billets en lignes 


Un système de vente de billets en ligne doit supporter différents types
de réductions de prix. Les seuls types de réductions possibles sont les
réductions de de volume et de groupe. Les réductions de volume peuvent
être basées soit sur le nombre de billets achetés, soit sur le montant
d\'argent dépensé pour l\'achat. Les réductions de groupe sont offertes
aux membres d'un groupe particulier, par exemple, une entreprise ou une
organisation de charité. Toutes les réductions sont comptabilisées comme
un pourcentage par rapport au total d'un achat d'un groupe de billets.

Proposez les classes du modèle du domaine pour le concept de réduction.

Pour la solution, voir
[[http://bit.ly/S2xJEm]{.underline}](http://bit.ly/S2xJEm) (URL masqué)

## Système de gestion des inscriptions


Un système pour gérer les inscriptions et les relevés de notes pour une
université doit supporter l'enregistrement de l'inscription d'un
étudiant à un groupe­cours, ainsi que sa note (le cote) à la fin du
cours.

Faites une partie du modèle du domaine du système comprenant les classes
conceptuelles importantes. Indice: une classe d'association est
essentielle pour la bonne solution.

Pour la solution, voir
[[http://bit.ly/1sxqTs4]{.underline}](http://bit.ly/1sxqTs4)

 

## **Reconnaître les GRASP dans les GoF**

Pour les questions suivantes, **suivre le modèle en annexe**.

1.  Soit le diagramme du patron GoF suivant ([[reproduit de
    > Horstmann]{.underline}](about:blank)), identifier les GRASP
    > (Polymorphisme, Fabrication pure, Indirection, Protection des
    > variations) dans ce patron et faire une mise en correspondance
    > détaillée.

> ![](/assets/exercices.gddoc.docx/image94.jpg){width="3.7708333333333335in"
> height="3.3541666666666665in"}

2.  Soit le diagramme du patron GoF suivant ([[reproduit de
    > Horstmann]{.underline}](https://cours.etsmtl.ca/log120/horstmann/htm/Ch5/slide037.html)),
    > identifier les GRASP (Polymorphisme, Fabrication pure,
    > Indirection, Protection des variations) dans ce patron et faire
    > une mise en correspondance détaillée.

> ![](/assets/exercices.gddoc.docx/image9.jpg){width="4.15625in" height="2.65625in"}

16.1 Annexe : Modèle (solutionnée)
-

Soit le diagramme du patron GoF suivant ([[reproduit de
Horstmann]{.underline}](https://cours.etsmtl.ca/log120/horstmann/htm/Ch10/slide004.html)),
identifier les GRASP (Polymorphisme, Fabrication pure, Indirection,
Protection des variations) dans ce patron et faire une mise en
correspondance détaillée :

![](/assets/exercices.gddoc.docx/image104.jpg){width="6.447916666666667in"
height="3.8020833333333335in"}

## Identification des GRASP dans Adapter (GoF)

**Polymorphisme** - définition selon Larman: "Lorsqu\'un comportement
varie selon le type (classe), affectez la [responsabilité de ce
comportement]{.underline} - avec des [opérations
polymorphes]{.underline} - [aux types pour lesquels le comportement
varie]{.underline}."

**Mise en correspondance détaillée :** Le "comportement qui varie" est
la manière d'adapter la "targetMethod()" à la "adapteeMethod()". Alors,
cette "responsabilité" est affectée au type interface "Target" dans
l'opération polymorphe "targetMethod()".

**Fabrication pure** - définition selon Larman: "Affectez un [ensemble
très cohésif de responsabilités]{.underline} à [une classe «
comportementale » artificielle]{.underline} qui ne représente pas un
concept du domaine - une entité fabriquée pour [augmenter la
cohésion]{.underline}, [diminuer le couplage]{.underline} et [faciliter
la réutilisation]{.underline}."

**Mise en correspondance détaillée:** La Fabrication pure est la classe
"comportementale et artificielle" est la hiérarchie Target et ses sous
classes Adapter. Ces classes ont des "responsabilités cohésives" qui
sont la manière d'adapter les méthodes de Target aux méthodes des
Adaptees. La cohésion est augmentée, car le Client n'a pas la
responsabilité de s'adapter aux Adaptees (c'est le travail des
Adapters). Le couplage est diminué, car le Client n'est pas couplé
directement aux Adaptees. La réutilisation des Adaptees est facilitée,
car le Client ne doit pas être modifié si l'on veut réutiliser une autre
Adaptee - il suffit de créer un Adapter pour cette dernière.

**Indirection** - définition selon Larman: "Pour [éviter le couplage
direct]{.underline}, affectez [la responsabilité]{.underline} à un objet
qui sert d\'[intermédiaire avec les autres composants ou
services]{.underline}."

**Mise en correspondance détaillée:** Le "couplage directe" qui est
évité c'est le couplage entre Client et Adaptee. Le patron cherche à
découplé le Client des classes Adaptee, car chaque Adaptee a une API
différente pour le même genre de "service". Alors, la responsabilité de
s'adapter aux services différents est affecté à la hiérarchie de
"classes intermédiaires" Target et Adapters.

**Protection des variations** - définition selon Larman: "Comment
affecter les responsabilités aux objets, sous-systèmes et systèmes de
sorte que [les variations ou l\'instabilité de ces éléments]{.underline}
n\'aient pas d\'[impact négatif sur les autres]{.underline} ?

Identifiez les points de variation ou d\'instabilité prévisibles et
[affectez les responsabilités]{.underline} afin de [créer une «
interface » stable]{.underline} autour d\'eux."

**Mise en correspondance détaillée:** Les "variations ou l'instabilité"
sont les classes Adaptees qui ne sont pas sous le contrôle des
développeurs du projet, puisque ce sont des classes qui offrent un
service que l'on veut réutiliser. Quant à "l'impact négatif sur les
autres," il s'agit des modifications que les développeurs auraient à
faire sur la classe Client, chaque fois que l'on décide de réutiliser un
Adaptee. Quant aux "responsabilités affectées", c'est les
fonctionnalités communes de tous les Adaptees. Pour ce qui est de
"l'interface stable", il s'agit du type interface Target qui isole
(protège) la classe Client des modifications (changement de Adaptee).

# FURPS

## Exercice sur l'identification d'exigences selon le modèle FURPS+


Rappel : Définition de FURPS :

  F    
   
  U    
  R    
  P    
  S    
  \+   

Identifier les exigences du modèle FURPS+ dans le texte suivant, tiré
d'une brochure de Microsoft Office 365\[1\] :

  **Exigence**                                                       FURPS+
  - 
  Une messagerie en nuage                                            
  Calendriers et contacts partagés                                   
  Messagerie instantanée, appels de PC à PC et conférence en ligne   
  Site Intranet pour le partage de fichiers                          
  Site Web destiné au public                                         
  Installation et administration simples                             
  Antivirus et filtrage antispam                                     
  Support de la communauté Microsoft                                 
  Disponibilité à 99,9 % garantie financièrement                     
  Office Web Apps (Word, Excel, PowerPoint, et OneNote)              
  Support en direct par téléphone 24h/24 et 7j/7                     
  Synchronisation Active Directory                                   
  Prise en charge de la messagerie vocale hébergée                   
  Stockage du courrier électronique et archivage illimités           

![1]
[http://www.microsoft.com/fr-ca/office365/free-office365-trial.aspx?WT.mc\_id=ODC\_enCA\_O365Try\_Generic\_Hero]{.underline}

**Solution: Exercice sur l'identification d'exigences selon le modèle
FURPS+**

Rappel : Définition de FURPS :

  F    Capability (Size & Generality of Feature Set), Reusability (Compatibility, Interoperability, Portability), Security (Safety & Exploitability)
   
  U    (UX) - Human Factors, Aesthetics, Consistency, Documentation, Responsiveness
  R    Availability (Failure Frequency (Robustness/Durability/Resilience), Failure Extent & Time-Length (Recoverability/Survivability)), Predictability (Stability), Accuracy (Frequency/Severity of Error)
  P    Speed, Efficiency, Resource Consumption (power, ram, cache, etc.), Throughput, Capacity, Scalability
  S    (Serviceability, Maintainability, Sustainability, Repair Speed) - Testability, Flexibility (Modifiability, Configurability, Adaptability, Extensibility, Modularity), Installability, Localizability
  \+   Design requirements, Implementation requirements, Interface requirements, Physical requirements

Identifier les exigences du modèle FURPS+ dans le texte suivant, tiré
d'une brochure de Microsoft Office 365\[1\] :

  **Exigence**                                                       FURPS+
  - 
  Une messagerie en nuage                                            R
  Calendriers et contacts partagés                                   R
  Messagerie instantanée, appels de PC à PC et conférence en ligne   U
  Site Intranet pour le partage de fichiers                          U
  Site Web destiné au public                                         U
  Installation et administration simples                             U
  Antivirus et filtrage antispam                                     R
  Support de la communauté Microsoft                                 U
  Disponibilité à 99,9 % garantie financièrement                     R
  Office Web Apps (Word, Excel, PowerPoint, et OneNote)              U
  Support en direct par téléphone 24h/24 et 7j/7                     U
  Synchronisation Active Directory                                   S
  Prise en charge de la messagerie vocale hébergée                   U
  Stockage du courrier électronique et archivage illimités           R

Packages

Patron GOF


# Conception de packages

## Servlet Java 


Voici des classes d'un système de Servlet Java:

![](/assets/exercices.gddoc.docx/image17.png){width="6.5in" height="4.680555555555555in"}

Organisez les classes en DEUX packages selon le principe de cohésion
fonctionnelle. Pour la solution, voir
[[https://www.uml-diagrams.org/examples/java-servlet-25-api-package-diagram-example.html?context=pkg-examples]{.underline}](https://www.uml-diagrams.org/examples/java-servlet-25-api-package-diagram-example.html?context=pkg-examples)

## Refactorisation 

## Exercice 1


Appliquez (au moins une fois) la refactorisation nommée « Extraction de
méthode » (*Extract method* en anglais) pour améliorer la lisibilité du
code suivant.

void afficherCréance() {

Enumeration e = \_commandes.elements();

double coursDeCrédit = 0.0;

// afficher entête

> System.out.println
> (\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");
>
> System.out.println (\"\*\* À recevoir du client \*\*\");
>
> System.out.println
> (\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

// calculer montant en cours de crédit

while (e.hasMoreElements()) {

> Commande chaque = (Commande) e.nextElement();
>
> coursDeCrédit += chaque.getMontant();
>
> }
>
> // afficher details
>
> System.out.println (\"nom:\" + \_nom);
>
> System.out.println (\"montant \" + coursDeCrédit);

}

 

## Exercice \#1 Solution 


void afficherCréance() {

Enumeration e = \_commandes.elements();

double coursDeCrédit = 0.0;

afficherEntête();

// calculer montant en cours de crédit

while (e.hasMoreElements()) {

> Commande chaque = (Commande) e.nextElement();

coursDeCrédit += chaque.getMontant();

}

// afficher details

> System.out.println (\"nom:\" + \_nom); System.out.println (\"montant
> \" + coursDeCrédit);

}

void afficherEntête() {

// afficher entête

System.out.println
(\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

System.out.println (\"\*\* À recevoir du client \*\*\");

System.out.println
(\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

}

 

 

 

# Révision 

## Révision GOF


![](/assets/exercices.gddoc.docx/image75.png){width="6.5in" height="4.069444444444445in"}

Définitions horizontales :

1-On veut accéder au contenu d'un objet agrégé sans connaître sa
structure interne (son implémentation). On veut pouvoir supporter de
multiples parcours d'objets agrégés. On veut fournir une interface
normalisée pour parcourir des objets agrégés ayant des formes
différentes.

3-On veut pouvoir défaire (« undo ») des opérations de l'application. On
veut pouvoir faire des opérations de l'application avec des paramètres.
On veut pouvoir spécifier, mettre en file d'attente, puis exécuter des
opérations de l'application. On veut définir et exécuter la combinaison
des opérations de l'application.

6-On a besoin d'accéder à des objets à distance, comme s'ils étaient
locaux.On trouve que l'instanciation de certains objets a un impact
négatif sur la performance du système. On veut limiter l'accès à
certains objets pour la sécurité. On a des besoins particuliers
concernant l'accès à certains objets, p.ex. charger en mémoire vive la
première fois un objet persistant.

8-L'application a besoin d'un service, mais ce service est déjà
implémenté. Il en existe plusieurs implémentations, ayant des interfaces
de programmation (API) différentes. On est obligé de faire beaucoup de
modifications dans l'application pour que ça fonctionne avec chaque API
différente.

10-On a une structure d'objets ayant plusieurs classes avec des
interfaces différentes. On veut effectuer des opérations sur ces objets
et les opérations dépendent des classes concrètes. On trouve que les
classes de la structure d'objets ont du code spécifique pour les
opérations et ce code n'est pas très cohésif. Les classes définissant la
structure d'objets évoluent rarement, mais il est plus fréquent
d'ajouter ou de modifier une opération effectuée sur la structure
d'objets.

11-On applique certains services sur un ensemble d'objets individuels.
Mais on aimerait également appliquer ces services sur une ou plusieurs
sortes agrégation de ces objets, comme si une agrégation était un objet
individuel.

12-On veut instancier un objet faisant partie d'une hiérarchie de
classes, mais on n'est pas toujours sûr de quelle classe il s'agit.

13-On veut pouvoir ajouter (ou enlever) des responsabilités
(comportements, fonctionnalités) aux objets d'une façon dynamique et
transparente, sans affecter d'autres objets. Le nombre de combinaisons
possibles de ces responsabilités est important. Alors, il est complexe
de faire une sous-classe pour chaque combinaison.

Définitions verticales :

2-On trouve qu'il existe un algorithme ayant des parties fixes et des
parties variantes, avec du code complexe pour traiter tous les cas
variant. On a des sous classes ayant des responsabilités communes et
dupliquées dans le code. On veut contrôler les extensions permises dans
les sous classes pour une certaine classe.

4-Une abstraction comporte deux aspects, l'un dépend de l'autre. Un
changement d'état dans un objet engendre des changements d'états dans
d'autres objets, et on ne sait pas a priori lesquels. Un objet devrait
pouvoir avertir d'autres objets des événements importants, sans un
couplage fort avec ces derniers (sans les connaître concrètement).

5- Les classes ayant des responsabilités d'affichage des informations
dans l'interface utilisateur graphique ont une tendance à évoluer
souvent dans le cycle de vie d'un logiciel. On cherche un design qui
facilite cette évolution, en minimisant les changements dans le reste du
code source. On veut aussi avoir une bonne traçabilité entre les
fonctionnalités du logiciel et le code source.

7-On trouve qu'il y a plusieurs classes similaires, mais qui varient
seulement sur le plan comportemental. On a besoin de plusieurs variantes
algorithmiques pour un même service. Un algorithme utilise des
structures de données complexes, augmentant le couplage entre le client
et ces structures. Une classe définit plusieurs comportements,mais ces
comportements dépendent d'une condition.

9-On veut faire en sorte qu'une classe n'ait qu'une seule instance et
que l\'accès à cette instance soit accessible aux clients à un endroit
bien connu.On veut permettre la spécialisation de la seule instance par
des sous classes, sans que les clients aient à modifier leur code.

 

## Question de révision de Larman


Review Questions from Larman

Les réponses sont affiché avec un font blanc. Sélectionner le texte pour
voir celle-ci.

**Chapter 2:**

> \- What is *iterative development*?

La croissance et l'affinement successifs d'un système par le biais
d'itérations multiples, le feed-back et l'adapdation cycliques.

> \- What is the benefit of short iterative cycles?

Feedback rapide et adaptation

> \- What are the benefits of iterative development?

Diminution des échecs, amelioration de la productivité et de la qualité.
Gestion précoce des risques élevés. Feedback, implication des
utilisateurs et adaptation précoces. Complexité géré, Possibilité
d'exploiter méthodiquement les lecon tirées d'une iteration.

> \- What is the *waterfall life-cycle*?

Méthode on l'on tente de défénir la plus grande partie des
specifications, voire toutes, avant de programmer

> \- What is "waterfall thinking"? What is wrong with it?
>
> L'idée qu'on peut écrire tous les cas d'utilisation ou realiser tous
> les modèles OO détaillé avant de commencer à programmer et un exemple
> de raisonnement incorrect. C'est l'une des principals raison d'échec
>
> \- What is *risk-driven* iterative development?
>
> Les objectifs des premières iterations sont choisis afin d'identifer
> et d'atténuer les risques les plus importants et construire les
> fonctionnalités visibles qui compte le plus pour le client
>
> \- What is *client-driven* iterative development?

Notre première priorité est de satisfaire le client en lui livrant
rapidement et de facon continue un logiciel de qualité. Accepter les
changements des besoins, meme en cours de développpement. Livrer
fréquemment. Experts métier et developpeurs doivent travailler ensembles
quotidiennement pendant toute la durée du projet.

> \- What is an *agile* process?

Processus qui prévilégie: les individus et les interactions advantage
que les processus etles outil; les logiciels fonctionnels advantage que
l'exhautivité de la documentation; la collaborationavec le client
advantage que la négociation de contrats; la réponse au changement
advantage que l'application d'un plan.

> \- What is the "secret of modeling" (its primary purpose)?

L'objectif de la modélisation (des diagrammes UML) est avant tout de
comprendre, pas de documenter.

> \- Does an agile process mean there is no modeling?

Non. Cela signifie qu'on génère seulement les artefact requis pour
comprendre le système.

> \- Identify some current agile processes.

Inception, Élaboration, Construction et Transition.

> \- What are the UP disciplines and how do they map to the traditional
> life-cycle?

Exigences: Modèle de cas d'utilisation et specifications supplémentaires

Modelisation métier: Modèle du domaine,

Conception: Modèle de conception DCC

Implémentation: programmation et construction du système

Environnement: Choix des outils et personalisation du processus.

> \- What is an *artifact*?

Tout document permettant d'apporter une comprehension au système

> \- Contrast a *heavy* process with an *agile* process.

Chapter 3:

> \- Identify the typical architectural layers (subsystems).

Interface usilisateur, couche logique applicative, autre couches et
composantes( service technique)

Chapter 5:

> \- Define *requirements*.

Condition auquels un système ou un projet doivent satisfaires

> \- What does it mean to manage requirements?

D'effectuer un travail systèmatique de recherché, de documentation,
d'organisation et de suivi des besoins évolutive du système (RUP) dna un
context oules sohaits des parties intéressés ne sont pas toujours
explicites et changent inévitablement.

> \- What are the types of requirements? (FURPS+)

Fonctionnalité, Aptitude à l'utilisation, Fiabilité, Performance,
Possibilité de prise en charge, Implémentation, interface, exploitation,
conditionnement, aspects juridiques.

> \- True or false: Requirements are object-oriented.
>
> false
>
> \- What is meant by *functional* requirements?

Les requis en terme de fonctions, capatités et de sécurité

> \- What are the requirements *artifacts*?

Modèle de cas d'utilisation, specifications supplémentaires, Glossaire,
Visition, Règles métier

Chapter 6 - Use Case Modeling

> \- Define the term *use case*.

C'est un artefact représentant les acteurs et les cas d'utilisation ansi
que les relation les unissant.

> \- Who is the \"guru\" of use case(s)?

L'acteur principal

> \- What is an *actor*?

Entité qui a un comportement, comme une personne (identifiée par un
role)

> \- Give examples of actors.

Un caissier, un système, une entreprise

> \- True or false: Use cases are object-oriented.

non

> \- A use case helps capture system \_\_\_\_\_\_\_\_\_\_\_\_\_.

requirement

> \- What is a *scenario*?

C'est une suite spécifique d'actions et d'intéractions entre un ou
plusieurs acteurs et le système. Histore de la facon dont on utilise le
sysème

\- What is the relationship between a use case and a scenario?

Un use case est une collection de scenario de réussite ou d'échec qui
décrit la facon don't un ou plusieurs acteurs utilisent un système pouir
atteindre un but.

> \- Identify three ways to format/express a use case.

Abrégé  scenario de base dans un paragraphe.

Informel  différents scenarios sont décrits dans plusieurs paragraphe.

Détaillé  toutes les étapes et les variatnes sont indiquées en detail,
avec les prédondition et guaranties en cas de succèes.

> \- What must be specified in a \"fully dressed\" use case?

toutes les étapes et les variatnes sont indiquées en detail, avec les
prédondition et guaranties en cas de succèes.

> \- What is an extension/alternate flow?

Elle indique tous les autres scenarios ou branchement possibles, tant en
cas de succèes qu'en cas d'échec.

> \- Give examples of special requirements.

Besoin non fonctionnel, un attribute de qualité ou une contrainte.

> \- What are the three kinds of steps in a scenario?
>
> \- What does \"essential UI-free style\" mean?

Dans le style essential, on rédige le scenario au niveau des intentions
de l'utilisateur et des responsabilités du systèe au lieu de decrier des
actions concretes. Il demeure exempt de ldétails sur la technique et les
mécanismes, en particulier ceux qui sont lies au L'IHM"

> \- What techniques are used to find use cases?

Adopter une perspective centre sur les acteurs et les buts.

> \- What is the \"boss test\"?

Votre patron vous demande : À quoi avez vous passé la journée?. Vous
répondez "je me suis connecté". Votre patron est t-il content?

> \- What is the \"EBP (PME) test\"?

Processus métier élémentaire: Tâche effectuée par une personne en un
lieu et un tmeps donnés, en réponse à un évènement, et qui ajoute rune
valeur commercial measurable et laisse les données dans un état
coherent.

> \- What is a use case diagram?

Représentation des noms des cas d'utilisation, ceux des acteurs et les
relations qui existent entre eux.

> \- What are the components of a use case diagram?

Acteur, les cas d'utilisation, système

Chapter 7 - Identifying Other Requirements

> \- What goes into the Supplementary Specification?

Les états, la documentations, le packageing, le support, les licences,
etc.

> \- What is a Vision?

Les specifications de haut niveau élaborées dan le modèle de cas
d'utilisation et dans les specifications suplémentaires ainsi que
l'étude d'opportunité du projet. Vrève vue d'ensemble qui permet de
dévouvrir rapidement les grandes idées d'un projet.

> \- What is the 4-step sequence for developing a Vision along with use
> cases?

Rédiger un bref préprojet de la Vision

Identifier les buts des utilisateurs et les cas d'utilisation
correspondant par leur nom

Rédifer certains cas d'utilisation en detail et commencer les
Spécifications Supplémentaires

Affiner la vision en résumant les informations receuillies.

> \- Comment on the author\'s \"freeze and sign off\" discussion.

Chapter 9 - Domain Models

> \- Define the term *domain model*.

Représentation visuelle des classes conceptuelles ou des objets du monde
reel dans un domaine donné. (modèle conceptual, modèle object du
domaine, modèle objet d'analyse.)

> \- What is a *conceptual class*?

Une idée, une shoes oui un objet qu'on peut considéré en terme de
symbole, d'intension et d'extension.

Symbole: mot ou image qui représente un classe conceptuelle

Intension: Définition d'une classe conceptuelle.

Exension: L'ensemble des exemples auxquels la classe conceptuelle
s'applique.

> \- Describe the difference in the way a problem is decomposed using
> structured analysis vs. using object-oriented analysis.
>
> \- What notation is used to illustrate a domain model?
>
> UML
>
> \- How does the term *abstraction* relate to modeling?
>
> \- What is the difference between a *domain model* and a *domain
> layer*?
>
> \- What is the \"representational gap\"?

Réduire le décalage de preprésentation en nommant les classes
logicielles de la couche domaine en s'insperant des noms du modèle du
domaindes avec des objets disposant d'informations et de responsabilités
familières au domaine.

> \- What are two techniques for finding conceptual classes?

Utiliser une liste de categories.

Identifier les groups nominaux.

> \- What are the four steps to building a domain model?

Tracer un diagramme de classe en mode esquisse

Utiliser un outils pour maintenir le modèle (photo, UML)

Inclure les rapports, recu dans le glossaire

Penser comme un cartographe  employé les termes du domains.

> \- What is a *description class*? Why use a description class?

Classe qui contient des informations qui décrivent quelque chose
d'autre.

Quand il est nécessaire de disposer de la description d'un produit ou
d'un service, indépendamment de l'existance actuelle de ces produitsou
de ces services.

Quand la suppression d'instances d'une entité qu'elle décrit entraine la
perte d'une information qui doit être memorise mais a été incorrectement
associée à l'entité en question.

Quand elle réduit la redondance ou la duplication des inforamtions.

> \- How does one determine whether a concept is a conceptual class or
> an attribute?

Si non pensons a une entité X en termes alphanumérique dans le monde
reel, alors X est probablement un attribute.

> \- What is an *association*?

C'est une relation entr des instances de classe qui indique un
connection significative ou intéressante.

> \- What is a *role*? (3 parts to a role)

Les extrémités des associations sont appelées roles. Nom, multiplicité,
navigabilité (fleche).

> \- What is an *attribute*?

C'est la valeur d'une données logique d'un objet.

Notation: visibilité nom: type multiplicité = défaut {propriété}

> \- What is a data type? How is it different from a class in this
> context?

Nombres, booléens, caractères, chaines de caractères, enumeration...

C'est un ensemble de valeur dont l'identité propre n'a pas de
signification dans le context de notre modèle. Les types de données sont
généralement immuables.

> \- What is a *foreign key*? Why is its use discouraged in the domain
> model?

C'est un attribute qui relie deux classes ensemble par une clé. On veut
représenter les liens entre les classes par des association.

> \- What is a *derived attribute*?

C'est un attribute qui est calculé à partir des informations continues
dans le modèle du domaine

Chapter 10 - System Sequence Diagram

> \- What does a system sequence diagram show?

Il illustre les évènements d'entrées/sorties associés aux systèmes
concerné. Il constitue la sources des contrats d'opération.

> \- Describe the notation used to draw an SSD.

:acteur, :system, lignes de vies, Messages avec paramêtres (opérations),
valeur de retour, cadre d'intéraction (loop, alt)

> \- How does one express a loop in an SSD?

Cadre identifé avec loop en haut a droite + \[condition\]

> \- How does one build an SSD? On what artifact is the SSD based?

Par l'étude d'un scenario d'un cas d'utilisation

> \- Where in the development cycle would one draw SSD\'s?

L'élaboration

> \- What are the types of events the system must react to?

Evènements généré par l'utilisateur (l'acteur)

Chapter 11 - Operation Contracts

> \- What is an operation contract?

Description des changements détaillés subis par les objets d'un modèle
du domaine et qui resulte d'une opèration du système.
Création/destruction d'instance, creation/destruction d'association ,
modifification d'attribut

> \- What is the purpose of operation contracts?

Ils fournissent des details sur l'effet des operations systèmes
impliquées dans le cas d'utilisation.

> \- What is the structure of an operation contract?

Opération, reference croisées, preconditions, postconditions.

> \- Where does one find operations in order to generate operation
> contracts

Dans le diagramme de sequence sytème

> \- What are the types of state changes that can be described in
> postconditions?

Création/destruction d'instance, creation/destruction d'association ,
modifification d'attribut

> \- What is the relationship between a system event and a system
> operation?

Systems operation will realise the system events.

Chapter 13 (12F) - Logical Architecture

> \- What is the logical architecture?

L'architecture logique définit les packages dans lesquels s'inséreront
les classes logicielles en tenant compte des contraintes arthitecturales
documentées dans les specifications supplémentaires.

> \- What is a layer?

C'est un regroupement à très forte granulatiré de classes, package et
sous-systèmes qui a une responsabilité de cohesion pour un aspect majeur
du système.

> \- What are the typical layers in an object-oriented system?

Présentation, logique applicative et objets du domaine, service
technique

> \- What is the primary benefit of structuring a system with layers?

Réduction du couplage et des dépendances. Encapulation et décomposition
de la complexité. On peut remplacer certaine couches par de nouvelle
implementation. Facilite la réutilisation et le développement en équipe.

> \- What is the model-view separation principle?

Ne pas coupler directement des objets de l'IHM avec d'autres objets du
modèle du domaine.

Ne pas placer la logique applicative dans les methods d'un objet de
L'IHM.

> \- In an object-oriented system what does one find in the model? in
> the view?

Model: logique application

View: fenêtres, pages web, applets, les états.

Chapter 14 (13F) - On To Object Design

> \- What type of diagram is commonly used to express a static model?

Diagrammes de classes conceptuelle et logicielle.

> \- What type of diagram is commonly used to express a dynamic model?

Diagrammes de sequence, diagrammes de communication

> \- What are CRC cards?

Classe-Responsabilité-Collaboration offrent une technique de
modélisation orientée texte

> \- What does CRC stand for?

Classe-Responsabilité-Collaboation

> \- What are CRC cards used for?

Modelisation des classes logicielles

Chapter 15,(14F) - UML Interaction Diagrams (Notation)

> \- What are the two different types of interaction diagrams?

Diagramme de sequence

Diagramme de communication

> \- What is an advantage of each type of interaction diagram over the
> other?

Sequence: indique clairement la sequence et l'ordonnancement des
message. Consomme trop d'espace horizontale

Communication: économique en termes d'espace, permet l'ajout d'objets
dans les deux dimensions. Lecture des sequences de message plus
difficile.

> \- Notations:

messages

returns

activation box

message to self

object creation

life lines

conditional message

iteration

iteration over a collection

message to a class (static call)

synchronous vs. asynchronous calls

Chapter 16 (15F)- UML Class Diagrams

> \- How does a design class diagram differ from the class diagram used
> for the domain model?

On y indique les methods de chaque classes

> \- What are the two options for showing attributes in a design class
> diagram and how does one decide which one to use?

Texte et ligne d'association

> \- What is generalization and how is it drawn in a UML class diagram?

Relation taxonomique entre un classificateur plus généraleet un
classificateur plus spécifique. Chaque instance du classificateur
spécifique est également une instance indirecte du classificateur
general.

> \- Give an example of generalization.
>
> \- What is composition and how is it drawn in a UML class diagram?

Une instance de la partie A appartient à seulement une instance
composite à la fois. La partie doit toujorus appartenir a un tout
composite. L'élément composite est responsible de la
creation/destruction de sys composantes.

> \- Give an example of composition.

Main avec ses doigts.

> \- What is a dependency relationship and how is it drawn in a UML
> class diagram?

Relation de dépendance indique quu'un element client a connaissance d'un
autre element fournisseur et que toute modification du fournisseur peut
affecter le client. Représenté par une fleche pointillé entre les deux
classes.

> \- Give an example of a dependency relationship.

Client-\>fournisseur

> \- What is the difference between an operation and a method?

Opération: MDD, method DCC

> \- Where does one find operations in the various artifacts we have
> covered in this course?

DSS

Chapter 17 (16F) - GRASP - Designing Objects with Responsibilities

> \- What is the fundamental activity when doing object-oriented design?

Application de patron de conception

> \- What is a responsibility?

Abstraction de ce que les objets doivent faire.

> \- What are the two general types of responsibilities? Give examples
> of each.

Responsabilité de faire

Responsabilité de savoir

> \- What is a \"design pattern\"?

Répertoire de principes généraux et de solution idiomatiques qui les
guident lorsqu'ils créent des logiciels.

> \- Who is \"GoF\"?

Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides

> \- What does GRASP stand for?

General responsibility assignment software pattern.

> \- Name the 9 GRASP patterns.

Créateur, expert en information, faible couplage, controleur, forte
cohesion, polymorphisme, protection de variation, indirection,
Fabrication pure

> \- How does one apply the *Information Expert* pattern? Give an
> example.

Affecteur la reponsabilité à la classe qui détient l'information pour
s'acquiter de la responsabilité

> \- How does one apply the *Creator* pattern? Give an example.

La responsabilité de créer une classe incombe è la classe qui agrège,
contient, enregistre, utilise étroitement ou dispose des données
d'initialisation de la classe à créer

> \- What is *coupling*?

Affecter les reponsabilité de sorte que la relation entre les classe
reste failbe.

> \- What are the the benefits of *low coupling*?

Minimise l'impact des modifications d'une classe

> \- What is *cohesion*?

Affecter les responsabilité de sorte que la responsabilité de la classe
demeure forte

> \- What are the the benefits of *high cohesion*?

On s'assure qu'une classe n'a qu'une seule responsabilité ce qui
facilite la mise à jour du code

> \- How does one apply the *Controller* pattern? Give an example.

Affecter la responsabilité à une classe façade représnetant le système
globale, un objet racide, un équipement un sous-système majeure ou bien
un controlleur de session représentant un scenario de cas d'utilisation

> \- What are the two types of Controllers?

De façade ou de session

> \- How does one decide which type of Controller to use?

Façade: système globale, objet racine, équipement, sous-système majeure.

Session: un scenario de cas d'utilisation

> \- What is a *bloated controller*?

Un controlleur qui a une faible cohesion puique nous lui avons assigné
trop de responsabilité différentes.

> \- What is the connection between the system sequence diagrams and the
> Controller(s)?

Les operation du DSS sont implémenté par les contrôleur.

Chapter 18 (19F) - Object Design Examples with GRASP

> \- What is a *use case realization*?

C'est une description de la facon don't les cas d'utilisation sont
realises dans le modèle de conception, en termes d'objets qui
collaborent.

> \- What is an *initial domain object*?

Les operations système des DSS deviennent les messages initiaux pour les
objets contrôleur de la couche domaine.

> \- Why should one wait to do initialization design late?

Lors de l'impémentation, codez d'abord au moins un cas d'utilisation
d'initialisation. Mais , Durant la modélisation considérerz-le en
dernier, après avoir découvert ce qui doit réellement être créé et
initialisé. Puis concevez le cas d'initialisation pour prendre en charge
les besoins de réalisations des autres cas d'utilisation.

# Suggestions

## MDD,DSS,Contrats

[[http://www.banq.qc.ca/services/pret/emprunt/]{.underline}](http://www.banq.qc.ca/services/pret/emprunt/)