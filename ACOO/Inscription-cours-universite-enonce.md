
# Système d'inscriptions à des cours
Une université désire un système permettant aux étudiants de gérer leurs inscriptions aux différents trimestres. Du côté administratif, l'université requiert l'admission des étudiants et l'organisation des trimestres. Le diagramme des cas d'utilisation ci-dessous (Figure 1) résume les fonctionnalités demandées par l’université.

![cu](Inscription-cours-universite/cas%20utilisation.svg)


##CU01- S'inscrire au prochain trimestre
**Acteur principal :** l’Étudiant
****Préconditions :****
- La période d'inscription est en vigueur. 
- L'étudiant est authentifié à partir d’un poste internet (avec une adresse IP).

**Garanties en cas de succès (postconditions) :**
Une inscription est enregistrée. La comptabilité et les places disponibles dans les groupes-cours sont mises à jour.  

**Scénario principal (succès) :**
1. Un étudiant désire s'inscrire à des cours lors du prochain trimestre.
1. L'étudiant démarre une inscription.
1. Le système affiche les cours offerts pour lesquels l’étudiant a réussi les cours préalables.
1. L'étudiant sélectionne un cours.
1. Le système affiche les informations à propos du cours et les groupes-cours offerts.
1. L'étudiant sélectionne un groupe-cours.
1. Le système affiche l'horaire du groupe-cours.

Les étapes 6 et 7 sont répétées tant que l'étudiant ne s'inscrit pas à un groupe-cours.

8. L'étudiant s'inscrit au groupe-cours.

Les étapes 4 à 8 sont répétées tant que l'étudiant ne confirme pas son inscription.

9. L'étudiant confirme son inscription.
10. Le système demande à l'étudiant de saisir sa clé d’authentification comme confirmation finale.
11. L'étudiant saisit sa clé d’authentification.
12. Le système enregistre l'inscription.

**Scénarios alternatifs**
8a. L'étudiant a atteint la limite du nombre de cours auxquels il peut s'inscrire dans un trimestre.
  1. Le système affiche un message avertissant l'étudiant qu'il a atteint la limite de cours.
    1. Retour à 3.

11a. L’étudiant saisit une mauvaise clé d’authentification.
  1. Le système affiche un message que l’inscription n’a pas fonctionnée
  2. Fin de cas d’utilisation [NB : cette terminaison est une simplification pour l’exercice. La bonne fonctionnalité du système donnera à l’étudiant plusieurs tentatives pour saisir sa clé, puis éventuellement désactiver le compte de l’étudiant en cas de trop d’échecs, etc.]

