## Diagramme d'état d'un vidéoprojecteur


Référence : UML2 par la pratique, 6^e^ Édition, Pascal Roques.

Modélisez le comportement du vidéoprojecteur lors d'une session de formation.

Commencez par identiﬁer les états et transitions « nominaux ». Ajoutez les périodes de préchauffage et de refroidissement de la lampe. Représentez ensuite le fait qu'il faut appuyer successivement deux fois en moins de
5 s sur le bouton power pour interrompre la vidéo projection. Envisagez enﬁn la panne de la lampe...

Commençons par identiﬁer le scénario nominal d'utilisation du vidéo projecteur : le brancher, puis l'allumer (bouton power), puis connecter l'ordinateur. Ensuite, l'éteindre, puis le débrancher. Ensuite nous ajoutons la possibilité de l'éteindre alors qu'il est allumé ou
connecté, puis celle de le débrancher intempestivement.


Ajoutons le comportement suivant : si l'on éteint le vidéoprojecteur sans le déconnecter de sa source, il repassera directement dans l'état *Connecté* quand on le rallumera. Les deux états *Allumé* et *Connecté* intègrent chacun une activité durable : respectivement la projection
d'un écran bleu ou de la source d'entrée.


Ajoutons maintenant les activités continues de préchauffage et de refroidissement de la lampe. Il est donc nécessaire d'introduire deux états supplémentaires autour de l'état *Éteint*.

Comment sortir de ces états supplémentaires : soit en utilisant un événement de changement (when) testant la température de la lampe, soit plus simplement une transition automatique. Nous utiliserons cette dernière
solution, plus simple et n'obligeant pas à spéciﬁer les températures visées.

Vériﬁons que nous avons pris en compte tous les scénarios : d'abord le comportement nominal en début de session de formation : 
 - *Débranché* brancher
 - *Éteint*  power
 - *Préchauffage*  [source absente]  
 - *Allumé* connecter
 - source  *Connecté*.

Puis, à la pause, le formateur éteint le projecteur :
  - *Connecté*  power  
  - *Refroidissement*  
  - *Éteint*. 

Ensuite, de retour dans la salle,

il rallume le projecteur et n'a pas besoin de reconnecter la source :
  - *Éteint* 
  - power  *Préchauffage*  
  - [source présente]  *Connecté*.


Pour éviter de perdre trop de temps lors d'un appui intempestif sur power dans l'état *Connecté*, les vidéoprojecteurs modernes demandent une conﬁrmation sous la forme d'un deuxième appui sur power en moins de 5 s.

On ajoute un événement temporel after (délai) qui va nous servir ici, à associé un nouvel état transitoire d'attente de conﬁrmation.

En fait, la conﬁrmation pour éteindre le video projecteur est également obligatoire depuis l'état *Prêt*. On peut donc introduire un super-état englobant *Prêt* et *Connecté*, mais il faut alors utiliser un
pseudo-état *History* (H) pour savoir dans quel sous-état revenir quand la temporisation tombe.

