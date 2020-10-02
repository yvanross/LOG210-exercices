# Système de téléphonie IP

## Diagramme de cas d'utilisation


Le diagramme de cas d'utilisation représente une partie limitée des
fonctionnalités du système de téléphonie IP.

![](/assets/exercices.gddoc.docx/image4.png){width="3.90625in" height="3.125in"}

 

## Cas d'utilisation


### CU01-Afficher l\'historique des appels

**Acteur principal:** Client

**Parties prenantes et intérêts:**

> **Client**. Il veut pouvoir regarder l'historique des appels pour
> contrôler l'utilisation de son téléphone, pour se rappeler des
> coordonnées ou de l'heure précise d'une conversation avec quelqu'un,
> pour estimer l'utilisation de son téléphone dans le futur, etc.

**Préconditions:**

Le Client est identifié et authentifié.

**Scénario principal (succès):**

> 1\. Le Client demande l'affichage de l'historique des appels.
>
> 2\. Le Système affiche l'historique des appels concernant le Client.
> Chaque appel est enregistré avec le nom et le numéro de l'appelant, le
> numéro composé, le nom et le numéro de l'appelé, la date et heure du
> début de l'appel, la durée de l'appel à la seconde près, l'état de
> l'appel (appel pris, pas de réponse, occupé), type d'appel (entrant,
> sortant, interne) et côut (p.ex. 1.25).

### CU02-Afficher appels en cours

**Acteur principal:** Client

**Parties prenantes et intérêts:**

> ● **Client**. Il veut pouvoir regarder les appels en cours pour
> contrôler des informations à ce propos.

**Parties prenantes et intérêts:**

Le Client est identifié et authentifié.

**Scénario principal (succès):**

> 1\. Le Client demande l'affichage des appels en cours.
>
> 2\. Le Système affiche les appels en cours concernant le Client.
> Chaque appel en cours est affiché avec la date et heure du début de
> l'appel, la durée à la seconde près, la source de l'appel en format
> d'[[URI
> SIP]{.underline}](https://en.wikipedia.org/wiki/SIP_URI_scheme), la
> destination de l'appel en format d'URI SIP, l'adresse IP de la source
> et l'adresse IP de la destination.

## Classes conceptuelles à partir de la liste de catégorie


## Classes conceptuelles à partir des groupes nominaux


## Modèle du domaine


### CU01-MDD-Afficher l\'historique des appels

### CU02-MDD-Afficher appels en cours

## Diagrammes de séquence système (DSS)

### CU01-DSS-Afficher l\'historique des appels

### CU02-DSS-Afficher appels en cours

## Contrats d'opération

### CU01-Contrat-Afficher l\'historique des appels

### CU02-Contrat-Afficher appels en cours

## Réalisation des cas d'utilisation


### CU01-Contrat-Afficher l\'historique des appels

### CU02-Contrat-Afficher appels en cours

 
