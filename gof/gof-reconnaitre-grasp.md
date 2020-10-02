
## **Reconnaître les GRASP dans les GoF**

Pour les questions suivantes, **suivre le modèle en annexe**.

1.  Soit le diagramme du patron GoF suivant ([[reproduit de
    > Horstmann]{.underline}](about:blank)), identifier les GRASP
    > (Polymorphisme, Fabrication pure, Indirection, Protection des
    > variations) dans ce patron et faire une mise en correspondance
    > détaillée.

> ![](/assets/exercices.gddoc.docx/image94.jpg){width="3.7708333333333335in"
> height="3.3541666666666665in"}

2.  Soit le diagramme du patron GoF suivant ([[reproduit de
    > Horstmann]{.underline}](https://cours.etsmtl.ca/log120/horstmann/htm/Ch5/slide037.html)),
    > identifier les GRASP (Polymorphisme, Fabrication pure,
    > Indirection, Protection des variations) dans ce patron et faire
    > une mise en correspondance détaillée.

> ![](/assets/exercices.gddoc.docx/image9.jpg){width="4.15625in" height="2.65625in"}

Annexe : Modèle (solutionnée)
-

Soit le diagramme du patron GoF suivant ([[reproduit de
Horstmann]{.underline}](https://cours.etsmtl.ca/log120/horstmann/htm/Ch10/slide004.html)),
identifier les GRASP (Polymorphisme, Fabrication pure, Indirection,
Protection des variations) dans ce patron et faire une mise en
correspondance détaillée :

![](/assets/exercices.gddoc.docx/image104.jpg){width="6.447916666666667in"
height="3.8020833333333335in"}

### Identification des GRASP dans Adapter (GoF)

**Polymorphisme** - définition selon Larman: "Lorsqu\'un comportement
varie selon le type (classe), affectez la [responsabilité de ce
comportement]{.underline} - avec des [opérations
polymorphes]{.underline} - [aux types pour lesquels le comportement
varie]{.underline}."

**Mise en correspondance détaillée :** Le "comportement qui varie" est
la manière d'adapter la "targetMethod()" à la "adapteeMethod()". Alors,
cette "responsabilité" est affectée au type interface "Target" dans
l'opération polymorphe "targetMethod()".

**Fabrication pure** - définition selon Larman: "Affectez un [ensemble
très cohésif de responsabilités]{.underline} à [une classe «
comportementale » artificielle]{.underline} qui ne représente pas un
concept du domaine - une entité fabriquée pour [augmenter la
cohésion]{.underline}, [diminuer le couplage]{.underline} et [faciliter
la réutilisation]{.underline}."

**Mise en correspondance détaillée:** La Fabrication pure est la classe
"comportementale et artificielle" est la hiérarchie Target et ses sous
classes Adapter. Ces classes ont des "responsabilités cohésives" qui
sont la manière d'adapter les méthodes de Target aux méthodes des
Adaptees. La cohésion est augmentée, car le Client n'a pas la
responsabilité de s'adapter aux Adaptees (c'est le travail des
Adapters). Le couplage est diminué, car le Client n'est pas couplé
directement aux Adaptees. La réutilisation des Adaptees est facilitée,
car le Client ne doit pas être modifié si l'on veut réutiliser une autre
Adaptee - il suffit de créer un Adapter pour cette dernière.

**Indirection** - définition selon Larman: "Pour [éviter le couplage
direct]{.underline}, affectez [la responsabilité]{.underline} à un objet
qui sert d\'[intermédiaire avec les autres composants ou
services]{.underline}."

**Mise en correspondance détaillée:** Le "couplage directe" qui est
évité c'est le couplage entre Client et Adaptee. Le patron cherche à
découplé le Client des classes Adaptee, car chaque Adaptee a une API
différente pour le même genre de "service". Alors, la responsabilité de
s'adapter aux services différents est affecté à la hiérarchie de
"classes intermédiaires" Target et Adapters.

**Protection des variations** - définition selon Larman: "Comment
affecter les responsabilités aux objets, sous-systèmes et systèmes de
sorte que [les variations ou l\'instabilité de ces éléments]{.underline}
n\'aient pas d\'[impact négatif sur les autres]{.underline} ?

Identifiez les points de variation ou d\'instabilité prévisibles et
[affectez les responsabilités]{.underline} afin de [créer une «
interface » stable]{.underline} autour d\'eux."

**Mise en correspondance détaillée:** Les "variations ou l'instabilité"
sont les classes Adaptees qui ne sont pas sous le contrôle des
développeurs du projet, puisque ce sont des classes qui offrent un
service que l'on veut réutiliser. Quant à "l'impact négatif sur les
autres," il s'agit des modifications que les développeurs auraient à
faire sur la classe Client, chaque fois que l'on décide de réutiliser un
Adaptee. Quant aux "responsabilités affectées", c'est les
fonctionnalités communes de tous les Adaptees. Pour ce qui est de
"l'interface stable", il s'agit du type interface Target qui isole
(protège) la classe Client des modifications (changement de Adaptee).
