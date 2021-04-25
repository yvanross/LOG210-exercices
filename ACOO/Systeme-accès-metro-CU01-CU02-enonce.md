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

