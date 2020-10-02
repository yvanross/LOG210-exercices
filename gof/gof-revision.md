## Révision GOF


![](/assets/exercices.gddoc.docx/image75.png){width="6.5in" height="4.069444444444445in"}

Définitions horizontales :

1-On veut accéder au contenu d'un objet agrégé sans connaître sa
structure interne (son implémentation). On veut pouvoir supporter de
multiples parcours d'objets agrégés. On veut fournir une interface
normalisée pour parcourir des objets agrégés ayant des formes
différentes.

3-On veut pouvoir défaire (« undo ») des opérations de l'application. On
veut pouvoir faire des opérations de l'application avec des paramètres.
On veut pouvoir spécifier, mettre en file d'attente, puis exécuter des
opérations de l'application. On veut définir et exécuter la combinaison
des opérations de l'application.

6-On a besoin d'accéder à des objets à distance, comme s'ils étaient
locaux.On trouve que l'instanciation de certains objets a un impact
négatif sur la performance du système. On veut limiter l'accès à
certains objets pour la sécurité. On a des besoins particuliers
concernant l'accès à certains objets, p.ex. charger en mémoire vive la
première fois un objet persistant.

8-L'application a besoin d'un service, mais ce service est déjà
implémenté. Il en existe plusieurs implémentations, ayant des interfaces
de programmation (API) différentes. On est obligé de faire beaucoup de
modifications dans l'application pour que ça fonctionne avec chaque API
différente.

10-On a une structure d'objets ayant plusieurs classes avec des
interfaces différentes. On veut effectuer des opérations sur ces objets
et les opérations dépendent des classes concrètes. On trouve que les
classes de la structure d'objets ont du code spécifique pour les
opérations et ce code n'est pas très cohésif. Les classes définissant la
structure d'objets évoluent rarement, mais il est plus fréquent
d'ajouter ou de modifier une opération effectuée sur la structure
d'objets.

11-On applique certains services sur un ensemble d'objets individuels.
Mais on aimerait également appliquer ces services sur une ou plusieurs
sortes agrégation de ces objets, comme si une agrégation était un objet
individuel.

12-On veut instancier un objet faisant partie d'une hiérarchie de
classes, mais on n'est pas toujours sûr de quelle classe il s'agit.

13-On veut pouvoir ajouter (ou enlever) des responsabilités
(comportements, fonctionnalités) aux objets d'une façon dynamique et
transparente, sans affecter d'autres objets. Le nombre de combinaisons
possibles de ces responsabilités est important. Alors, il est complexe
de faire une sous-classe pour chaque combinaison.

Définitions verticales :

2-On trouve qu'il existe un algorithme ayant des parties fixes et des
parties variantes, avec du code complexe pour traiter tous les cas
variant. On a des sous classes ayant des responsabilités communes et
dupliquées dans le code. On veut contrôler les extensions permises dans
les sous classes pour une certaine classe.

4-Une abstraction comporte deux aspects, l'un dépend de l'autre. Un
changement d'état dans un objet engendre des changements d'états dans
d'autres objets, et on ne sait pas a priori lesquels. Un objet devrait
pouvoir avertir d'autres objets des événements importants, sans un
couplage fort avec ces derniers (sans les connaître concrètement).

5- Les classes ayant des responsabilités d'affichage des informations
dans l'interface utilisateur graphique ont une tendance à évoluer
souvent dans le cycle de vie d'un logiciel. On cherche un design qui
facilite cette évolution, en minimisant les changements dans le reste du
code source. On veut aussi avoir une bonne traçabilité entre les
fonctionnalités du logiciel et le code source.

7-On trouve qu'il y a plusieurs classes similaires, mais qui varient
seulement sur le plan comportemental. On a besoin de plusieurs variantes
algorithmiques pour un même service. Un algorithme utilise des
structures de données complexes, augmentant le couplage entre le client
et ces structures. Une classe définit plusieurs comportements,mais ces
comportements dépendent d'une condition.

9-On veut faire en sorte qu'une classe n'ait qu'une seule instance et
que l\'accès à cette instance soit accessible aux clients à un endroit
bien connu.On veut permettre la spécialisation de la seule instance par
des sous classes, sans que les clients aient à modifier leur code.

 
