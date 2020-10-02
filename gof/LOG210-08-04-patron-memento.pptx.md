
---

<!-- .slide: id="memento" -->
# Patron "Memento" (Snapshot)

--

## Synopsis
- Capturer une image de l’état d’un objet afin de rétablir l’état plus tard si nécessaire
- L’objet qui demande la sauvegarde de l’état (ou sa restauration) n’a pas besoin de connaître les informations sur l’état
- Il doit seulement savoir que l’objet pour lequel il demande une sauvegarde implémente une certaine interface


--


## Contexte
- Une sauvegarde de l’état dans un jeu de rôle
- sauvegarde (implicite) après avoir réalisé certaines étapes du jeu
- sauvegarde demandée explicitement par le joueur



--

## Forces
- On a besoin de sauvegarder l’état d’un objet et de le restaurer plus tard
- On veut que le mécanisme de sauvegarde/restauration soit indépendant de la structure interne de l’objet
- si cette structure change, on n’aura pas besoin de changer le mécanisme de sauvegarde/restauration



--

## Solution « Memento »
- (copie non persistante)
- « interface »
- MementoIF
- Caretaker
- « static »
- Memento
- Creates
- is-a-Private-Member-Class-of
- 0..*
- declaring class
- 0..*
- 1
- 1
- member class
- Originator
- createMemento():MementoIF
- setMemento(:MementoIF)



--

## Conséquences
- La complexité de sauvegarder et restaurer l’état d’un objet est placée dans une classe membre, qui est séparée d’une certaine façon de la classe



--

## Conséquences (suite)
- Le patron Snapshot n’est pas pratique lorsqu’on veut défaire une série de commandes qui font des petites modifications à l’état d’un objet
- faire beaucoup de sauvegardes peut prendre beaucoup d’espace mémoire
- utiliser plutôt le patron Command



--

## Implémentation
- Choix entre l'utilisation de memento et serialization
- memento : plus simple, sauvegarde non-persistante
- serialization : plus complexe, permet de sauver sur disque (sauvegarde persistante)

--

## Java API usage
- Classes pouvant servir à faire le snapshot par serialization
  - ObjectOutputStream, OutputStream
  - ObjectInputStream, InputStream

--

Exemple de code
<code>
class MoveCommand extends Command {
 // État sauvegardé pour le undo.
 private Memento memento;
 private Vector2D moveDistance;
...
</code>

--

Exemple de code (suite)
<code>
...
 public void execute
()
{
  // Objet
 permettant de calculer les
  // contraintes de position de formes
  // UML et de leurs liens
  ConstraintSolver solver =
   ConstraintSolver.getInstance();
...
</code>

--
- Exemple de code  (suite)
<code>
...
// public void execute (suite)
// Fait le snapshot (memento) de l'état
memento = solver.createMemento();
// Déplace la forme UML
moveDistance = UI.getDistance();
objectToMove.move(someDistanceXY);
...
</code>

--

## Exemple de code (suite)
<code>
...
// public void execute (suite)
// Ajuste la position des liens
    solver.solve();
 } // execute()
...
</code>


--

## Exemple de code (suite)
<code>
...
 public void undo() {

ConstraintSolver solver = ConstraintSolver.getInstance();

objectToMove.move(-moveDistance);
  solver.setMemento(
memento);
  solver.solve();
 }
</code>


--

## Patrons associés
- command peut utiliser snapshot / mémento pour faire l'annulation (undo)

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF
