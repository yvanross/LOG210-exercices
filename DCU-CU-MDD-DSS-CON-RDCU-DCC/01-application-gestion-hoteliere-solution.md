
#CU01 - Noter une réservation
Le propriétaire d’un petit hôtel désire se doter d’une application pour gérer les réservations et les séjours de ses clients. Il ne veut pas que l’application s’occupe de la facturation. La figure 1 illustre les tâches accomplies par un commis à la réception. Vous devez analyser et concevoir une application permettant de noter les réservations, démarrer les séjours et transférer les séjours de chambre.
## Diagramme de cas d'utilisation
![DCU](https://www.plantuml.com/plantuml/svg/TL0x3i8m3DrpYYSMfafyTWGgCmlb024rRI1jAZjXGTm7pj6BaLP2AWERt_FxMDvAq1nYux3FJyhH9I1uiAtgWD8ocM1zgpfjRheYp7PTvwpH0ucIK96CO-q3ETk_c6PuA4GXeoN9yzDYcHtIaX5R0fCGtrFVQ9yFb51q15FhvZoOjU3mwr_zzHCw5yLIP87qxwkFF0OSVmFMMS6wbKl_vZ7cgnq2fhs5Wdggt3UD5MJP9Xqo0SSfA9JQKbkchtq0 "DCU")

## CU01-Cas d'utilisation «Noter une réservation»
**Pré(s) condition(s) :**
•	Le commis est authentifié.
**Post condition(s) :**
•	Une réservation est inscrite dans le système.
**Acteur principal:**
•	Le commis à la réception (commis).

**Scénario principal**
1.	Un client appelle à l'hôtel pour placer une réservation.
2.	Le commis démarre une nouvelle réservation.
3.	Le commis entre:
i.	La date d'arrivée;
ii.	La date de départ;
iii.	Le nom de la catégorie de chambre;
iv.	La quantité de chambres.
6.	Le système affiche toutes les informations entrées.
7.	Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
8.	Le système enregistre la réservation et affiche le numéro de confirmation.
9.	Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**
*. En tout temps, le commis annule la réservation.
1.	Le système supprime la réservation.
2.	Fin du cas d'utilisation.

3a. Il n'y a pas assez de chambres de la catégorie choisie pour la période entrée.
1.	Le système affiche un message d'avertissement.
2.	Le système affiche les disponibilités de toutes les catégories pour la période entrée.
3.	Le commis communique les disponibilités au client.
4.	Retour à 3.

#### CU01-Réservation simple
Jean Hernandez appelle à l'hôtel pour réserver une chambre.
Le commis entrera:
Le 2011-06-01 comme date d'arrivée
Le 2011-06-02 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation en entrant le nom du client et communiquera le numéro de confirmation à monsieur Hernandez.

## Interfaces usagé
![IU1](https://www.plantuml.com/plantuml/svg/TPBDQiCm3CVlUWgHoxumf1tiCEXQo2uxh8p2Jg45asgT8R6BukIIfS-oQrvZUR7PwPekj0KZBFs5h9_aMMubso9ByULz1DUtDoZ44mPGLP3Br485hwGBV6Eb4xMLAUns4C-D9SP24tBRvCIbjChe9THGrn2Wp36JIWDuYuBLvjCEYzu1ulaYJX32cMTf2TTNabcLRODV68p3SIZ2UtU2NdUdRROEO93mu1CYQTjcOrYHqrREeyvPeTCmZgHEA5qwALxiNoV-tp_JFWPmk5tWE9rEPFI7ugoZyHsMnZBX53gikS6arxLvT0rCJsbz68-yPt1znf5tWEkad-_am3k2oUJomlomXqjRK2__WH30ZFJQVP5V "IU1")


## CU01-Modèle du domaine

![CU01](https://www.plantuml.com/plantuml/svg/RPBTIiD048Nlzoc6t1Ia1NiRGgYaWdTArGVO9aExiZznTb8GyNtiS_J5dCrFZU3LPYTdpdndaaraJTmv2zNhxLhLLiS83u7HGb5KmJDwx6W9Z_ith1dQuqSqxnsMvIYjDECXa46HRp7MP5esmKEpGC-6B-UoX4y5u8FBuPd9-8Fw6djt695EkjSNnGjf7tMTRcMPMXgnlYCo9ypxvx6qnLQ8nz9aLGNdJ1INNR0pkADsUqfe2V-NVWb3iavCV0IxEAR0ItYYq7I61Rxp23m7cXojaLpNEGapzg5IGA5Hm-goTGQh5MGtsSIGGnjYl7mtg2Qgz3Q9H7lTOWwwJV7I53KEcypac6rC5e1E--GtP9_D_2Eh2V4VhA4fXtlNsc1GpJ_6d6o4pG4Z0_MYonc44GgrGT_8h_C3 "CU01")


## Diagramme de séquence système

![DSS1](https://www.plantuml.com/plantuml/svg/TL11JiCm4Bpx5QkUYkGSk5eLj4hF294Zuc2SRR6QNKVhJQK-YNVmCPoKj22LYpKUZsTcTvtLYmxKmRPfxer6xT31Kr8K61X1lZupoj5hJ6po8NBlnHDaFNLOJebX_6msGPF0mjM9AEO5-0ndQ9wBVGonzwpblJbbHS99y8FDMGZLmymuQ96y2CeBNiANTxDmjQgglr9kIzlMAsv4uX7j2BTOcgg5KF0-IKGBhvoedgzlS2jOfa2K-iFJk-3oQkh6ONbluMf-eNxxEcWczf-w8V4k2aqZFLeWv07weXytrA5P8xTbdzy0 "DSS1")

## Contrat
[**demarrerReservation()**](#rdcu-demarrerReservation)
  - aucune

[reserverChambre](#rdcu-reserverchambre)(dateArrive:string, dateDepart:string, nomCategorie: String)
  - Précondition:
    - c:Commis est authentifier

  - Postcondition
    - Une instance r:Reservation a été créé
    - Une association a été créée entre r:Reservation et Chambre sur la base de correspondance avec categorie.nom == nomCategorie
    - Une association a été cree entre c:Commis et r:Reservation
    - Une instance cl:Client a été créée (? Nom, Prénom, Courriel)
    - Une association entre r:Reservation et cl:Client a été créée
    - r.dateArrivé est devenu dateArrivé
    - r.dateDepart est devenu dateDepart

## RDCU


### demarrerReservation() {#rdcu-demarrerReservation}
![rdcu-demarrerReservation](https://www.plantuml.com/plantuml/svg/RL3DIWCn4BxdAOQUMh0-mAAbq7D1NF1YFSJiT3iqFsjc8kmZwMlqnPoiMbRmaeJ9zyttisMnMKhma3jNrXq6cpFcHsJCxrOeHSDdYeFDDW3Bw57FJAvIp8DIoT5Wey2YsQKeENaiS_O2B4Fx5nbSixV3NKoXQNLNx6-S5UnJ9cnslw_DnDplZ8b943Br9m58Hnqry4HChsf5RO5UX-YksZ0KuhTIXvAAw3V3IJTuXYBaYL4j768TXyjdq4l5Bn-J9dzhUJnALMfdaQ3JuCXS2vaPcb1G626uspEEl5o19EXHG7kqOmNyX1iDh3SL_Qp1hp5Vu1x-ANsvCcQBiTEMlm00 "rdcu-demarrerReservation")


### reserverChambre

![rdcu-reserverChambre](https://www.plantuml.com/plantuml/svg/VPDDRjim48NtEiKWcpf1SW6XIHEe1RgmWS0kklA6eSOIKVuems7G7iczXYxMeMGvjf1w8r9ympV3RyZ7o8euEGjKwtH7697UaAfMkHV28luolbEa74J-Or6-P7GEBvvbcz6cKvxXggo2PmeM4wq71yKc-2jG4JRdaLf2dJDnqAgPPilA6lGyYijprUbofRhFFhXo8rNuvbOhnYQGmRAQPW_3rjNSMF5xo6Z-z6CMqfQ7Cu_wztEPolcvraNX0oEGQLg6i8EgX9yccXUX9CH0XgtNHonRtoKJNnE2_eIH8VciTzJl9QOssVRKBnkkBZl2PBZr71AB7A4L1niXiR4c2aZHyhBh_peP14E_7nZ4CPV5tL3wvgH_K4kNCSPS4DmzY0QpIx7O-bfWFX6PDvnw0UFYLvHA-MJnlKSmBbuNSCvD4bI44fQeW4rEMIrlRahG5kuFokBBHxk-_UwG6D23yRj0RkXDCJXaT99P31haHRuo5x9Vy95h8aRjw7Cu_jBC6FJxoVr32jV5Vyzx2pgq_Jwp1cJvIPrL3Owvrna2tHy82CdZ3Hsu7jxHC9_UpPH_rfgJaeuOYaVqjRpZVm00 "rdcu-reserverChambre")



## Diagramme de classe

![DCL-cu01](https://www.plantuml.com/plantuml/svg/VLDBRjim4Dth50DlOWSKa6m9GKqX5-WYHeEa5s2eWSr28bMI2X0KkKzz3b-imuy-GOBkoCUPDs_USEwS5zQFVGVxvhwKuyrj8JlX73H6Usiw7EqZEhGlmYkZ_nG0BVR2Mbp3sntXDjxHDYVHFrlSjiBZLslL2tBdhT971W7Quq05PqWIT3HM8OUd2EsAjwnWSn13fKtFqmDRGflfL6z0E3Wq48GTqM-Ny1s7EOmeC-Ttux63gWhTeQRc6Fnu_eNImt1wTUhtY7Kz6J1bK_WUdRHg2Br2UuNQAtyvrtKi6qfcxKb4Dk1UlNFXSfwYsCg6HMjAcfjVkKlrVrgXdP3XLjTn28kvyPoXp3f1wn794yyrcEIDwNlbcEnuqobgXwtudZuEwyDeKZu9UwGViZYM-0aEdYwMCaXsZyIf7NHNfp051W_MjAFovEYe4VownuangflhHByJjlqIr1Hfdd1TbZLihZUJ10w3SUxojyLY4XLUoz8iO-KWXj1TO2jo8QZAyfrjF7vt7NXIovz4I8ku4f9qf6WEt_gXC_G3r_DCKaZmxIoO8j7vl4ENCv0mg8fFTp2c7fh_FARY1Qt5RCky2NUeMzhsVm00 "DCL-cu01")


### CU01-Exercices-Notez une réservation
1. Représentez le fait qu’un Client est responsable d’une Réservation.
1. Représentez le fait qu’une Réservation peut avoir plusieurs Ligne de Réservation.
1. Représentez le fait qu’une Catégorie de chambre regroupe plusieurs Chambres.
1. Est-il nécessaire d’associer un Client à une Chambre? Justifiez la réponse.
1. Représentez le fait qu’un Client désire occuper une Chambre d’une catégorie précise 1. durant la première fin de semaine de mois de juillet. Justifiez les associations à 1. l’aide d’un verbe exprimant la raison d’être de l’association. Indiquez les 1. attributs des classes conceptuelles.
2. Représentez le fait qu’un Commis a confirmé la Réservation à l’aide des 1. informations personnelles (nom et numéro de téléphone) du Client. Justifiez les 1. associations à l’aide d’un verbe d’action. Indiquez les attributs nécessaires.
3. Bâtissez le modèle du domaine partiel du système de l’hôtel. Justifiez les 1. associations à l’aide d’un verbe. Indiquez tous les attributs pertinents


### CU01-CU02-Exercices-RDCU

1. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une réservation. Annotez votre solution des principes GRASP.
 
2. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’instancier une ligne de réservation. Annotez votre solution des principes GRASP.
 
3. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’associer une ligne de réservation à une catégorie de chambre. Annotez votre solution des principes GRASP.
 
4. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de stocker une réservation. Annotez votre solution des principes GRASP.
 
5. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de repérer une réservation à partir de son numéro de confirmation. Annotez votre solution des principes GRASP.
 
 1. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de créer un client tout en l’associant à une nouvelle réservation. Annotez votre solution des principes GRASP.
 
6. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant de détruire une réservation appartenant à un client. Annotez votre solution des principes GRASP.
 
7. 	Proposez une solution logicielle, sous forme de diagramme dynamique, permettant d’imprimer une facture incluant l’information sur une réservation, ses lignes de réservation et les catégories de chambres associées.  Annotez votre solution des principes GRASP.



# CU02 - Noter une réservation avec plusieurs chambres
**Pré(s) condition(s) :**
- Le commis est authentifié.
  
**Post condition(s) :**
- Une réservation est inscrite

**Acteur principal:**
- Le commis à la réception (commis).

**Scénario principal**
1. Un client appelle à l'hôtel pour placer une réservation.
1. Le commis démarre une nouvelle réservation.
1. Le commis entre:
   1. La date d'arrivée;
   2. La date de départ;
   3. Le nom de la catégorie de chambre;
   4. La quantité de chambres.
1. Le système inscrit les informations à la réservation.

Les étapes 3 et 4 sont répétées tant que le client n'indique pas qu'il a terminé.

5. Le commis termine la réservation.
1. Le système affiche toutes les informations entrées.
1. Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
1. Le système enregistre la réservation et affiche le numéro de confirmation.
1. Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**
*. En tout temps, le commis annule la réservation.
  1. Le système supprime la réservation.
  2. Fin du cas d'utilisation.

3a. Il n'y a pas assez de chambres de la catégorie choisie pour la période entrée.
  1. Le système affiche un message d'avertissement.
  1. Le système affiche les disponibilités de toutes les catégories pour la période entrée.
  1. Le commis communique les disponibilités au client.
  1. Retour à 3.




#### CU02-Réservation d'affaires
Jean Hernandez appelle à l'hôtel pour réserver deux chambres identiques, mais pour des périodes légèrement différentes. Son collègue, Patrice Retardataire, arrivera une journée après Jean.
Le commis entrera d'abord:
2011-08-02 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-08-03 comme date d'arrivée
2011-08-07 comme date de départ
"Standard" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.

#### CU03-Réservation budgétaire
Jean Hernandez planifie des vacances avec son fils. Il appelle à l'hôtel pour réserver deux chambres de catégorie différente pour la même période.
Le commis entrera d'abord:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Puis, il entrera:
2011-07-10 comme date d'arrivée
2011-07-18 comme date de départ
"Standard" comme catégorie de cham¬
Le commis terminera ensuite la réservation et communiquera le numéro de confirmation à monsieur Hernandez.


## Interfaces usagé
![IU-CU02](https://www.plantuml.com/plantuml/svg/nLFRIiD047sVhnZoegu4OYf2XKWblWXQjDYdqiBQhEr2iYcJJH5w-Pz-Ht_CsLIRLDjdOLcOERDdpfbCEeMLPCiiHNpi-t4_2E5SNA3ltw47YmKKChMm026UbIdnXRGPwvbCXO3r6WRTt2h2qYYaxQPGD9TMvsO8ArYjm4DPO2Qr0N0t-gGdKtj8V0c8GXoduHx8GlXwBQMnscutc2WSJsNsJWgNwBNR7gCFqYfCpYIHddC9vyCW3FoWnQV6-MmtC_PwK73Z2cB9r9ESj2CTSQIgO8GmwEtqA1hY4WPlYZ9jM6egVncE8duQHJodNYDVL6DYX6VLTF5jeRXbAFphmAMnzd34GlLmx-70WeEUoa_rVuqHwy_FlVR306X69zRXwABz6EdcECxDXwQiud0Txw_2rlL-_2SNigd9BMElLXBl61L0Hvc4_uGl "IU-CU02")
## Modèle du domaine
![MDD CU01 + CU02](https://www.plantuml.com/plantuml/svg/jLFBJiCm4BpxArQvL88YACSeYeeI90uWK84FS9CbDOhjr7OgLHN_Gx-ZFyOwZpPjpkJY93kUsTcnvzPnusfPmakQGl9vDuDhlzophEJMmfDsM48K9LevL5YRARmklp5pKAssLgnhZECEcd27XJO22PwYpOoedD0AyWag9znXF_KGNkh2Ru8T0r1QXl3kZ505--be5cZHR7YpDOe-35UMP_uhZdTCQMhaInZPr4TxdqMXy9oW-GKvWXioDUgHZTSrzxrjUwReriPKoSdAWp5YWo6az0x__7IIALOKHYjvz9HeAOKb9mjT3eQzud9f_AXz7ASqQCPDKZKHAWlbPEK3dCARqNaj78LHgujPz8obe9nEEgoDFfW5S7C3mLNGQuPGQMiFlpcolWjVzI327az12BpoTZmhwyXxCbe6AOKKZ-JAyxLU1vfdiCmWic6y0-1bz8IcGJJYOoEjJ0YFiYgrG3OwDsFNX4Rhm3IWmnx86aHiZYgdo_C7 "MDD CU01 + CU02")


Cette version sous entends que les Catégories sont les même pour tous les Hotels.  Si ce   n’étais pas le cas, on associe Hotel à Catégorie et on enlève l’association entre Hotel et Chambre.

Catégorie peut être traité comme une classe de description ou un catalogue selon le sens par lequel nous utilisons les classes.  
Plusieurs chambres sont décrite par une catégorie (Classe de description)
Une Catégorie (Catalogue) contient plusieurs Chambre.




## Diagramme de séquence système
![DSS - CU02](https://www.plantuml.com/plantuml/svg/TP9DJiCm48NtFiMe6refaH3Bg22gLEn0Y8XLoSAaqtP4RATZfrA5E53FqOinIVgBmiQQZ9rvttlsem-QGsrAc6OPn92-tzwfGA7415vSG8Qgh3rXpHvul_F86nt8MQ_y5zbAipRWmxP4MPcAPfAQ5C4n39BK6KD-0Df3LwfNqQA2Acs3x6TR7z1WU-1Gg-uWn0_7JW9pD9eP-GrFwiEHiW87JCjL0BSup4_WoR6fIqsCLxGVjXaY2oVmlQv5di8sckk04sRQO5jEKUo420gfbuu9Vo9W3AvcAnGpwqnwtCbpE9AEnt5yPZthNz16i28laT2wliRoS0-pN9NELJ0hIaA9nTveg2GGYTwGtUzo1T0J2hVZaTELDf_oCJowIe2iK297SFQND9TZbrshytbgNVfA86kx8n4zoLuxNFGd_Bz7fT3ELP-7pkBVY-sNVKPRGoLipUifiS5EdLqGc_O_zIWYylP-0G00 "DSS - CU02")

## Contrat
**demarrerReservation()**
 - Précondition:
    - c:Commis est authentifier
  - 
  - Postcondition
    - Une instance r:Reservation a été créée
    - Une association a été cree entre c:Commis et r:Reservation
    - Une instance cl:Client a été créée (? Nom, Prénom, Courriel)
    - Une association entre r:Reservation et cl:Client a été créée

  **reserverChambres(quantity: integer, dateArrive:string, dateDepart:string, nomCategorie: String)**
  - Précondition:
    - c:Commis est authentifier
    - r:Reservation existe

  - Postcondition
    - Une instance lr:LigneReservation a été créé
    - Une association a été créée entre r:Reservation et lr:LigneReservation
    - <u>quantity</u> associations ont été créées entre lr:LigneReservation et Chambre sur la base de correspondance avec categorie.nom == <u>nomCategorie</u>
    - lr.dateArrivé est devenu <u>dateArrivé</u>
    - lr.dateDepart est devenu <u>dateDepart</u>

**terminerReservation()**
  - Précondition:
    - r:Reservation existe

  - Postcondition
    - r.noConfirmation est devenu un numéro unique

## RDCU

### demarrerReservation()

![RDCU-CU02-demarrerReservation](https://www.plantuml.com/plantuml/svg/RLBBJkim4DtxAqQiMjGYnD82Bb9O1WcbWWsNXN67rCAFuB6H-aUKtyYFtN7QSfl2nh5yPiwSd3Ctb5HCsLbeRgk7UVLmVZ5VebCnOcoGC7weP88Nz6Pyfw9oG6bjaSzeTEaJzznljEcKJt0Yg-1J31RpOVS9A8B5k3BAuu9cNA2Popb30rOTOLPMrg1FMx0UeqxBEzLT-k3aWcNwTgPLmZP4WxBQtww7rhiZOckZh0sbIpvRZmSIj_LrtGZXGqA8fbqbWF3A718U3PaNjeKj0lxyzVhR1-YoeVTS7bF8YM625JDOWfoCDSI_mLXvTlsNum-hxJU3IDhEilYQogJ5WRsmv12Gg8Hp86YeWam8Jf-zuPecKqW1Map0cQfrATYviHOmloxLJ-pKjo_FS0M_BC1a-dDA5P6xSXImA4nLVNegGLics2AJFrC1ltJrcw5j1Zgi-atv0s1vEkJEgXR5GDOKhdYr8og6xjPXLkxx-8z5DVz5pM2qOT05elvpYOF_GyhZV4K3SvxB0PV9l0VxsLDnWtx9c_uF "RDCU-CU02-demarrerReservation")

### reserverChambres

![RDCU-CU02-reserverChambres](https://www.plantuml.com/plantuml/svg/hLJ1Rjim3BtxAuYUag81XXsDjcZXxkO2WxFkikoWEeojrfPSIWxMJyf-8p-s9oTkRRVhPRjO4lL8FZvIld9UYM_hYhARv6wHt7twl11sB5kMf5JrFGwHUzIcKQ9gSlwvOdn5vy4f-WfddUj66KydSMAD5rjnAraNGdbjpGafHyiniixZMzMS6rl7IyGonLckF1TMDCT9lxliF6-JiIk0hv0EaLn_6qCadgRFne1AubGNXgUmT8hhWCwVlu4VkALmY8prJAABqXFP3VZ6z5qxVG-Te1bXMPdyHHXgMksUsc3qjlMuTbGYGkMezRhIZf5uPOAvtl-kiQ3W_QwhrXroLRpn8TDoe3UjqHLs3jGYMbpYZgPTdAtCKukoj7-EjO60B2kpXfBN8dhBVIFeOBnXaFS3usk3w62SHpGelUD3NturB9xOa3ORAtMdLRGCZ88kY44NLB2V_Miqz3oc7tdvyn2lhp7L-7vSw7xNftotr7dqXWR_dKO6cI_K0nevqZaGYu_dFij4vK5Y6cNkkviYTY8CM2jdXBouost9eSKugsx0SjisbIeuoWARD3iz3OJopkr_yGX4tfLWPOGKjOPf6-OTmuj19OTXnBl125T2x7m7m5mZv3fiy8x2HlQxbyTqP1yI7RKSFZS1OePWyoYwOhF6N-SF "RDCU-CU02-reserverChambres")

### terminerReservation

![RDCU-CU02-terminerReservation](https://www.plantuml.com/plantuml/svg/ZP0nQyD038Nt-nKFBqq7G-XeI36u7GF5nbkMIoAtehREwEII_FkSJOQaPCYYvUbxxqbbDAys3JtgZwhDgtRzbXlfm49QKoJzyyP1NFnb6Rtw0T7EFQMfV9WvzvLuFl3enP0LLH3JqDDqIsVm4StzfXR_5shd91YXfyuGEZGtPZYcI8fnheByFMcGaEIETLWSiC63sgjNXyLJ-VldQehFqqXg805B5wxyJhQJULkYNhobw_QJkMREgf_ESYN9CVta0W00 "RDCU-CU02-terminerReservation")


## Diagramme de classe

![DCL-CU02](https://www.plantuml.com/plantuml/svg/dLHDZzCm4BtdLunwsMwKIC3HgiAY50caLg05JgizU9CXTPNOMTjPQONuF_Htz8ynjlFLTW69Is9Fni_llPdCZR5SswwfOPrlqlpRgpTHKNDZ85VIQbLZfs_He7xYLYZv8m8eiU5QupoylAQuzdlK-Out3xHPFdPSMc6VsKTfiKATbDpYEwt54x8lLWjP9U12Qso9mXWgA5GfBP1123bmYxeHylpIdptNnPQtAwcQ0ME2o8TLjW1kO9k3ar2XNKxfrmp6D8BiCJyeYpMiLiu7b6H30fyUzbXOQ7VFHZnsc6M3LSDfIb-ZARHe7K4ehz0PS3maSKmvl5PLXt6SPPw48z0h39G6upQ2dfVkmMZVyJ0SJ2xy8p5tFT3zwC_CDQBuLNDfUE5sMHQOaCZlGZS-OqPgxdQXcaOObliNLQaM98wSyszN8hvNdPsL_wxOtRD-zu_ImyWzB62vDqh-iUuZmx5O6r59F5NfGzIiOC_bmemCh6aTmGcPFbHefCN_o9Xu1RU8pItzILE_13GAkuwQ6Yg1q6mTWKe3zTNEzM02dxKgEs6fdpfvfcT0z5KOx_7z5MBBjvvEw6Q8qpI3HRmOA31ebJ77NoL60odtDKtLrDGCUElaERIelmXMQNhI7ioF1UbmWkGNCiXGd149F48sW_TDMolw_-P5NBnsL0BXymeJ77dbELqKVtvkaCK0ZUrdrF4090XMqOippX_Tvd_v64X7D4p6MyRvSOEof6dw6m00 "DCL-CU02")

# CU03-Transférer un séjour de chambre
**Précondition(s) :**
- Le commis est authentifié.

**Postcondition(s) :**
- Le séjour se poursuit dans une autre chambre.

**Acteur principal :** Le commis à la réception

**Scénario principal**
1. Un client désire occuper une chambre différente pour le reste de son séjour.
1. Le commis entre le numéro de chambre dans laquelle le client séjourne.
1. Le système affiche le séjour ainsi que toutes les chambres disponibles de la même catégorie.
1. Le commis informe le client des chambres disponibles puis sélectionne celle que le client préfère.
1. Le système modifie la ligne courante du séjour et inscrit une nouvelle ligne au séjour pour la nouvelle chambre.
1. Le commis remet la clé de la chambre au client et lui indique l'emplacement de la chambre dans l'hôtel.

**Scénarios alternatifs**
3a. Il ne reste plus de chambres disponibles dans la catégorie réservée.
Le système affiche les chambres disponibles pour toutes les catégories.
Retour à 4


## MDD CU01 + CU02 + CU03
LigneRéservation correspond à Sejour. Il faut aussi modifier les multiplicité entre Séjour et Chambre pour 1 – 1. 

![MDD-CU01+CU02+CU03](https://www.plantuml.com/plantuml/svg/TPBFRi8m3CRlUGghHwPAOxlbn4GdSTbbQ0-GjOPcv0zANAG9xLrsvJdwOdCWBKLY5olvyhC_s-qYaWhKMGDlLLKkFnxd3noUKdWMSQVTNWLb8TAtGOv1rmaMhMuGB5BhcoXgesA4fRTMHnXkHgCZE0e0vwqWDBXllKFnau6LP-ruv-4T8uQ38kqTfzVURNImvwjSKzXgDv9h_F9TOAXHX2yXw0DAgFYymYxWMQsG-wUfEYGlMsK_0tAsyrVHzAVXo1bR7_I5i1BONBijetdGObv0MK8nAsvQbl2wsI1l2KNUmRzWXLQv1iLKdS1vFCcRTPGgYQnCc64AcKkpQLRIQuAOlOuY8NAjikbFTT24iUJjYFENk2bw6P0diNlZDTuXHjknjz5tGl4s6S58fUyE60XdoUzEXyb8rMZJkdAFKLFNdyh-LopGDVpF_G40 "MDD-CU01+CU02+CU03")


## DSS CU03-Transférer un séjour de chambre

![DSS-CU03-demarrerTransferChanbre](https://www.plantuml.com/plantuml/svg/TKyzJaCn3Dvp2giJI8s4n5PLg2ZCB843f7b-O8YT9pj1wf4u1nSZBOK5M3ny_zvPIzew5xYBqOV7gsi_8ITLr0TDOZDgU4woLtJsIh8aJGpM3WN7LSf7gxlDhIgiDg4oawqW6GGtf8qoBKdQeEB16lA9Yiu5VnCty4_HnJ5Oda3g07W0bovijzuF1ybSbLEZAZ1ri8_tbzfr3VbBQ32HBLLeNz2-Mzev_PJFV-MF-HtB6dxm-zhVi1JyrP-hp7GUuDmEPHhlVm80 "DSS-CU03-demarrerTransferChanbre")

### Contrat CU03-demarrerTransfert
**Opération:** demarrerTransfer(numeroChambre)
**Présconditions:**
**Postconditions:**
- Aucune


### Contrat CU03-transférerChambre
**Opération:** transférerChambre(noChambreActuel, noNouvelleChambre)
**Présconditions:**
**Postconditions:**
- Une instance sn:Sejour a été créée
- sn.dateArrive est devenu maintenant
- sn.dateDepart est devenu Chambre.sejour.dateDepart sur la base de correspondance avec noChambreActuel
- Une association a été créée entre sn et Chambre.sejour.réservation sur la base de correspondance avec noChambreActuel
- Une association a été créée entre sn et Chambre sur la base de correspondance avec noNouvelleChambre
- Chambre.Sejour.dateDepart et devenu maintenant sur la base de correspondance avec noChambreActuel


### RDCU CU03-demarrerTransfertChambre


### RDCU CU03-transférerChambre
