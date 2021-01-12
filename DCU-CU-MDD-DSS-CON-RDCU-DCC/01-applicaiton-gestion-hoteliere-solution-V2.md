
# CU01 - Noter une réservation
Le propriétaire d’un petit hôtel désire se doter d’une application pour gérer les réservations et les séjours de ses clients. Il ne veut pas que l’application s’occupe de la facturation. La figure 1 illustre les tâches accomplies par un commis à la réception. Vous devez analyser et concevoir une application permettant de noter les réservations, démarrer les séjours et transférer les séjours de chambre.

## Diagramme de cas d'utilisation
![DCU](https://www.plantuml.com/plantuml/svg/TL0x3i8m3DrpYYSMfafyTWGgCmlb024rRI1jAZjXGTm7pj6BaLP2AWERt_FxMDvAq1nYux3FJyhH9I1uiAtgWD8ocM1zgpfjRheYp7PTvwpH0ucIK96CO-q3ETk_c6PuA4GXeoN9yzDYcHtIaX5R0fCGtrFVQ9yFb51q15FhvZoOjU3mwr_zzHCw5yLIP87qxwkFF0OSVmFMMS6wbKl_vZ7cgnq2fhs5Wdggt3UD5MJP9Xqo0SSfADIMsZ8zxGC0 "DCU")

## CU01-Cas d'utilisation «Noter une réservation» pour une seule chambre
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
6.	Le système affiche toutes les informations entrées.
7.	Le commis valide les informations auprès du client et confirme la réservation à l'aide du nom et du numéro de téléphone du client.
8.	Le système enregistre la réservation et affiche le numéro de confirmation.
9.	Le commis communique le numéro de confirmation au client.

**Scénarios alternatifs**

A. En tout temps, le commis annule la réservation.
1.	Le système supprime la réservation.
2.	Fin du cas d'utilisation.

3a. Il n'y a pas de chambre disponible de la catégorie choisie pour la période entrée.
1.	Le système affiche un message d'avertissement.
2.	Le système affiche les disponibilités de toutes les catégories pour la période entrée.
3.	Le commis communique les disponibilités au client.
4.	Retour à 3.

#### CU01-Exemple d'une réservation simple
Jean Hernandez appelle à l'hôtel pour réserver une chambre.
Le commis entrera:
Le 2011-06-01 comme date d'arrivée
Le 2011-06-02 comme date de départ
"Luxe" comme catégorie de chambre
1 pour la quantité
Le commis terminera ensuite la réservation en entrant le nom du client et communiquera le numéro de confirmation à monsieur Hernandez.

# CU01-Interfaces usagé
![CU01-Interfaces usagé](https://www.plantuml.com/plantuml/svg/lPF9QiCm48RlynI3BzqGE6cRBj1II2yzj9IG7afeGJYJnA18GPBTGvPdwTMlKRzOnrdiEBZNWZ1eVerc_i-Z1-UbzSbKOVSjR8adxScEP4GE4oV7UGR7foSen3q6C9-3ayh379v99_XgOnt5CwbWjOB1Y-54J3IXpJD7DfK-Dle3bh1SGe3IOP5KvX10VO_2nkE9hnSw0yJcYraGWZ-FqXCEZwIrSPfdkC2W7RP34Pxp2agTLvxDs6VjGASuq9K-pyR6niJQ9-zelVb4rd3GbJeYzS7IeBUfJdRVqyZOQQ9aRAb7LMy0ZN4KG_Eb3nrsZHx5TieUK-FjWKls-6AcjulWFPKQUyQv0FfvfjZDn6XYeTK-5nUN7N5rVHC6y0UMMpQ05PW6BiM92aoD2qi_tz4EJ6jNOfzDwQ6PpLRUmccEer0qQlZzlJqS66qIU2fvv7WoTe6Dka26mInWtL_13Kji7EYJeWqrt8Vs7yZkxc2mVZEpSjxNtAhPrYP9IQd3rrFqLX5r4_DLcxC7qaD-khy0 "CU01-Interfaces usagé")


# CU01-Modèle du domaine
![CU01-Modèle du domaine](https://www.plantuml.com/plantuml/svg/RP91JiCm44NtESKecqgeHNGRHL5HYiG6WGhisBZnq1hPdc0xbH3YFiqvSZ76JL82OXN7-JF_pP-iV10kD4P3-NorNDoHx8uQGJOWoGXbCQcqy1vkAQ26F2_91hJOk3dSRz-m2b3lFxnwRx0e1caf0kx8AMJv6dtbL1qKMP0pj465hYqA-4m0B9aC7eDJTfTy3RKRzEWEugJFyoSdh1TLV2kAM2AvzRLpwe3PwJnShR7c8OQhiLL9nYZFNJQa9t1xOROkeaNy7_evz9FntEm9UhQF0y_XmP5iL63unYA4lq2sCUWeywSfWBqjbq6W6kZrx9MDfyjU3kW3sAwjq7kXMF1YQseSU74WvO1fD5H3RPIwhesfTEquWrQSv7coo340SAJCaFJBIfSfB1QGNgIZVmOrUTyT9IOZM_mQHQmzxoq3KST0eqioc8tD-37P4KUEHjZOhqzxulbBLZd4Vx3weWnkJAr9OJ9T_yJn9yXJ7DYd0Sm8UR92A_d__GO0 "CU01-Modèle du domaine")


# CU01-Diagramme de séquence système
![CU01-Diagramme de séquence système](https://www.plantuml.com/plantuml/svg/XP5DQiCm48NtFiMGLGesj5iJIe93bwKqT5MwKEIf8sf9xcWSo8sQS_XY7V_6WT3kdaPlvdiQhGChujgMaBtTFoHRemfIrYBa2A4vVzVejAXJuER7OiI6IqpXsJCIr0w1cdD0EYestaNXoxXAIJy4FfNIncHqEppQQFO4YpJprfgm01MWbz6Bu8qsbN8izpi1eSNECEYeDqBoE5PI2MSL4T8hJl3btMXShPBaskfoIPihnWsHEMBSoYrAKev1Youy6OpXtNcRZSSFk0Mc3eYK7PJT4oulGzFsiQw8uJ9yAitdfh3hgl_5rTvz6hBzOcya6UwlTo2W2SfOOdNmJhpXBwBpsGpLXPqrZ-_PrzpB9zDvXWL4QtIvVF0l "CU01-Diagramme de séquence système")

# CU01-Contrats
## demarrerReservation()
  - aucune

## reserverChambre(<u>dateArrive</u>:string, <u>dateDepart</u>:string, <u>nomCategorie</u>: String)
  - Précondition:
    - c:Commis est authentifier

  - Postcondition
    - Une instance r:Reservation a été créé
    - Une association a été créée entre r:Reservation et Chambre sur la base de correspondance avec categorie.nom == <u>nomCategorie</u>
    - Une association a été créée entre c:Commis et r:Reservation
    - r.dateArrivé est devenu <u>dateArrive</u>
    - r.dateDepart est devenu <u>dateDepart</u>

## confirmerReservation(<u>nom</u>:string, <u>telephone</u>:string)
  - Précondition:
    - r:Reservation existe

  - Postcondition
    - Une instance cl:Client a été créée
    - Une association entre r:Reservation et cl:Client a été créée
    - cl.nom est devenu <u>nom</u>
    - cl.telephone est devenu <u>telephone</u>
    - r.noConfirmation est devenu un numéro unique
    

# CU01-RDCU


## demarrerReservation() {#rdcu-demarrerReservation}
Aucune postcondition à satisfaire mais nous devons retourné la liste des catégories.
![CU01-RDCU-demarrerReservation](https://www.plantuml.com/plantuml/svg/RL2xJWCn4Epz5QjKK9m4hGLH95EcG8b2ar0OtmPM-75urv7oIU4tycFiHI8w91hRcl7ipCw2nLTfAOBRtDrtgoUtwNfClbQiAsIi1ozKik5FoeElFW7BCQAUbSAeCy-gfq23pm8pwqgMMYAsgNe6dc7zzsSCrYw9vI5umVTI2QtxVSqlWgKp9XT1YBWNWB9NnC8BCRrf00sZ1Enok3h2q8Y_sWXAQQ8qmuSEY0nDA1AZ6k_o2AVpTz9BlS-dYoLFhDHfFLa4UbqNcSSQe9ih1zjSqZNjApp2FvNTt1gpmDnhHpy0 "CU01-RDCU-demarrerReservation")


## reserverChambre(dateArrive:string, dateDepart:string, nomCategorie: String)
![CU01-RDCU-reserverChambre](https://www.plantuml.com/plantuml/svg/dLFDJiCm3BxdAQoT1jeGN2k6G1qtaD06d7O9dTT6D4bnt0aUQRp6NWodtKyxE75fMiV-_gpU1jR4jIqXVRcy6i-cwSkOC22jaT92spT25TwDgpHf2u6_IfGdcIpEg2UPDPcfj6CO9AbtJBx4ccODWcRZtG1qW7c_qsR9ewwkdRV9NB1SFieqO-x9O9BktswQoSUqFogDnvQc8xrxxhTGSae_KyfvHY2J5mpWLmARmAi9vatiY3MGO-6oWtweQXC-wbXaNxDS1oW4eGnGiobDG25Qk5YsssyhX-ZQRXfHeUKgSSMHQTw91POI7eOWkXICR-GEJh8UBjnItDqHcJNkmu6sE4LHoftYCJHeYsSAEZuRShZ_h90Oq85nAq-sIKND8tqCGJ1W0ZdoC6xZVpYo0G4gMfoTaGTpucQxsQF_wUTC_M9C2QMhfX5aljXkOcg0B1zrLUeSBs824gwr9W06XdL_dyTjjYfdv-SIzwH55MLPaUoqZZf8Ut4d6-ZeFMIaRj4jvI_u0G00 "CU01-RDCU-reserverChambre")

## confirmerReservation(nom:string, telephone:string)
![CU01-RDCU-confirmerReservation](https://www.plantuml.com/plantuml/svg/ZL5BQiCm4Dth54DMSOYXtHfI0keob6AJNJP27jkYyiX8uqAFr7FqOXsxNjYbWMu4ewVtcQTpOXDvx3tewyDZNZxhQsu3DIxs64jC6DyDkq0glJaQJ3Gz9FxmA6TqTYAgLn5mrWs667Q53iGnU1pNx1sO1DNsfVM5zWw9Pr1VjcWiVjDBfIWmWiU68JHGhQoWba2OqXGKyYV1uAybzZUYq1TJT6gFS2D6ZqCN29UxJC7i4LtRBIQW8neM3mNL9AqlXuEeUpWjo3z4xseU9MRtzJdb1cGPni6R5jNiL1OIHl-iCSS_tTb9chHparccoeMPa5ysv7scZ6Kd99GgQrmDPwHQFl8R "CU01-RDCU-confirmerReservation")


# CU01-Diagramme de classe
![CU01-DCL](https://www.plantuml.com/plantuml/svg/ZLH1Rjim4Bph5GjVOiSIq5m5GaWX5-WXJekaVG0ZRMqM4gcIL82Yw7_gT_XZNOgaH2D6qPkzNExCpenuRopNTkmxgB--kojszKFMTDmOg9MqMdKuwYSqg5-v5KgoPgv2Ys3G6AfMy2i3sBROSwqnxLzlt86U2gZh8-zVDAvRRl6zrk8LIsEra8SSN6c70r6PImsL3aeBBE5vAaspYC0teVjB5Adw-Ph53eUZad7s9liTDbhj-S2Ow_NpyWMXZh-g2XZzuPqwZEXMf9xpQJeorGguWNtjjpsWNI-pDYNCCmWm87vKn8O6acWeIRCSFhrynyR2SFnfn8yHgoXsl0kCxT0qMWnkCMXlK5f132glSU4GWno1H13rGLmeUpx5jZoHTk7gBytI9682-wAvDBnnVwe0MdlLfuOIJCGl4YSd2sCjuCNQDZMhEPO1Fc_AMlMzC7aov_bj8gxuFuswcDgLTIT8hKtApw1zl22_NkBWeO4zKPohw5XW1imPjVYKW_Tm95hIG7TpTCxcy5chTXIMV1ebWdqZt4X1LJEX6NaY6f0NNnVQIuQNNRR-rlhnlxAU1Eeopdu_0sg4wq7BCfzQk2sA2bQtgwX92OCovlodnIogv4wBGYre9V31MUQOPc5DO4K1QS8e5lHII3V7Mt2bez682H7FmtUNyA4VEaNVMPfQJuK8tys4gHED1V_wd4z0n81bLz-rwUg-_iUX1y_ewvzbcR_tUvGjlQ1_0G00 "CU01-DCL")



# CU02 - Noter une réservation avec **plusieurs** chambres
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


## CU02-Réservation d'affaires
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

## CU02-Réservation budgétaire
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


# CU02-Interfaces usagé
![CU02-Interfaces usagé](https://www.plantuml.com/plantuml/svg/vLJDZjCm4BxxAKQv046HGhOiTAMYHUM211LRbWEgkf99fcsGOrUsaqLgki_2DQz1NennkcdI9H87u8HaMV9yy_-Dvz9OhcsU2PX-2gFWhRIeLpn60xdXwxfYZ_qd40Ilm6Ex7JDSMBPZllyUPGuVT2hZTCk5xxExExQOAJA6N2BekZAe2svJ9PTip_PxvW4taF5KCkPk27IwtjXJnqyPWEyFkw4OG8dGTPLpQLDRLv0Wn1kUVT489NZZiKVe6suHaaTSwxGW5P97OHG6uHcT3gTJLrkg_4JXt2bCERbUAvqwfpVqmkPn0smnvJ96iInXyVghobsMz-7D4ag2bLobEaEzP9C96KycrAbvhmRJD8eGwbQ_ZjRB1K7HhpKuCNHL31JH6BOAevCY7FGk_uP_67Zqky2ZeS0VBPS9rma1tH2ibCvomLEDSposXWrA8KZKhNmu9CS-Gw6iFXqJHYCoKzb5wNqkk8IvCiPZrtKbAE6DaaZ0i-Wi63q_3rwy78UUq_-lc6Y7c6JzWHsYvnu-z9KDoo4Gk1hunlsnX_XWGDl4LJrJhU20ba2C424D5U38WoDt9BX6WGVgeCzSkmt-CaC_lWj74VmhxwRbWPR3ejcYstQBOiD9j_saoWiKuk4sTPbrR9cDkkr_8tQ9Cg5r_XC0 "CU02-Interfaces usagé")


# CU01+CU02-Modèle du domaine
Le modèle du domaine est cummulatif. On conserve les classe du CU01 et on ajouter les classes nécessaire pour faire le CU02.

![CU01+CU02-Modèle du domaine](https://www.plantuml.com/plantuml/svg/jLJBRjim4BppAnQ-16XjjEbH48mKSe4UKhH8srikZBYnMP1SXey0GT3_YRz3FzQb7h4SdQk396fdPtTd1xgAIOQKhO7czyVBztpxjFb6gdin22g38YkrGz4Q6IDyfOG6wePSGeSvhE7xtHzi4_Z3KzGF6RSZi949znGqGht3s0RjaoO7wW9TqgaxhWj26jfp2ZmB04UsWfyfQBSNVqUI6umO7cMVMVyAqaNPbiFsMJZY7kvri7rqbicHX9380zt3jTuxdBDKS2tX8SkX2S040NteZf7RulEjypA0aM2pITeRtVOmXM0kk25gTKzpwnWUS4dFVCr1shimwRL0rFsNmfXcy_GAr74xTlOqpLD_Y5kEA1RpSmZw4IlOyJlyvsiikKDM8mqbNtVIaBKwGdr3vhJiOMQeYnbENk0TzpvX4_6eBE6Xk6SDFmAfh1ER8Rjp7NeZP8k1AeZdNcYCPj77kYV7Z2W0PaP_88UpJ37OTNMvWiq6LkzMKwSLU8gnUr4efjvBj80O--hT2gGl4fJAOcnW8kF7RAyLRzHAL_W6VMOrps1jG1HpGyo0Ryt2QDQlBxuSP2XJmHVh3MaKOc6rvTWCZyp8dY-exeWHYjzhSOLEyH_W7m00 "CU01+CU02-Modèle du domaine")


Cette version sous entends que les Catégories sont les même pour tous les Hotels.  Si ce   n’étais pas le cas, on associe Hotel à Catégorie et on enlève l’association entre Hotel et Chambre.

Catégorie peut être traité comme une classe de description ou un catalogue selon le sens par lequel nous utilisons les classes.  
Plusieurs chambres sont décrite par une catégorie (Classe de description)
Une Catégorie (Catalogue) contient plusieurs Chambre.




# CU02-Diagramme de séquence système
![CU02-DSS](https://www.plantuml.com/plantuml/svg/VPB1QiCm38RlVWgnorf8OEmOocX9sMqm5dRgUl1IfJMBxKnM2cNiWVeSVR4fIPEs47OniYIax__jUM1DNDiIqlU7ntYPPIfy6LTfqXO27qgKaqpUjAX5pfxWBaczjIRSWGxGXUfLXfZSLDgnrBD3OBJODfnZfRfEY9_wL08Rj9e8wGq3qbwpyMuoLSup0fdjZi4NvmK9F7koTQaDIUrq7Fe_N3D43ahWvxkM_OOFqKOpBeZC7jjmYQA78yWbtdeo-1i18VkQd52idBTfNrcleIUTpUBumdhPVqKRWN655DhB3PTIfVSLhFBIe7ZYxZLKuWOZMUDEnxK26364sj58wKxRJxbCUaM9B192f0WksfBcPTosItKQXzIrfWIoDZkLfSFQMtN5kBl_w4EtKQ36HEJU5ORixRCApy36M6AryutteGSRfNf1LqCb7StFAh5HbNR3H-ZEJYEVNUmmvy8fN_SF "CU02-DSS")


# CU02-Contrat
**demarrerReservation()**
 - Précondition:
    - c:Commis est authentifier
  - 
  - Postcondition
    - Une instance r:Reservation a été créée
    - Une association a été cree entre c:Commis et r:Reservation

  **reserverChambres(<u>quantity</u>: integer, <u>dateArrive</u>:string, <u>dateDepart</u>:string, <u>nomCategorie</u>: String)**
  - Précondition:
    - c:Commis est authentifier
    - r:Reservation existe

  - Postcondition
    - Une instance lr:LigneReservation a été créé
    - Une association a été créée entre r:Reservation et lr:LigneReservation
    - <u>quantity</u> associations ont été créées entre lr:LigneReservation et Chambre sur la base de correspondance avec categorie.nom == <u>nomCategorie</u>
    - lr.dateArrivé est devenu <u>dateArrivé</u>
    - lr.dateDepart est devenu <u>dateDepart</u>

**confirmerReservation(<u>nom</u>:string, <u>telephone</u>: string)**
  - Précondition:
    - r:Reservation existe

  - Postcondition
    - r.noConfirmation est devenu un numéro unique
    - Une instance cl:Client a été créée
    - cl.nom est devenu <u>nom</u>
    - cl.telephone est devenu <u>telephone</u>
    - Une association entre r:Reservation et cl:Client a été créée

# CU02-RDCU's

## demarrerReservation()
![CU02-RDCU-demarrerReservation](https://www.plantuml.com/plantuml/svg/RP9DJiCm48NtFiMegxOY4c8PqQfIM6Q1KfKDPM6IQMhXd-2naRWHvHgv6EDGggHY4olsc-_DF7j3GVeGZOPYTtkNLG_5BclGIE_HLqZeFsHGpWfwKxQJNXgWyAcHlrxLgKuyShsgLITjW5bUE1kyqnZ7rJEG1DkfqkVNWkeALIeAztaX0xREArmFehAOghJsPs6fMeiZvbbVLa9O5n2yQey1m1sOaSEJ8lNAS_1CmClUrfV6eOkAtcFQ32u6FYOuCa4JnA2q8cJZlKtRflyslDGozAUXIVhrqdW8oMaxoWCQJWs9KfgGhVaCdgqpb_bUO0N_93zV21ZrFq2XyFs9wwA_WTeT-rE20WR-YPsMBOfjSgYMonpygl38sdcQaTinHj52J8bL8k8PkBUJgu7E4VLV3Guv36bFSnOLP6p6GISxley_muNOe6tuYVm0 "CU02-RDCU-demarrerReservation")


## reserverChambres
![CU02-RDCU-reserverChambres](https://www.plantuml.com/plantuml/svg/fLJ1Rjim3BtxAuYUqc81XXsDjcZXxkO2WxFkCk-WEeojrfPSIWxMJyf-8p-s9pjfOwVjfHTPeXx9nqVALyuhyLrJKtBtzTiykqdkviAEPSsILAgvno5oZzgqIbH3pZ_NZ5Lq4PoY7t3MXMwLyNGI9zPuiJLtalKXbDVMd91oj1WZcoA-LUrvRenjuWMYcV9BRWhbkRIYEKxskylU-pOPkmFu2kaHoVNFCKJYAOLi3AWbJdLfU0fBfxWUwFpv4NpWbi8XCjOprRpoP5TW6zClxVGzb89gi1DgUv66sawxfouOlUqyhXrLyAyTTLxNsZ7IvYQOc-s_1X-KkztqjRf9giM1vBH4OzWvC8jeVeaxcZPobfkd3bLf_nnh0_rOShE4aDSYUitxJj1Wl66mzmV6r_xGO3oDQE0ZkgnsXEZxtvR54nlIPcMbwRMA5e5IK0P1w89AzhDFXqFJO_fTL7-6WFigKutrurAtcttEDuizZOvvyFiyCYXzeHxGp97KWLcyE-_JJ8G-o4plf4RmH1YuJa8GfCPjOIiEZUujgf-qmdPjhKgEia0fpSxEe7Nl-0agnrpUb24tGeewmxGESuyXni2ImqpYzM2KQo5slWTWlX5n6JPuJM4ZsytBazgHJv5ef-VXenCWPhM0rnMR9Nu__m40 "CU02-RDCU-reserverChambres")


## confirmerReservation(nom:string, telephone: string)
![CU02-RDCU-confirmerReservation](https://www.plantuml.com/plantuml/svg/TP51ImCn48Nl-HL3BshfWk0je1IYjmgoIq_g8UxEji5aiancHV-zsTJAglMImsJU-zvBraaionWycEtbLLNVcctLHkeT1-GQ4_AR5HT9fLT7WsKR8Cc7ntooQoUXUiW6hdM39O65Df64eyTnhbw0JT2eORxPUcsyGv9oQJO_VLZ_bjTAKHG4Zxr0xA6PeQ3BWJ2bAIXKD_aEJfKufnZq59nsAn3qEEmZeOR3w48fA0Hsk_qN0bf6AvcWe9cCpMQvF0x_SJkQ_VMwUn-G1P30KHyvb4nFT3zAGK1tPYMBNqPH1LPhUAHe3aNAyifxVeRhq-M-7pGNMIDr-My-0G00 "CU02-RDCU-confirmerReservation")



# CU02-Diagramme de classe
![CU02-Diagramme de classe](https://www.plantuml.com/plantuml/svg/dLJRQjmm47ttLmpxahtOqFRH69FYBRIGfILjdq8U57lgrM9BZYG7Gkd_DD-nFzRHnPVD9YtqnPP6SpbpT3INsZ1b-hO1ABw_UPTiEQiLQrk42g5icDOOkHyKKXWb6-pLDMfK3ynmARB9cl-C03OLjamfdFiiL_P0EGEgOi_QEzeixtic33UFwITXi4OLLypWUwNu0wPVZUAYZi6QjjWHmj5KagcMYcCAtkIobrByuAezhIjac-eGPh31RYy5XUaGzYiqjjYnBhE-eSHKeHXM-GAOXbq1hiSQpNBoNwKm-b7EaFIZf8hWw451xCJm-Uw0fO5k_wZvVO_vGEiG2zaMTQbuPx53TO6MdUDJl5wJ2sjatUDwdJi4YQqUsW-01bglE7tFkOMHtEFJ41cViKkjt8H4joCzCqOX-wQOqAoqcpmWAJprpc4EQduJfMnRhjF2_To5iOFipKmDD-N-DWsxVoW1Hh1-0Sk3bk9r6PHDMZISw5nDrtF5Qu4ddJcB5Rrvtk8C3MnfFTW6EC6sAHNIwdywcN1vXY2xfYSrAiJdWimgQ19G35vSFMKK6fgBlPLS35-Kh7fkI46zEErcoEV823KcFUdXvfBfhOosZGzwvKbDBohokeTrakImM2y6y2bqKklZxmgZeHrxcYHoUW0fiCxIOWj50IHaIG9p2QPW9uomUJnLBtZGHU0CYCVXlLFuq7QDf9Swl_p5Mml50twk34f7D3jCPwAPnmrjqNmXV_3ZxlY46gWdoA8NnwUBtXL_EVIu8nezOw5ns5oYg6Xo_m40 "CU02-Diagramme de classe")


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

![CU01+CU02+CU03-MDD](https://www.plantuml.com/plantuml/svg/jLHDQzj04BtlhnXy2RWHRTgR42P5BhGGQ4cQMouRQM9lsA_ipXf2w7_fiVuT-cETbTQnJ7gj3xB5lddlpSnRNqQIWPBHqDv-k7Z7Zu_vyQdwTYj4fsMCyDKHQcXQPmajfd0Et-yViIFms-UedXAk2h2LX1iN54ApnjW5vKav2_qPMb8qxCypGcgtuH9u4G3McHfkA2Yx4RyAoJL633ivLZO_WxHHTlbbzIAiOmyFAfZnT5R99uH0peDxW1jyT2b03LSIdfASf0490lemx2ERuVSxwsK0BS4aJSfhrOsm7a6ViGtNgL7apZ8y85ofZSMvDUPhjzBS1oo-Ysmp8ZCFpRoFtJPnLVmy7xmtx-EAJteUtESGr0vhMFDl-C-V8hb6dW5Dag_pRvqnAa9pxVHniLEdqEJ57_VE-nmpaPZDHXxSDYVb77u4roT5lFXaJ-SmBZqP3Aw6UBhtLYiUTT4zfgEW09WP_TPPd5KUV2qk5b1Li5Wkc8QtM0D6gbpQOI1SSfD7v792Si4NuxNiq6HLvkHEggWe3Vjg-2t45FevySHGWtSn3dzw_1VdwmseGVeytDoJAAqToFXhbgIQisAapNpJv6UQ9x0k88fv16V0ANoCuIv6oRVs9_9wRDif5A84zcsBPHfyNxBMiCS8-QuquX9jp_yKVm40 "CU01+CU02+CU03-IU")



# CU03-DSS
![CU03-DSS](https://www.plantuml.com/plantuml/svg/ROz1JWCn34NtEONL5KWTgHAxga95wRgRm07IZ0SCYJso4wGUYNDmCT9IkYaRBxw_t__UMerQMydWNrOFmou4Pn_4SzHOmEenOvzAwMHnJwcAmcBjfHIo1KG3xxgrKg8vSkshSBIAvRmApldXCQnXn19LKPyriase_YtoGV7k1EPNOEb2wSAzyvlDCFGBuacqn4h2C3QmxwztQRg4z6iq6CbcOJfajB-KUg6V-UK_Vg_VC2_Xgk-bVMBEU9EVX2Uw571kYppszty0 "CU03-DSS")


# Contrats

## CU03-demarrerTransfert
**Opération:** demarrerTransfer(numeroChambre:string)
**Présconditions:**
**Postconditions:**
- Aucune


## Contrat CU03-transfererChambre
**Opération:** transfererChambre(noChambreActuel:string, noNouvelleChambre:string)
**Présconditions:**
**Postconditions:**
- Une instance sn:Sejour a été créée
- sn.dateArrive est devenu maintenant
- sn.dateDepart est devenu Chambre.sejour.dateDepart sur la base de correspondance avec noChambreActuel
- Une association a été créée entre sn et Chambre.sejour.reservation sur la base de correspondance avec noChambreActuel
- Une association a été créée entre sn et Chambre sur la base de correspondance avec noNouvelleChambre
- Chambre.Sejour.dateDepart et devenu maintenant sur la base de correspondance avec noChambreActuel

# RDCU's
## CU03RDCU-demarrerTransfert
![CU03-RDCU-demarrerTransfert](https://www.plantuml.com/plantuml/svg/bLFDQjj04BxhAOPSwa8K2hqjhKdPfAWGGx6SKzt3MXxRcqgpOcOLcZTgdiClrj6VJPLGo452sXbzVpEwbkWuDbK9zlx3ntHvO-_JBLQE6Nd5ZcI771FvvQbsx2gG-5IYtjaNxLT9eiVH5xvs5E72s42HGuaDBr6G7rtqWIx02UIJpYn4BBjADgaiNFs9cWevc9Q7zfV67borOPnt_Gix9UshNT5Eq0eNSH_uoTZXeU_wiaeIKWLGuYv2s85TBUyCdEN3LbsYYCg799tdOAQfpDRKgnpe1x7l1s3s-qE7d1l0txMc24ZWQHUuwb9PKt5cSz0GmgCNl_6bZyTd43qjtuND0qPWLtWj7zh8rjGb1_enEIzgGA3e5KYIGpg7pC2FqVQbu4De-6ghxryz_OJFiAOznc-guxiMHZE3Xza_kR-meiYthrlfDTL1vFX7aoiTw1IJB9qlh55vIgka0_eROE_SwEtaLtGWSdnkNUbPmzoEMJCIRNKQdBhsc6Hj4FQL94u9ZFjm6_EkOFLIgDaBTVrc_4VWYVMiSJeJtJVJ9Z34VEEb3kGt9UeILSvJH5BkSTrLu32lyo2kaRRwl_q5 "CU03-RDCU-demarrerTransfert")

## CU03-RDCU-transfererChambre
![CU03-RDCU-transfererChambre](https://www.plantuml.com/plantuml/svg/bLJDRjim3BxxAOXUrWBnC60tOmrQE1jyM8OXRazD3uh39EfaoI3bO7sZzJdoOgCSEUxSOcWDs915cjyFAL-nL-JRsa1---bpkfZbjwadPNc3X9JlLBqYJFYNjeqYLGFxHuFo95s5hv94jhskTAEiXxCiTzQJCzZI0XbfhxnszWmKGpdAB9n7qqMAKMIkcY-shP5S5d3iTf957jCkVvwFGO_HBfYFgbNAuzRHOvR7nJ7h-cPKOqntaSXbXICOt7Xm6oWp6DJ1Man0Pac799sMaBqmxNnfhOlhQp4BJIy7GkI7Q_Te3CQC6Bk8eAItknuLVpT87j22jXj7TKToQQk1Z8BM8kmrwvKssX-UW6NNV72h1_H0gj8ItWN3bxRp7UHZgpIBE8Rgo82J4j8f51dSCJwubZxIuCcazt4IOsjv_wRjFLoAcfkelLV-J_TUI1A4hwzBEd9h7FFXZnXi5CWi94KwdUUPq1IiBVfO_HrblwjUuqatIz_uy1Iao5vB5AP0l699LMAWIDMO5C6GF3WoaXzb8zNYB9NTta-vUoFEBv9N6laVUYVCWU6uCpApWmdHwPdcnbczCc7QQgMjHojAdWrQxDFGYpVErt4O5XdGfH9r_jHS5gIxQdVVdpe16O0d4F1c6CvM1cMFUOLsBJ-Blm00 "CU03-RDCU-transfererChambre")


# Exercices supplémentaires

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
