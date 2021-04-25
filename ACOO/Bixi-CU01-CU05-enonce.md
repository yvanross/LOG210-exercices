# Location de vélo (inspiré de Bixi) 

Dans ce cas d'étude, nous nous inspirons du système de Bixi à Montréal.
Il s'agit d'un service de prêt de vélo en ville géré par une entreprise.
Un client doit d'abord s'abonner au système utilisant une carte de
crédit, puis il peut emprunter un vélo pour un temps limité. Le vélo
doit être rendu avant un délai, sinon le client est facturé (par la
carte de crédit qu'il a utilisée pour son abonnement) des frais de
retard.

 Chacun de ces points peut héberger un
vélo avec un mécanisme de verrouillage. On donne une clé d'accès (qui
n'est qu'un code à 4 chiffres) au client dès qu'il s'abonne. Cependant,
ce code n'est que temporaire et doit être renouvelé après chaque emprunt
de vélo.

## Diagramme de cas d'utilisation

![](/assets/exercices.gddoc.docx/image44.png)
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




