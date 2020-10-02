# Accès au métro

## Diagramme de cas d'utilisation

![](/assets/exercices.gddoc.docx/image96.png)

## Cas d'utilisation

### CU01-Recharger la carte

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

**Le Client.** Il veut un moyen efficace d'ajouter des passages sur sa
carte d'accès au métro. Il veut une preuve d'achat des passages pour le
rapprochement de son compte de carte de crédit. Il y a plusieurs
stations de métro dans la ville et chacune possède des kiosques
transactionnels pour que le client puisse ajouter des passages sur sa
carte a puce.

**L'entreprise.** Elle veut enregistrer correctement les achats de
passages. Elle veut satisfaire les souhaits des clients tout en libérant
les caissiers au guérites pour qu'ils puisse offrir un meilleur service
à la clientèle.

**Le Système externe d'autorisation de paiement :** Reçoit et traite les
demande d'autorisation de paiement fait par les kiosques.

****Préconditions:****

Le client possède une carte à puce du métro.

**Garanties en cas de succès (postconditions) :**

La vente de passage (recharge) est enregistrée. (La taxe est calculée)?
Le nombre de nouveaux passages est ajouté sur la carte à puce. La
comptabilité est mise à jour. La carte de crédit du client est facturée.
Le reçu est généré. Les autorisations de paiement sont enregistrés.

**Scénario principal (succès):**

> 1\. Le Client se présente à un kiosque transactionnel d'une station de
> métro et désire ajouter des passages sur sa carte à puce.
>
> 2\. Le client place sa carte à puce sur le lecteur de carte du
> kiosque.
>
> 3\. Le kiosque détecte la présence de la carte et affiche le nombre de
> passages restant et offre au client d'ajouter 10 ou 20 passages
> supplémentaires.
>
> 4\. Le client choisi de prendre 10 passages.
>
> 5\. Le système affiche le nombre de passage désiré et le détail de la
> facture incluant le montant total et demande une carte de crédit pour
> le paiement.
>
> 6\. Le Client met sa carte de crédit dans le lecteur.
>
> 7\. Le système détecte la carte et envoie une demande d'autorisation à
> un Système d'autorisation des paiements externe et attend une
> approbation.
>
> 8\. Le Système reçoit l'accord et l'indique au Client. Le système
> ajoute les passages sur la carte à puce du client. Le Système
> enregistre la quantité de passages achetés, l'heure, la date, le
> montant et le no d'autorisation de la transaction et les informations
> sur le client, la carte a puce et la carte de crédit utilisé.
>
> 9\. Le système indique au client qu'il peut retirer sa carte à puce et
> sa carte de crédit.

 

### CU02-Faire un passage

**Acteur principal: Le client**

**Parties prenantes et intérêts:**

**L'entreprise.** Elle veut enregistrer correctement les passages des
ses usager et conserver la date, l'heure et le lieu du passage. Elle
veut offrir un service de qualité à ses clients pour traiter le plus
rapidement possible les passages aux bornes d'accès et minimiser les
files d'attentes.

**Pré-conditions:**

Le client possède une carte à puce du métro et celle-ci à au moins 1
passage.

**Garanties en cas de succès (Post-conditions) :**

Le client est passé à la borne d'accès, sa carte à puce à été débité
d'un passage.

**Scénario principal (succès):**

> 1\. Le client prend sa carte, se dirige vers une borne d'accès,
> présente sa carte sur le lecteur pour faire une demande de passage.
>
> 2\. Le système demande à la carte le nombre de passage restant
>
> 3\. Le système autorise le passage du client et met le nombre de
> passage à jour sur la carte à puce. La borde d'accès débloque le
> tourniquet, en affichant la lumière verte et le nombre de passage
> restant.

**Glossaire**:

**Carte à puce**: Carte contenant un micro-processeur et de la mémoire
permettant de conserver de l'information pour effectuer des transactions
sans utiliser une carte de crédit.

**Borne d'accès** Une borne d'accès est un système permettant de bloquer
l'accès au métro ou de laisser passer les clients lorsqu'il ont payé
leur passage. Il possède un afficheur numérique et deux lumière pour
indiquer l'état de la transaction. La lumière rouge indique que le
passage n'est pas autorisé, la lumière verte indique que le passage est
autorisé.

## Classes conceptuelles à partir de la liste de catégorie

## Classes conceptuelles à partir des groupes nominaux

## Modèle du domaine

### CU02-MDD

![](/assets/exercices.gddoc.docx/image100.png){width="6.375in" height="5.34375in"}

## Diagrammes de séquence système (DSS)


### CU01-DSS-Recharger la carte
![](/assets/exercices.gddoc.docx/dss-recharger-la-carte.png){width="6.375in" height="5.34375in"}
### CU01-Contrat-placerCarteAPuce

> **Operation:** placerCarteAPuce()
>
> **Référence:** CU01-2 Rechargé la carte,
>
> **Préconditions:**
>
> **PostConditions:**
>
> ● une instance de carte à puce à été créée

### CU01-RDCU-placerCarteAPuce

![](http://www.plantuml.com/plantuml/img/bPD1JiCm44NtFiMecy82iQzA9OHOKK4bsB5otMaxaDYkPuBWHdJF3N8nnar9WneGI54KZ_E_tlzE-9byjCcMmF9MeDuJEQdAmWY9hcDX7QOhcmGlPvN3arFZWo0Kk1G8InYCheAN50giqWq5tbGuC3ERmELn_P7di41OMcSNQExcJoWGrszC-YQSGxtTL1InH2y6_GAokJ6FPvDUPnZr0HbZdT2BLQnU79TmlzUg1aSfEbix_5HlLLGb4olADk26oA8AU6vyZO933Cpr-o8xwUMoG6UgAb4awSo2oyvWuIcFsuYzwPhK1nADEnutz9D9GvnejVwzU7oDcBJZFVR1pkGZ8Iqwm_fGpfLFoQDbjYlyFvgVpnefNC0AvVPhoVb8_W0RZs17OAPjlrfPvH5UY6bE1Kcz1TPsjL4MAnIycRQFFxqxrBG9OoB-KxxxnYs7aoRKWqsq9BSRzyNwKdJ3w0VkmhhUSWRR9pF5_rZbsph_JDuIwy4nI0U9kwbQ-bsMwrRzInpp2G00){width="6.5in"
height="4.416666666666667in"}

### CU01-Contrat-choixPassage

> **Operation:** choixPassage(nbPassage)
>
> **Référence:** CU01-4 Rechargé la carte
>
> **Préconditions:**
>
> - une instance carteAPuce de CarteAPuce existe
>
> **PostConditions:** Aucune

### CU01-RDCU-choixPassage

![](http://www.plantuml.com/plantuml/img/VP2nJiD038PtFuNL1HWYzWnTc10ITE_aN9p4aDnTVKxLFb9ttY0lngK52TIKnJh_idvztwKFyP6K1ansx3bF5MVZq8E9vTrrGGuRIebQ1X-CiUV6C3IuAf-2DmqzZ_eY8Ur6Ni665DqSJvzpZZLZGuvgXhVgdGrZTqoIB_4HfzDkbCW3UmFsDSxb0DjYlTYCvH-KUrzzlyfdRzooFW00EPCzPSR5XWk-IjlTvh-Aa9DXVyU7o6eGmtZsIwnxrlmLcNgebBCdn0iFdczwmgZ1TIIUCSJff6GI_2_HHSIYMD-GJsolrRKyoe_zl-vV)

### CU01-Contrat-saisirCarteCredit

> **Operation:** saisirCarteCredit(no:String,expiration:String)
>
> **Référence:** CU01-6 Rechargé la carte
>
> **Préconditions:**
>
> - une instance carteAPuce de CarteAPuce existe
>
> - Une instance kiosque de Kiosque existe
>
> - le nombre de passage à ajouter est dans la session
>
> - le montant de la transaction à été ajouté a la session
>
> - une instance entreprise:Entreprise existe
>
> **PostConditions:**
>
> - Une instance de carte de crédit à été crée
>
> - Une instance paiement de Paiement à été créé
>
> - Une association entre l\'instance paiement de Paiement et la
> CarteDeCrédit à été créé
>
> - L\'instance paiement de Paiement à été associé à la carte à puce
>
> - L\'instance paiement de Paiement à été associé au kiosque
>
> - paiement.quantite\_passage est devenu quantité nbPassage
>
> - paiement.date est devenu la date courante
>
> - paiement.heure est devenu l\'heure courante
>
> - paiement.montant est devenu montant
>
> - carteAPuce.nbPassage est devenu CarteAPuce.nbPassage+nbPassage
>
> - une instancea authorisationPaiement de AuthorisationPaiement à été
> créé
>
> - authorisationPaiement.numero\_autorisation est devenu
> numero\_autorisation
>
> - autorisationPaiement à été associé à paiement
>
> - une association à été créé entre entreprise:Entreprise et
> paiement:Paiement

### CU01-RDCU-saisirCarteCredit-V1

![](/assets/exercices.gddoc.docx/image64.png){width="6.375in" height="3.71875in"}

### CU01-RDCU-saisirCarteCredit-erreurs-typiques

![](/assets/exercices.gddoc.docx/image33.png){width="6.5in" height="3.6805555555555554in"}

-   nom de l'opération?

-   ControlleurSession -\> ControleurPaiement?

-   Contrôleur kiosque au lieu de contrôleur de session?

-   ControlleurSession n'a pas de visibilité sur paiement

-   CarteDeCrédit n'a pas de visibilité sur Paiement

-   ~~Kiosque n'a pas de visibilité sur Paiement~~

-   SetMontant(montant), setQty(qty) -\> ajouterPassages(montant,qty) -
    > de couplage

-   Paiement n'a pas de visibilité sur CarteAPuce

-   Paiement n'a pas de visibilité sur Entreprise

-   Entreprise - Paiement =\> redondance d'association, est-ce
    > nécessaire.

### CU02-DSS-Faire un passage

![](/assets/exercices.gddoc.docx/image7.png){width="4.770833333333333in"
height="3.6458333333333335in"}

## Contrats d'opération

### CU02-Contrat-debiterPassage

> **Operation:** debiterPassage()
>
> **Référence:** CU02-1 Faire un passage
>
> **Préconditions:**
>
> une instance carteAPuce de CarteAPuce existe
>
> des instances non utilisé de Passage existent
>
> une instance borne de Borne existe
>
> **PostConditions:**
>
> carteAPuce.nbPassege est devenu carteAPuce.nbPassage-1

## Réalisation des cas d'utilisation

### CU02-DSS-debiterPassage

RDCU Manquant

**9 Compagnie aérienne**

## Diagramme de cas d'utilisation

## Cas d'utilisations


### CU01-Ajouter nouveau vol

****Préconditions:** L'administrateur est identifié et authentifié.**

**Scénario principal:**

> 1\. L'administrateur démarre l'ajout d'un vol dans la compagnie
> aérienne.
>
> 2\. L'administrateur saisit le numéro du vol, le jour de la semaine,
> l'heure de départ, l'heure d'arrivée, la période de validité,
> l'aéroport de départ et l'aéroport de destination.
>
> 3\. Le système affiche les informations du nouveau vol.

## Classes conceptuelles à partir de la liste des catégories

## Classes conceptuelles à partir des groupes nominaux

## Modèle du domaine (MDD)


### CU01-MDD-Ajouter nouveau vol

![](/assets/exercices.gddoc.docx/image85.png){width="6.5in" height="3.9166666666666665in"}


## Diagramme de séquence système (DSS)

### CU01-DSS-Ajouter nouveau vol

![](/assets/exercices.gddoc.docx/image32.png){width="6.5in" height="3.6666666666666665in"}

## Contrats d'opération

### CU01-Contrat-Ajouter nouveau vol

## Réalisation des cas d'utilisations


### CU01-RDCU-
