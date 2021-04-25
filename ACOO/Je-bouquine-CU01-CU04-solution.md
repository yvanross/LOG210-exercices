
# Étude de cas jeBouquine


## Classes conceptuelles à partir de la liste de catégorie

## Classes conceptuelle à partir des groupes nominaux


## Modèle du domaine

### CU04-MDD-Je bouquine

![](../assets/exercices.gddoc.docx/image63.png){width="6.240740376202974in" height="7.458333333333333in"}

## Diagramme de séquence système (DSS)

### CU01-DSS-Maintenir le catalogue

![](../assets/exercices.gddoc.docx/image35.png){width="6.5in" height="2.1666666666666665in"}


### CU02-DSS-Chercher ouvrage

![](../assets/exercices.gddoc.docx/image40.png){width="3.263888888888889in"
height="2.7083333333333335in"}

### CU03-DSS Gérer son panier

![](../assets/exercices.gddoc.docx/image36.png){width="3.0833333333333335in" height="3.375in"}

### CU04-DSS Effectuer une commande 

![](../assets/exercices.gddoc.docx/image50.png){width="6.5in" height="3.263888888888889in"}

## Contrats d'opération


### CU01-contrat-ajouterNouveauté

Opération : ajouterNouveauté(ouvrages)

Préconditions :

Postconditions :

-   Une instance c:Catalogue à été créé

-   C.version est devenu nouvelle version

-   Des instances o:Ouvrage ont été créées

-   o.prix est devenu ouvrage.prix

-   Des associations entre c:Catalogue et o:Ouvrage ont été formées

### CU01-Contrat-miseAJourDesStock 

Opération : miseAJourDesStock(\[\[ouvrage:String,qty:Integer,
etat:String\],\[\...\]\])

Préconditions

-   c:Catalogue existe

Postconditions

-   Des instance s:stock ont été créées

-   s.qty est devenu qty

-   s.etat est devenu état

-   des associations entre o:ouvrage et s:stock ont été créées sur la
    > base de correspondance avec ouvrage

-   

### CU01-contrat- validerCatalogue 

Opération : validerCatalogue(catalogue:String,valide:Boolean)

Préconditions

-   c:Catalogue existe

-   l:Libraire existe

Postconditions

-   c.valide est devenu valide

-   Une association a été créée entre c:Catalogue et l:Libraire

### CU02-contrat- demarrerRecherche 

Opération : demarrerRecherche(texte:String)

-   Aucune postconditioncontrat

### CU02-Contrat-selectionOuvrage

Opération : selectionOuvrage(ouvrage:Ouvrage)

Préconditions :

Postcondition : Aucune

### CU03-contrat ajouterAuPanier 

**Opération : (ouvrage: Ouvrage)**

-   Une association a été créé entre p:Panier et ouvrage:Ouvrage sur la
    > base de correspondence avec ouvrage

### CU04-contrat demarrerCommande 

**Opération : demarrerCommande (p: Panier)**

-   Une instance c:Commande à été créée

-   Des instances ci:CommandeItem ont été créées sur la base de
    > correspondence avec commandeItem de p:Panier

-   Des association ont été créés entre c:Commande et les
    > ci:CommandeItem

-   ~~C.commande a été associé à cl:client~~

-   ~~Des associations entre c:Commande et o:Ouvrage ont été créées sur
    > la base de correspondence des instance de p:Panier~~

-   Les associations entre o:Ouvrage et p:Panier sont détruites

### CU04-contratSaisirAdresses

**opération: SaisirAdresses(adresseLivraison:Adresse,
adresseFacturation:Adresse)**

-   Une instance al:adresse à été créée

-   Tout les attribute de al:Adresse sont devenu égale aux attributs de
    > adresseLivraison.

-   Une instance af:Adresse à été créé

-   Tout les attribute de af:Adresse sont devenu égale aux attributs de
    > adresseFacturation.

-   Une association entre cl:Client et af:Adresse à été créée sur la
    > base de correspondence avec adresseFacturation

-   Une association entre cl:Client et al:Adresse à été créée sur la
    > base de correspondence avec adresseLivraison

-   Une association entre c:Commande et af:Adresse

-   Une association entre c:Commande et al:Adresse

### CU04-contratValiderCommande

opération: ValiderCommande(no:String, date:String)

-   Une instance cc:Carte de credit à été créée

-   Une association entre cl:Client et cc:Carte à été créée

-   Carte.no est devenu no

-   Carte.date est devenu date

##c6.8 Réalisation des cas d'utilisation

### CU01-RDCU-ajouterNouveauté 

![](../assets/exercices.gddoc.docx/image48.png){width="6.5in" height="4.208333333333333in"}

### CU01-RDCU-miseAJourDesStock v1

![](../assets/exercices.gddoc.docx/image51.png){width="6.5in" height="5.180555555555555in"}

### CU01-RDCU- miseAJourDesStock v2

![](../assets/exercices.gddoc.docx/image46.png){width="6.5in" height="5.180555555555555in"}

### CU01-RDCU- validerCatalogue 

![](../assets/exercices.gddoc.docx/image41.png){width="6.5in" height="3.138888888888889in"}

### CU02-RDCU- demarrerRecherche

![](../assets/exercices.gddoc.docx/image82.jpg){width="6.5in"
height="4.875in"}![](../assets/exercices.gddoc.docx/image42.png){width="6.5in"
height="2.0833333333333335in"}

### CU02-RDCU-selectionOuvrage

![](../assets/exercices.gddoc.docx/image58.png){width="6.5in" height="2.3194444444444446in"}

### CU03-RDCU-ajouterAuPanier-V1

> ![rossypro:Users:rossypro:GDrive:cc-yvan.ross\@etsmtl.net:LOG210
> Collaboration
> enseignants:exercices:MDD-DSS-Contrats-RDCU:5-je-bouquine:screenshots:RDCU\_ajouterPanier\_g01.JPG](../assets/exercices.gddoc.docx/image54.jpg){width="6.48125in"
> height="4.863888888888889in"}

### CU04-RDCUajouterAuPanier-V2 

![](../assets/exercices.gddoc.docx/image103.jpg){width="6.5in" height="4.875in"}

### CU04-RDCUdemarrerCommande-V0 

![](../assets/exercices.gddoc.docx/image43.png){width="6.5in" height="5.583333333333333in"}

### CU04-RDCUdemarrerCommande-V1

![](../assets/exercices.gddoc.docx/image10.jpg){width="6.5in" height="4.875in"}

### CU04-RDCUSaisirAdresses

![rossypro:Users:rossypro:GDrive:cc-yvan.ross\@etsmtl.net:LOG210
Collaboration
enseignants:exercices:MDD-DSS-Contrats-RDCU:5-je-bouquine:screenshots:RDCU\_saisirAdresse\_g01.JPG](../assets/exercices.gddoc.docx/image56.jpg){width="6.48125in"
height="4.863888888888889in"}

### CU04-RDCUValiderCommande 

**RDCU manquant**
