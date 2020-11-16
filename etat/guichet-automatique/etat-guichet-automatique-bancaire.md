## Guichet automatique bancaire

Faire un diagramme d'états en UML qui correspond au système décrit par
les cas d'utlisation suivants (format bref):

**S'authentifier.** Le Client arrive à un guichet automatique bancaire,
car il désire effectuer une transaction sur son compte. Le Client
introduit sa carte bancaire et le système attend qu'il saisisse le NIP
de la carte. Si le NIP est valide pour la carte, alors le système est
prêt pour accepter d'autres actions. Sinon, le système enregistre la
mauvaise tentative et demande de nouveau au Client de saisir son NIP. À
tout moment que le système possède la carte du Client, ce dernier peut
annuler la session pour récupérer sa carte.

**Gérer guichet**. L'Administrateur démarre le système et le système
attend l'introduction d'une carte bancaire du Client. Quand le système
est dans cet état, l'Administrateur peut aussi l'éteindre.



![](http://www.plantuml.com/plantuml/img/ZP0n3i8m34NtdC9iW8IwTq15J2oeU-aGDHPOQbFakDofNACNmw52ZH03w__lszykWbYMeMjDjQrXjzl3GGIzEwgAa8ERniuo8vj4Nx3pgLI8l73l1c9yssRn8bdoz1IbWgL07DNAqnqUjYM7zHUSZaq2g_KIsTIGNJnwnYi5qMemZSqDcv-JFdTOxuTMqGn2pq8y5vsh_KkdZ4RYmtBTBKZUCPf2pVZ85m00){width="4.930555555555555in" height="4.361111111111111in"}






