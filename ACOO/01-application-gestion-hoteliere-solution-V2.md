
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
![CU01-Interfaces usagé](https://www.plantuml.com/plantuml/svg/lPFDIiD04CVlynH3Bdwna5QjMgWKwiM3HOeUf2YiwRGD9BjbTrCF_NWMhtaDys9E-f4q9Lw59J3ptzdP_o-pNUkaSKaSOU_LRuX7vSYCPK0M4oidMGgdvsSen3rwi5Y0bP631JoHIl3PX2e8PpA2zHg6WoorPEPaC564mLJ6duRUOGMh5NWeBUOrHGa1L6CK9fnCNRNF1I3sjTkTQROTf0krOa48_Zn8HpWwaSQ4yop59NfDl-aB_vANL-YyidJ6DYiRMlc6ddHPEj4c9DO-EA9Dy86iuR0dLK3HEqkblqDFOstY99AXeG6LTmEepQCOwIzrxB2drJWqCNkSQsUENBB7lexRI-zjBXKEjBKUl6Hfn6wcMX4BZUQbkBfkYPlREz-3Fx2qsG2MO6guv3jAC1KkBFry1timZNsBGpQ5XtesEta7fpwF8g9npUyV7E30O5l0GyaJnvEnJspL9J8CPW6R--NSiC36YHUAQ4iD3w7z1x9E1uQR9pChvhqwKzKtaz-ev6Yd-gioNLrI8twllm00 "CU01-Interfaces usagé")



# CU01-Modèle du domaine
![CU01-Modèle du domaine](https://www.plantuml.com/plantuml/svg/RL9BJXmn4DttAKgpGOfc8jXQenPeG68J9I9XnyPq5uoHNUMKtID5KUx3dAClHddwGuEoykzLlK_vCcKhkGiUTlVd5vjltFQl7g7jeELW7M7LU9iIt7963zljZYaZOITh-FxuWas6kF-JtEyEwtg4xcp6PnQ72h_6r8YBsJ51UuQKNUwFTGr_Am3YOE1d5aVFrR-nzWuJoi6UyDljBx6KR5DETLrAMcrz9U8EQ4xxyUeQevgOhuXLvPEJSEfZ87tas748BcdxE_OBrNiR7gLeBhxURQrXiAo1g1ZmP_kIn1f-2BUTo-gg8uJyMIbr0ONDG0tAJLe6cIFmqynbfjtN0GwOCb1_R30bwnJmG94xWMGFx0HKZOTch2rGwOybhluuUV1E8vwTJI6F_W5KECOz4vevaceOxEfY1PiDhBwi9aa68gVKlxPOJNBBQm4fTfwn0HjB-8Mu6lcdPheivgdZmM2fz1i6iE3y06i4yJ-oXY83Do5wTbWjlyg2yJtRKq8u10Ig4QfBf5Q_-Xi0 "CU01-Modèle du domaine")


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
![CU01-DCL](https://www.plantuml.com/plantuml/svg/ZLH1Rjim4Bph5GjVOiSIq5m9GaWX5-WXJekaVG0ZRMqM4gcIL82Yw7_gT_XZNOgYH2D6qPEj9RapEpFalNN2kA5heVhwxgxOLGzPtGfheTBA6TtYO9xGedaLJch5wxaA3O95QwbQmgyCODjW9up1TFzwunVCM41J7KNtOd3T28VlZP6loAmpKXroyAKTzaHbBjLKEcWZaS7pM1fx4O5lqdINA4ftyp67BVP7hMBlJVPxccYr5ptdVc_eboy8LVnNbi3fGxJwCA0VaVQSJ-EIBLSWBEohCEq1tNhfjM4mzo302V6Z9ZRKa4H3HPhbyEdbEzOE-kDFAtyCM4QnurdWV8UsDhBtWq5pWyf9Ob06ZGkFECanaPX4VP0NofvFSLkUIBjm3OTcQH8nWNynGbbH-uzo0gs2wkC61ZRY5ucJeuMnDk75sZOrgpwo2JwlMQMxJjeywVFyDX5N_1zRNNHjMTLAKckJyhFe7Y_8hvSu16ZWJnJdCZesCGFkZLfyoY5uE10jPQ6zENfdS_XiT3D8HpuD2i6z4MwWeEgPq8my4fsG5ryNsak6brcsuTJwyR-odWJgCivXFWjwWEj1oxAGMhWjYX9Mjwke2ODUMtl-qs0MLVAhHQ4ND0QYzvPvfjaq9l2YW3HX50jwAPJl4oouigCsY0cHm2FiPl2XwrjDzonDxUhEKod7tqYF0Le7uVKvdu280S-klclZqNtrZyK0dj7jdsMPx_izgePUqBy0 "CU01-DCL")




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
![CU02-Interfaces usagé](https://www.plantuml.com/plantuml/svg/vLNDZjCm4BxFKuno0O8YbMnPw4f5Yye52Ieeom5LMMIIQMlas9NjT97QxhDmxMlG5sEIRDeKWZW09wJ8KhvlF7_VP7BflB2-o1MEtlVYwANsP6SY9OU54_Fz3kw73p2Adc40wpKueJoi8GnVaoxmZPKwbKkXmX1kRs4wsUySsHLPB3HXkX3v9qj96r-gmaagh6jO5oQmXUqM0XGESo4rG7bYPELyuK_ZFWJ4C1mRVnV1rdw5bqPp2iXvyl6s4DfBlzzXTaW2DnWC1W6pBuGdpEu9Q-MAJHYFUt4lwftnS-JvsU-Mt9WJW_FIO2JOzTnOMJgzvZUgNguHfYEXKrB91gVFFvkYpBAfCi4DqqRFfCt99Z0SykNXa1ivQTNWgZuomyrirz5ukM0g_hc64iPZ5Hr5L1SRW_v94INrglX2VnYu_xl0_Qx0xxpGcR0P4ySXc1cR5qf8InCwj0OwKOmoSwD_7993dt5bl3qT4-0H6PlyOXDyM0cD4-DS05VxdUA45qOJ4u_YiwZ_-3nwydJG2qhx_qg9PeWPQmzibpntTDrNwCOnKZJh-8pROuzfVO6NJLdrs3H0pMwG5M51AYcm50yFsZ5mHOfgwR2jNBCD_h92txwgKYByLzvTemClXscrP9VDagLAa-uTY_2HKwfu-kMgJQgU79Lq2tFJ_iJWadJ6VuBl "CU02-Interfaces usagé")


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
![CU01+CU02+CU03-MDD](https://www.plantuml.com/plantuml/svg/jLJBRjim4BppAnQ-170jj6blWc2aa0hqaA95qjvoOQIDpO2ly64W2FelFTRVeH_hag8Z6UsrFiWME3ipkplqbG_SXQWaj3_UNRwXn_lq-51zwJh6UiczXyyce8IcDJgWnkWsyFN-4Vi0Tl_inLF4RG6sFE3EE87GTEXx9smGHiDmWJg8C1ut2S6bsL49l300RLGDjy49lMC_2yaDUdG7dYkRxuvhp_lqidrXsf271-5KFbrKqab02CQ2UO1RV3JHGGtN79uYdwG10pYqRZnwCaFlTzfo1vA3YZ88AqMVOGE2l20RfXTPv4uJt25SYvt6fJNYQ_TStJiilejiav699ooyvsuRlor-da_UcxT-IoS33UwZS-A0DNJq6_xpfqXsI3C8a-Jh_5kZbF3Gt1WvBtRg59gq-7dljC-SYKXisjFWzYaf6_Zcp115eCL7VJw7lFIeq9aQ_FdUMober4LtJaT10H0pshtHkAWy-LfThg2gOBLU4GrjiGRqeJBnW2xWcfgSaUi9IGMVb9MyHvLKYPCwgRm8SJnMuo_6fj0lYIU66gpnVlmzuByuNsz03TocuQQUM6djH4PVYoJLb1N5TUAR9h_GF8Fr3f4j8xW0Jk4Z37MH9V-sFv7NkMqZa9MydipF7PPXq7L9KkCHFQIhqh0hr0FzK_m1 "CU01+CU02+CU03-MDD")


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
- sn.dateDepart est devenu Chambre.sejour.dateDepart sur la base de correspondance avec noChambreActuel. **<u>Pour pouvoir accéder aux séjours à partir d'une chambre il faut une association 1 chambre a plusieurs séjour.  Donc je modifie l'association pour plusieurs à plusieurs</u>**
- Une association a été créée entre sn et Chambre.sejour.reservation sur la base de correspondance avec noChambreActuel
- Une association a été créée entre sn et Chambre sur la base de correspondance avec noNouvelleChambre
  
- Chambre.Sejour.dateDepart et devenu maintenant sur la base de correspondance avec noChambreActuel. <u>Cela annule tout les séjours alors que je veux seulement en annulé un seul. Je dois donc créer un nouveau séjour avec la date de début correspondant au séjour courant, la date de fin a maintenant et associé avec la chambre précédente.  Je dois aussi détruire l'association entre séjour précédent et l'ancienne chambre. L'association plusieurs à plusieurs entre Sejour et Chambre me permet de régler le problème mais rend la solution très complexe en plus d'ajouter une table d'indexe dans le diagramme de classes logiciels</u>  

Je vais donc proposer une nouvelle version du MDD qui utilise un concept de classe d'association.

## Simplification du MDD
| | |
| - | -|
|![CU01+CU02+CU03-MDD-avant](https://www.plantuml.com/plantuml/svg/jLBDJi904BxtAIPSI9H6qLlJ40mzOZIYDovhEvGXszsoEqian7VnodFmOavBg_W0zh3fxlnyttpVJ3qhnw7IC7kx7L_BSTSSz_5ZbiLgfmn7JAmn0MzrOB86o12JqXZbMdaFB-ZHxLGRIb-TCbxbpMLoY8oTMRCYLxNH11Rio9JHPzILBd1ZWuDqJgL1A13ueXmE4K3g9ziW98ZtVNbwuoSIAHJZWtEq4sgP_CC_VnraXhNeTOQKGOmLPBOrs1NCrgfwTmW9p1LKebMjAIS-7Q7MmHC6v-7qTN5P6geaPniGWipVQY8o3CaK-D6twpHQcaAa0IrnKgLJLTKATgwHTriA5chVIzkJIP_UDyXGh_U-0Hg1EC9e0fpR3TSoW1x1ixD581RmXWd_SH70X0gTbHNuyU_IzC5u074CWwj1PsW2kO0Gokvqx9jOb_AhafSaS6sZqr5c464XZQPe2bd7Rm00 "CU01+CU02+CU03-MDD-avant")|![CU01+CU02+CU03-MDD-après](https://www.plantuml.com/plantuml/svg/jP5BJiCm48RtFiM_AuWMyTX54IfAbY0GXGEuoRHnvTZ17aT25VVX7boCIL9LPS4IByRsFFpFV5v6re5JQr6yNLrVYBaPpEtYiImNkWlVNr6nOKiPLjucDjv1zrGXEK9bTOo4UYQRhumUecfqueKYXNxq87yDsaLT3PUxlNA-y6vZGZj6vLqEnctLfv884zXty1kiQETJo53yhJ6b87ymMsccbj8J7UmLK6kc-n1CB-sNSiO_huDaIPr0dII7kQPsYqQtwq38dzOxOdJDHpJlYUOG74mkIQcBiBD6ADWvdeElas6PV43Dln02BhKKV8PuX7TsWdn-q3h7vH5a9Ig67AibkLe-_0S0 "CU01+CU02+CU03-MDD-après")
|

La solution de gauche nécessite 4 classes dans le diagramme de classe alors que je peux le faire avec seulement 3 classes si j'utilise la solution de droite.

## Nouveau contrat utilisant la classe d'association
## Contrat CU03-transfererChambre
**Opération:** transfererChambre(noChambreActuel:string, noNouvelleChambre:string)
**Présconditions:**
**Postconditions:**
- Une instance nouveauSejour:Sejour a été créée
- nouveauSejour.dateArrive est devenu maintenant
- nouveauSejour.dateDepart est devenu Chambre.sejour.dateDepart sur la base de correspondance avec noChambreActuel.
- Une association a été créée entre r:Reservation et nouveauSejour:Sejour
- Une association a été créé entre nouveauSejour et Chambre sur la base de correspondance avec noNouvelleChambre
- Chambre.Sejour.dateDepart est devenu maintenant sur la base de correspondance avec noChambreActuel.
 
 Le contra est maintenant beaucoup plus simple.
# RDCU's
## CU03-RDCU-demarrerTransfert
![CU03-RDCU-demarrerTransfert](https://www.plantuml.com/plantuml/svg/bLFDQjj04BxlKmovr8Me57eJhKdOf2XGGucIKzt3MXxRcqYpOcOLcZTgdiClrj6VJHKJo452sXbzVpEwaEWuDbK9zlxpb-JsojudQwmSC_8TEv8DSZJowAbsx2gG-5oYtjaNxLV6w77qXQyTHJXBRQ38eSI6Rr6GdrpqWSx02UIJpYn4BBjADgaiNFsLcWevf2qFRSzJktFLYd7UzI_ibBIlTaKxGIjSn6tWvzGE3ttNvPqnf0gWn4s4i84yXQDsMAj5557jO99v3kaqajcIUea3zw3quu3AVhiROV5FhH424dZQ1AwwI9PK7DaSD8JmvCMlVEdZ_WL4JyiFOVM04TWLNikxDgybTR61VapEYweNA7e5Od98vf2by6lqV2xu41h-jDRtxvv-mpTOqXRZZUhugONHpE1Xzb_ehwmeylLfAxscEeZi_sfofGCTeScI-SAcAazfbNH0VmVi3pTwE_WL7OZiNrfNUjOmjpFMZ4HRdGQdhZsQh0t2daZYaC2u3DSnxmfMBuMQdPhV6-eEb4U1qu7efgMj_I7ZAozr8BygKJUeSfuYaXAFYwxgXc4Tft21jDO_xHy0 "CU03-RDCU-demarrerTransfert")

## CU03-RDCU-transfererChambre
![CU03-RDCU-transfererChambre](https://www.plantuml.com/plantuml/svg/bLJDRjf04BxlKuno2OsWgjIRrQ0W9nM7WYAxEOKS5ZF0fkjTDBj6pHirpy6BTTPU1sFQga42uPtP-NvcnZVEI_9LgI5z-FHvbDsc3oDFqhWr4bAwbUMIKBWVokmaoHASVz78lwIAS4i8FlQgK3jfF5magJMUhCQACdH8U-cLDHSW7UIzpAdrgEl8j1UPoTqNKvL8DWauPZDC8ezndJzB-w1Dj0wc_Mfz7fcuxyOTFjkA9Ym6TPBN3mtToMaTOwizogh9w2RESy4Vmsf0uzg3NKEUmD47MB5Tw1pZWnYDSqZEx1qiZB7nVsGIXKE8p0EqrXWpOkn312MrsRQe-7E7v04DABEsLDQg5wOuaf5G6OIzScgfjFA7Lt1ygY_jyXaza2mKXxUXDGjJTmZuif7AiJW7HSF0YHn6OvWcyDZOzv6E9WyBwN5ZwMKOOoj-_ghC4ropckzHUwlyfCzdaXZXxi-I6cuxwzpX5nki9V3KYEbeF4iJfibO6_In-ZlAVfEjnZVTZllc3gz12fzLH64Ss2l7gP8DPAaAnJGOaWP7UlAZRAIIdQLcRkxvsnenE6CNglobaRFAS_KmKvVIisNBoekKHUUJ1Fm9nE2_nwFfPPO0NKk-wTzwutWi7uljKxjUF8obLCQZOGU64DfwYs574iXFsfUra5oqitt1KQ-GtGkZ52rr8Wlmy_pgYfU6a8iEgBkpmuK9I1CYjSVEMdJW_xKhF05B961gDsXM_CBw3G00 "CU03-RDCU-transfererChambre")


#CU01+CU02+CU03-DCL-Diagramme de classe

![CU01+CU02+CU03-DCL-Diagramme de classe](https://www.plantuml.com/plantuml/svg/ZLRRJjj047tFLupoWadighHlbXk1d5PKWXQHzYcWQcCFoI9xr-okaL3L_sc-8p_MlVcM0EKXYJqxFdlcx9bnJgKYGjLb0P3-V7yorLyVpDV7Q9vUH7DAreAK9KAEa1L4IXpP7qWvKu8NM8jhb2WUYQAS9Lrqzdi4CCsn949WFoSuDWl21b2a6rAk10OvKNWc17t4M2f1sJe44vfZfTcreKo7rbnGZ65XGyzXoU2X9anHzHH_PJeVHTX3NnoYBrv5ppYxew8Sri1usP9IM62ruKm_9jl7b21Ctg7eAcJSNvrbgiQYVPpnRxn-nA90lnutA7-yrEDBKYLcHq-quvasLxCn40cNALZLrwY2BlyuXZPl3xFMPV66IUQtzpGQo7EBQI7xwGRL9MfC3thEjHPWJO1CUo24xwjxp1HKcoT97sgqfbXAlEUrU2SwFPkIdaA_Paxd2sMty0b-U2LR7GSiseBQ4Y6Peym4hGmmv4TehB3RXfE9JY45NzSucSniKP4HoP-rrytlSa47fjnjcxJmm3Sz8GOGqc4SU17UYhhqGBSQ5xADbg83drDPSKPN1GOth2JK2AxtQKrrmxo2hKwjK3qRGsB59PcvcNb5KkTtcz0Nfs__Z9SbbN5gVuuFLZUDXyBCv_od0_lzHhG1LA-PbzdcjiLx6qmC8kuHUh6Bio9E2weDOZQE9AflW-g3uyxQ2-jBI2xecjbXgFQLwzdv5yrZRTCL2hFW-seOx1K2SttTn9fAV6oQ2jHNmQ2Uq9tkthXqmRs1USCEnuiZ0LPiBNH96GfNNhzWTswGNEjfFcjY3W4IqzPTLuVWEhxMPy4a54SRCmT2k18yhwdIFLYpGy6MUprlUtr0vqf_ckuFUfrkZympw_fODawDke7SngRkeHVcTZTBHcw4GHJDmCo-aPb_vcOy6JVbnr1nANT_SnmrWfZL98gw8HG3gSn1c4r7dh3DwBTV3ERro0oE4_kPZ4mWDgGcUjNoSDanV2whWkkXtc_fyScu9Unar23wU2mJ5sZOcjIs9fGAn6uh3T9k2veyp4RFlkGj_6Nwog8ZgBNhf6jVGAV8Slrluny0 "CU01+CU02+CU03-DCL-Diagramme de classe")
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
