# Location de vélo (inspiré de Bixi) 


### CU01-Traiter abonnement

| **Catégorie du Tableau 9.1**     |  **Classe d'utilisation**           |  **Référence au cas conceptuelle** |
| -- | -- | -- | 
| transaction métier | Abonnement|-|
| lignes d'une transaction |  autorisation paiement | -|
| produit ou service lié à une transaction ou à une ligne d'une transaction | emprunt |-|
| où la transaction est enregistrée |  Système de réservation |-|
| lieu de la transaction; lieu du service|-|-|
| rôle des personnes; acteurs |  Client,entreprise,système de réservation |-|
| événements notables | Abonnement |-|
| objets physiques | carte crédit,recu,clé d'accès |-|
| descriptions d'entités |-|-|
| catalogues |-|-|
| conteneurs |-|-|
| contenu d'un conteneur |-|-|
| autres systèmes externes |  Autorisation Paiement |-|
| documents financiers,contrats,documents légaux | Abonnement |-|
| instruments financiers, algorithme |-|-|
| plannings, manuels, documents régulièrement consultés pour effectuer un travail | - |-|

### CU02-Emprunter vélo

| **Catégorie du Tableau 9.1**    | **Classe conceptuelle**          | **Référence au cas d'utilisation**|
|-|-|-|
| transaction métier | Abonnement         |-|
| lignes d'une transaction      | authorisation paiement     |-|
| produit ou service lié à une transaction ou à une ligne d'une transaction.| emprunt            |-|
| où la transaction est enregistrée  | Système de réservation        |-|
| lieu de la transaction; lieu du service       |-|-|
| rôle des personnes; acteurs dans les cad d'utilisation        | Client,entreprise,système de réservation              |-|
| événements notables        | Abonnement         |-|
| objets physiques   | carte crédit,recu,clé d'accès,vélo, Station,pts encrage          |-|
| descriptions d'entités      |-|-|
| catalogues         |-|-|
| conteneurs         | station            |-|
| contenu d'un conteneur      | vélo               |-|
| autres systèmes externes   | Autorisation Paiement      |-|
| documents financiers, contrats, documents légaux        | Abonnement         |-|
| instruments financiers, algorithmes       |-|-|
| plannings, manuels, documents régulièrement consultés pour effectuer un travail    |-|-|

### CU03-Rendre vélo

### CU04-Demander extension de temps

### CU05-Demander nouvelle clé d\'accès



### CU04-MDD-Location Vélo

![](/assets/exercices.gddoc.docx/image38.png)

## Diagramme de séquence système (DSS)

### CU01-DSS-Abonnement

![](/assets/exercices.gddoc.docx/image37.png){

### CU02-DSS-Emprunter vélo

![](/assets/exercices.gddoc.docx/image13.png){

### CU03-DSS-Rendre Vélo

### ![](/assets/exercices.gddoc.docx/image65.png)
### CU04-DSS-Demander extension de temps

![](/assets/exercices.gddoc.docx/image84.png)

### CU05-DSS-Demander nouvelle clé

![](/assets/exercices.gddoc.docx/image71.png)

 

5.7 Contrats d'opération


### CU01-Contrat-démarrerAbonnement

**Opération:** démarrerAbonnement(durée :Entier)

Préconditions :

Une instance de borne existe

**Postconditions :**

> -une instance *a* d'Abonnement a été créée
>
> \-*a.dateHeureDébut* et *a.dateHeureFin* ont été initialisés selon
> *durée*
>
> \-*a* a été associé à la Borne
>
> -\[*a* ne peut être associé au Client, puisque Client.nom est
> inconnu\]
>
> -\[*a* ne doit pas être associé à un Prêt, puisqu'il ne s'agit pas
> d'un prêt\]

### CU01-Contrat-saisirCarteCrédit

**Opération:** saisirCarteCrédit (numéro :Entier, dateExpir :Entier)

**Postconditions :**

> -une instance *p* de Paiement a été créée
>
> -une instance *cc* de CarteCrédit a été créée
>
> \-*cc.numéro* et *cc.dateExpiration* ont été initialisés selon
> *numéro* et *dateExpir*
>
> \-*cc* a été associée à l'instance p :Paiement
>
> \- p.Paiement a été associé à l'Abonnement en cours

### CU01-Contrat-confirmerAbonnement

**Opération:** confirmerAbonnement (estConfirmé : Booléen)

Préconditions :

Une instance p de Paiement existe

**Postconditions :**

> \-*p.montant* a été initialisé
>
> -p.approbation est devenu noApprobation
>
> -une instance *ca* de CléAccès a été créée
>
> \-*ca.identifiant* a été initialisé
>
> \-*ca.estActivée* est devenu vrai
>
> \-*ca* a été associée à l'Abonnement en cours

### CU02-Contrat-demarrerEmprunt

**Opération:** demarrerEmprunt()

**Postconditions :**

-   Une instance emprunt:Emprunt a été créée

-   emprunt.dateDebut est devenu maintenant

-   emprunt.heureDebut est devenu maintenant

-   emprunt.estTermine est devenu faux

### CU02-Contrat-emprunterVelo

**Opération:** emprunterVelo(cléAccess: integer)

**Postconditions :**

-   Une association a été créée entre emprunt et Abonnement sur la base
    > de correspondance avec cléAccess

-   ~~Une association entre GrandLivre et emprunt:Emprunt a été créée~~

### **5.7.6 CU02-Contrat-retirerVelo**

**Opération:** retirerVelo(identifiantPointAncrage:integer,
identifiantVelo:integer)

**Postconditions :**

-   Une association a été créée entre emprunt et Velo sur la base de
    > correspondance avec identifiantVelo

-   Une association entre velo:Velo et PointAncrage a été détruite sur
    > la base de correspondance avec identifantPointAncrage

### CU03-Contrat-ancrerVelo

**Opération:** ancrerVelo(velo: string, identifiantPointAncrage:integer)

**Postconditions :**

-   Une association a été créée entre Velo et PointAncrage sur la base
    > de correspondance avec vele et identifiantPointAncrage

-   Une instance p:Paiement a été créée

-   Une association entre p:Paiement et Emprunt a été créée sur la base
    > de correspondance avec velo

-   Une association a été créée entre p:Paiement et CarteCredit sur la
    > base de correspondance avec velo, emprunt:Emprunt,
    > abonnement:Abonnement, client:Client et carteCredit:CarteCredit

-   Une association a été créée entre SystèmeAutorisationPaiementAcredit
    > et p:Paiement

### CU04-Contrat-demanderExtensionTemps

**Opération:** demanderExtensionTemps()

**Postconditions :** Aucune

### CU04-Contrat- ajouterTemps

**Opération:** ajouterTemps(carteCrédit:integer)

**Postconditions :**

-   Une instance p:Paiement a été créée

-   Une association entre p:Paiement et Emprunt a été créée sur la base
    > de correspondance avec la carteCredit, le client et l'abonnement

-   Une association entre p:Paiement et CarteCredit a été créée sur la
    > base de correspondance avec carteCredit

-   emprunt.dateHeureFin est devenu emprunt.dateHeureFin + nouveau délai

### CU05-contrat-demanderNouvelleCle

**Opération:** demanderNouvelleClé()

**Postconditions :** Aucune

### CU05-contrat-nouvelleClé

**Opération:** nouvelleClé(carteCrédit:integer)

**Postconditions :**

-   Une instance ca:CleAcces a été créée

-   Une association entre ca:CleAcces et Abonnement a été créée sur la
    > base de correspondance avec carteCredit

-   Une association entre ca:CleAcces et Emprunt a été créée sur la base
    > de correspondance avec paiement et carteCredit.

## Réalisation des cas d'utilisation (RDCU) 


### CU01-RDCU-démarrerAbonnement

![](/assets/exercices.gddoc.docx/image53.jpg)
### CU01-RDCU-saisirCarteCrédit

![](/assets/exercices.gddoc.docx/image107.jpg)
### CU01-RDCU-confirmerAbonnement

![](/assets/exercices.gddoc.docx/image81.jpg){
    
### CU02-RDCU-demarrerEmprunt

TODO

### CU02-RDCU-emprunterVelo

TODO

### CU02-RDCU-retirerVelo

TODO

### CU03-RDCU-ancrerVelo

TODO

### CU04-RDCU-demanderExtensionTemps

TODO

### CU04-RDCU- ajouterTemps

TODO

### CU05-RDCU-demanderNouvelleCle

TODO

### CU05-RDCU-nouvelleClé

TODO

 