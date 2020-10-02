# Location de vélo (inspiré de Bixi) 

Dans ce cas d'étude, nous nous inspirons du système de Bixi à Montréal.
Il s'agit d'un service de prêt de vélo en ville géré par une entreprise.
Un client doit d'abord s'abonner au système utilisant une carte de
crédit, puis il peut emprunter un vélo pour un temps limité. Le vélo
doit être rendu avant un délai, sinon le client est facturé (par la
carte de crédit qu'il a utilisée pour son abonnement) des frais de
retard.

Il y a plusieurs stations dans la ville où les clients abonnés peuvent
emprunter les vélos. À chaque station, il y a une borne transactionnelle
et plusieurs points d'ancrage. Chacun de ces points peut héberger un
vélo avec un mécanisme de verrouillage. On donne une clé d'accès (qui
n'est qu'un code à 4 chiffres) au client dès qu'il s'abonne. Cependant,
ce code n'est que temporaire et doit être renouvelé après chaque emprunt
de vélo.

## Diagramme de cas d'utilisation

![](/assets/exercices.gddoc.docx/image44.png){width="5.416666666666667in"
height="5.010416666666667in"}

Figure 1 Diagramme des cas d\'utilisation du système de prêt de vélo

## Cas d'utilisations


### CU01-Traiter abonnement

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le Client.** Il veut un moyen efficace de s'abonner au système. Il
    > veut une preuve d'achat d'abonnement pour le rapprochement de son
    > compte de carte de crédit.

-   **L'Entreprise.** Elle veut enregistrer correctement les abonnements
    > et les transactions. Elle veut satisfaire les souhaits des
    > clients.

**Préconditions:**

Le client possède une carte de crédit.

**Postconditions-Garanties en cas de succès :**

L'abonnement est enregistré. Le reçu est généré. Les autorisations de
paiement sont enregistrées.

**Scénario principal (succès):**

1.  Le Client se présente à la borne d'une station de vélo et désire
    > s'abonner au service d\'emprunt de vélo.

2.  Le Client démarre un nouvel abonnement, indiquant la durée de
    > l'abonnement (24 ou 72 heures);

3.  Le Système affiche la durée et le prix pour l'abonnement spécifié et
    > demande une carte de crédit pour le paiement.

4.  Le Client présente sa carte de crédit à la borne.

5.  Le Système affiche de nouveau la durée et le prix, ainsi que les
    > conditions de l'abonnement, et demande une confirmation.

6.  Le Client confirme qu'il veut payer son abonnement.

7.  Le Système envoie une demande d'autorisation à un Système
    > d'autorisation des paiements externe et demande une approbation.

8.  Le Système reçoit l'accord et l'indique au Client. Le Système
    > enregistre l'abonnement et affiche le code de la clé d\'accès pour
    > le premier emprunt de vélo.

**Scénarios alternatifs**

2-6a. En tout temps, le Client annule l'abonnement.

1.  Fin du cas d\'utilisation.

4a. Carte de crédit invalide:

1.  Le Système affiche un message indiquant que la carte n'est pas
    > valide.

2.  Retour à l'étape 4.

8a. Le Système reçoit un échec pour la demande d'autorisation.

1.  Le Système signale l'erreur au Client.

2.  Fin du cas d'utilisation.

### CU02-Emprunter vélo

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le Client.** Il veut un moyen efficace d'emprunter un vélo.

-   **L'Entreprise.** Elle veut enregistrer correctement les
    > informations à propos du vélo emprunté (le Client, la date,
    > l'heure, le vélo). Elle veut satisfaire les souhaits des clients.

**Préconditions:**

Le client est abonné au Système et possède une clé. Il y a au moins un
vélo qui n'est pas en panne présent à son point d'ancrage de la station.

**Garanties en cas de succès (postconditions) :**

L'emprunt du vélo est enregistré. La quantité de vélos disponibles est
mise à jour.

**Scénario principal (succès):**

1.  Le Client se présente à un point d'ancrage ayant un vélo et désire
    > emprunter le vélo.

2.  Le Client entre le code de sa clé d\'accès.

3.  Le Système déverrouille le point d'ancrage et indique que le vélo
    > peut être retiré.

4.  Le Client retire le vélo du point d'ancrage.

5.  Le Système enregistre l'emprunt du vélo.

**Scénarios alternatifs**

2a. Code de la clé d\'accès invalide:

1.  Le Système indique que le code de la clé d\'accès n'est pas valide.

2.  Fin du cas d'utilisation

4a. Le Client ne retire pas le vélo du point d'ancrage avant 15
secondes.

1.  Le Système verrouille le point d'ancrage sans enregistrer un emprunt
    > de vélo.

2.  Fin du cas d'utilisation

3.  Déterminez les concepts dans le cas d\'utilisation CU4-1

### CU03-Rendre vélo

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le Client.** Il veut un moyen efficace de rendre un vélo.

-   **L'Entreprise.** Elle veut enregistrer correctement les
    > informations à propos du vélo rendu (le Client, la date, l'heure,
    > le vélo). Elle veut satisfaire les souhaits des clients.

**Préconditions:**

Le client possède un vélo emprunté. Il y a au moins un point d'ancrage
libre à la station.

**Garanties en cas de succès (postconditions) :**

Le retour du vélo est enregistré. La quantité de vélos disponibles est
mise à jour.

**Scénario principal (succès):**

1.  Le Client se présente avec le vélo devant un point d'ancrage libre à
    > une station.

2.  Le Client rentre le vélo dans le point d'ancrage libre.

3.  Le Système verrouille le point d'ancrage et indique que le vélo a
    > été rendu.

4.  Le Système enregistre le retour du vélo, calcule le temps pour
    > l'emprunt, et facture la carte de crédit du Client si les frais
    > s'y appliquent.

**Scénarios alternatifs**

2a. Le mécanisme de verrouillage est défectueux:

1.  Le Système indique l'impossibilité de verrouiller le point
    > d'ancrage.

2.  Fin du cas d'utilisation

5\. Le client veut signaler que le vélo qu'il vient de rendre a un
problème.

1.  Le client indique que le vélo qu'il a rendu est a un problème.

2.  Le Système registre le fait que le vélo est défectueux et
    > l'information est indiquée au point d'ancrage.

### CU04-Demander extension de temps

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le Client.** Il veut un moyen efficace d'avoir plus de temps pour
    > rendre un vélo.

-   **L'Entreprise.** Elle veut enregistrer correctement l'extension de
    > temps pour le vélo emprunté. Elle veut satisfaire les souhaits des
    > clients.

**Préconditions:**

Le client possède un vélo emprunté. Il se trouve à une station n'ayant
aucun point d'ancrage libre.

**Garanties en cas de succès (postconditions) :**

L'extension de temps pour le vélo emprunté est enregistré.

**Scénario principal (succès):**

1.  Le Client se présente à la borne transactionnelle d'une station.

2.  Le Client demande une extension de temps.

3.  Le Système demande la carte de crédit du Client.

4.  Le Client présente sa carte de crédit.

5.  Le Système affiche l'heure du nouveau délai et enregistre
    > l'extension de temps pour le client.

**Scénarios alternatifs**

2-4a. En tout temps, le Client annule l'extension.

1.  Fin du cas d\'utilisation.

4a. Carte de crédit invalide:

1.  Le Système indique que la carte de crédit n'est pas valide.

2.  Retour à l'étape 3.

### CU05-Demander nouvelle clé d\'accès

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le Client.** Il veut un moyen efficace d'emprunter encore un vélo

-   **L'Entreprise.** Elle veut empêcher que les codes d'accès soient
    > réutilisés par des personnes non abonnées au système. Elle veut
    > satisfaire les souhaits des clients.

**Préconditions:**

Le client est abonné, mais son code de clé d\'accès a déjà été utilisé
la dernière fois qu'il a emprunté un vélo. Il se trouve à une station
ayant des vélos disponibles.

**Garanties en cas de succès (postconditions) :**

Le nouveau code de clé d\'accès pour le client a été généré et
communiqué.

**Scénario principal (succès):**

1.  Le Client se présente à la borne transactionnelle d'une station.

2.  Le Client demande un nouveau code de clé d\'accès.

3.  Le Système demande la carte de crédit du Client.

4.  Le Client présente sa carte de crédit.

5.  Le Système génère un nouveau code de clé d\'accès et l'affiche pour
    > le client.

**Scénarios alternatifs**

2-4a. En tout temps, le Client annule la demande.

1.  Fin du cas d\'utilisation.

~~4a. Client n'est pas abonné:~~

1.  ~~Le Système indique qu'il n'existe pas d'abonnement pour la carte
    > de crédit.~~

2.  ~~Retour à l'étape 3~~.

4b. Carte de crédit invalide:

1.  Le Système indique que la carte de crédit n'est pas valide.

2.  Retour à l'étape 3.

5.3 Classes conceptuelles par catégories



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

## Classes conceptuelles à partir des nom

### CU01-Traiter abonnement

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le [Client]{.underline}.** Il veut un moyen efficace de s'abonner
    > au [système]{.underline}. Il veut une preuve d'achat
    > [d'abonnement]{.underline} pour le rapprochement de son compte de
    > [carte de crédit]{.underline}.

-   **[L'Entreprise]{.underline}.** Elle veut enregistrer correctement
    > les [abonnements]{.underline} et les transactions. Elle veut
    > satisfaire les souhaits des [clients]{.underline}.

**Préconditions:**

Le [client]{.underline} possède une [carte de crédit.]{.underline}

**Garanties en cas de succès (postconditions) :**

[L'abonnement]{.underline} est enregistré. Le [reçu]{.underline} est
généré. Les [autorisations de paiement]{.underline} sont enregistrées.

**Scénario principal (succès):**

1.  Le [Client]{.underline} se présente à la [borne d'une station de
    > vélo]{.underline} et désire s'abonner au service
    > [d\'emprunt]{.underline} de vélo.

2.  Le [Client]{.underline} démarre un nouvel [abonnement]{.underline},
    > indiquant la [durée]{.underline} de l'abonnement (24 ou 72
    > heures);

3.  Le [Système]{.underline} affiche la durée et le prix pour
    > [l'abonnement]{.underline} spécifié et demande une carte de crédit
    > pour le paiement.

4.  Le [Client]{.underline} présente sa [carte de crédit]{.underline} à
    > la borne.

5.  Le [Système]{.underline} affiche de nouveau la durée et le prix,
    > ainsi que les conditions de l'abonnement, et demande une
    > [confirmation]{.underline}.

6.  Le [Client]{.underline} confirme qu'il veut payer son
    > [abonnement]{.underline}.

7.  Le [Système]{.underline} envoie une demande d'autorisation à un
    > [Système d'autorisation]{.underline} des [paiements]{.underline}
    > externe et demande une [approbation]{.underline}.

8.  Le [Système]{.underline} reçoit l'accord et l'indique au Client. Le
    > Système enregistre [l'abonnement]{.underline} et affiche le [code
    > de la clé d\'accès]{.underline} pour le premier emprunt de vélo.

**Scénarios alternatifs**

2-6a. En tout temps, le [Client]{.underline} annule
[l'abonnement]{.underline}.

2.  Fin du cas d\'utilisation.

4a. Carte de crédit invalide:

3.  Le Système affiche un message indiquant que la [carte]{.underline}
    > n'est pas valide.

4.  Retour à l'étape 4.

8a. Le Système reçoit un échec pour la demande
[d'autorisation]{.underline}.

3.  Le Système signale l'erreur au Client.

4.  Fin du cas d'utilisation.

Déterminez les concepts dans le cas d\'utilisation CU4-1

### CU02-Emprunter vélo

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le [Client]{.underline}.** Il veut un moyen efficace d'emprunter
    > un [vélo]{.underline}.

-   **[L'Entreprise]{.underline}.** Elle veut enregistrer correctement
    > les informations à propos du [vélo]{.underline} emprunté (le
    > Client, la date, l'heure, le vélo). Elle veut satisfaire les
    > souhaits des clients.

**Préconditions:**

Le [client]{.underline} est abonné au [Système]{.underline} et possède
une [clé]{.underline}. Il y a au moins un [vélo]{.underline} qui n'est
pas en panne présent à son [point d'ancrage]{.underline} de la
[station]{.underline}.

**Garanties en cas de succès (postconditions) :**

[L'emprunt]{.underline} du [vélo]{.underline} est enregistré. La
quantité de vélos disponibles est mise à jour.

**Scénario principal (succès):**

1.  Le [Client]{.underline} se présente à un [point
    > d'ancrage]{.underline} ayant un [vélo]{.underline} et désire
    > emprunter le [vélo]{.underline}.

2.  Le [Client]{.underline} entre le [code de sa clé
    > d\'accès]{.underline}.

3.  Le Système déverrouille le [point d'ancrage]{.underline} et indique
    > que le [vélo]{.underline} peut être retiré.

4.  Le [Client]{.underline} retire le vélo du [point
    > d'ancrage]{.underline}.

5.  Le [Système]{.underline} enregistre [l'emprunt]{.underline} du
    > [vélo]{.underline}.

**Scénarios alternatifs**

2a. [Code de la clé d\'accès]{.underline} invalide:

3.  Le [Système]{.underline} indique que le code de la [clé
    > d\'accès]{.underline} n'est pas valide.

4.  Fin du cas d'utilisation

4a. Le [Client]{.underline} ne retire pas le [vélo]{.underline} du point
d'ancrage avant 15 secondes.

4.  Le [Système]{.underline} verrouille le [point d'ancrage]{.underline}
    > sans enregistrer un [emprunt]{.underline} de vélo.

5.  Fin du cas d'utilisation

6.  Déterminez les concepts dans le cas d\'utilisation CU4-1


### CU03-Rendre vélo

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le [Client]{.underline}.** Il veut un moyen efficace de rendre un
    > vélo.

-   **[L'Entreprise]{.underline}.** Elle veut enregistrer correctement
    > les informations à propos du [vélo]{.underline} rendu (le Client,
    > la date, l'heure, le vélo). Elle veut satisfaire les souhaits des
    > clients.

**Préconditions:**

Le [client]{.underline} possède un [vélo]{.underline} emprunté. Il y a
au moins un [point d'ancrage]{.underline} libre à la
[station]{.underline}.

**Garanties en cas de succès (postconditions) :**

Le retour du [vélo]{.underline} est enregistré. La quantité de
[vélos]{.underline} disponibles est mise à jour.

**Scénario principal (succès):**

1.  Le [Client]{.underline} se présente avec le [vélo]{.underline}
    > devant un [point d'ancrage]{.underline} libre à une station.

2.  Le [Client]{.underline} rentre le [vélo]{.underline} dans le [point
    > d'ancrage]{.underline} libre.

3.  Le [Système]{.underline} verrouille le [point d'ancrage]{.underline}
    > et indique que le [vélo]{.underline} a été rendu.

4.  Le [Système]{.underline} enregistre le retour du vélo, calcule le
    > temps pour l'emprunt, et facture la [carte de crédit]{.underline}
    > du [Client]{.underline} si les frais s'y appliquent.

**Scénarios alternatifs**

2a. Le mécanisme de verrouillage est défectueux:

3.  Le [Système]{.underline} indique l'impossibilité de verrouiller le
    > [point d'ancrage]{.underline}.

4.  Fin du cas d'utilisation

5\. Le [client]{.underline} veut signaler que le [vélo]{.underline}
qu'il vient de rendre a un problème.

3.  Le [client]{.underline} indique que le [vélo]{.underline} qu'il a
    > rendu est a un problème.

4.  Le [Système]{.underline} registre le fait que le [vélo]{.underline}
    > est défectueux et [l'information]{.underline} est indiquée au
    > point d'ancrage.

### CU04-Demander extension de temps

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le [Client]{.underline}.** Il veut un moyen efficace d'avoir plus
    > de temps pour rendre un [vélo]{.underline}.

-   **[L'Entreprise]{.underline}.** Elle veut enregistrer correctement
    > l'extension de temps pour le [vélo]{.underline} emprunté. Elle
    > veut satisfaire les souhaits des clients.

**Préconditions:**

Le [client]{.underline} possède un [vélo]{.underline} emprunté. Il se
trouve à une [station]{.underline} n'ayant aucun [point
d'ancrage]{.underline} libre.

**Garanties en cas de succès (postconditions) :**

L'[extension de temps]{.underline} pour le [vélo]{.underline} emprunté
est enregistré.

**Scénario principal (succès):**

6.  Le [Client]{.underline} se présente à la [borne
    > transactionnelle]{.underline} d'une [station]{.underline}.

7.  Le [Client]{.underline} demande une [extension de
    > temps]{.underline}.

8.  Le [Système]{.underline} demande la [carte de crédit]{.underline} du
    > [Client]{.underline}.

9.  Le [Client]{.underline} présente sa [carte de crédit.]{.underline}

10. Le [Système]{.underline} affiche l'heure du nouveau
    > [délai]{.underline} et enregistre l'[extension de
    > temps]{.underline} pour le client.

**Scénarios alternatifs**

2-4a. En tout temps, le [Client]{.underline} annule
[l'extension]{.underline}.

2.  Fin du cas d\'utilisation.

4a. Carte de crédit invalide:

3.  Le [Système]{.underline} indique que la [carte de
    > crédit]{.underline} n'est pas valide.

4.  Retour à l'étape 3.

### CU05-Demander nouvelle clé d\'accès

**Acteur principal: Le Client**

**Parties prenantes et intérêts:**

-   **Le [Client]{.underline}.** Il veut un moyen efficace d'emprunter
    > encore un [vélo]{.underline}

-   **[L'Entreprise]{.underline}.** Elle veut empêcher que les [codes
    > d'accès]{.underline} soient réutilisés par des
    > [personnes]{.underline} non abonnées au [système]{.underline}.
    > Elle veut satisfaire les souhaits des [clients]{.underline}.

**Préconditions:**

Le [client]{.underline} est abonné, mais son [code de clé
d\'accès]{.underline} a déjà été utilisé la dernière fois qu'il a
emprunté un [vélo]{.underline}. Il se trouve à une [station]{.underline}
ayant des [vélos]{.underline} disponibles.

**Garanties en cas de succès (postconditions) :**

Le nouveau [code]{.underline} de [clé d\'accès]{.underline} pour le
[client]{.underline} a été généré et communiqué.

**Scénario principal (succès):**

6.  Le [Client]{.underline} se présente à la [borne
    > transactionnelle]{.underline} d'une [station]{.underline}.

7.  Le [Client]{.underline} demande un nouveau [code]{.underline} de
    > [clé d\'accès]{.underline}.

8.  Le [Système]{.underline} demande la [carte de crédit]{.underline} du
    > [Client]{.underline}.

9.  Le [Client]{.underline} présente sa [carte de crédit]{.underline}.

10. Le [Système]{.underline} génère un nouveau [code]{.underline} de
    > [clé d\'accès]{.underline} et l'affiche pour le client.

**Scénarios alternatifs**

2-4a. En tout temps, le [Client]{.underline} annule la demande.

2.  Fin du cas d\'utilisation.

~~4a. Client n'est pas abonné:~~

3.  ~~Le Système indique qu'il n'existe pas d'abonnement pour la carte
    > de crédit.~~

4.  ~~Retour à l'étape 3~~.

4b. Carte de crédit invalide:

3.  Le [Système]{.underline} indique que la [carte de
    > crédit]{.underline} n'est pas valide.

4.  Retour à l'étape 3.

5.5 Modèles du domaine


### CU04-MDD-Location Vélo

![](/assets/exercices.gddoc.docx/image38.png){width="6.5in" height="8.23611111111111in"}

## Diagramme de séquence système (DSS)

### CU01-DSS-Abonnement

![](/assets/exercices.gddoc.docx/image37.png){width="4.416666666666667in"
height="2.8055555555555554in"}

### CU02-DSS-Emprunter vélo

![](/assets/exercices.gddoc.docx/image13.png){width="5.5in" height="2.8055555555555554in"}

### CU03-DSS-Rendre Vélo

### ![](/assets/exercices.gddoc.docx/image65.png){width="4.75in" height="1.5833333333333333in"}

### CU04-DSS-Demander extension de temps

![](/assets/exercices.gddoc.docx/image84.png){width="3.8333333333333335in"
height="2.2083333333333335in"}

### CU05-DSS-Demander nouvelle clé

![](/assets/exercices.gddoc.docx/image71.png){width="3.25in" height="2.2083333333333335in"}

 

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

![](/assets/exercices.gddoc.docx/image53.jpg){width="6.5in" height="4.875in"}

### CU01-RDCU-saisirCarteCrédit

![](/assets/exercices.gddoc.docx/image107.jpg){width="6.5in" height="4.875in"}

### CU01-RDCU-confirmerAbonnement

![](/assets/exercices.gddoc.docx/image81.jpg){width="6.5in" height="4.875in"}

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

 