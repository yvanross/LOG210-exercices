# Refactorisation 

## Exercice 1


Appliquez (au moins une fois) la refactorisation nommée « Extraction de
méthode » (*Extract method* en anglais) pour améliorer la lisibilité du
code suivant.

void afficherCréance() {

Enumeration e = \_commandes.elements();

double coursDeCrédit = 0.0;

// afficher entête

> System.out.println
> (\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");
>
> System.out.println (\"\*\* À recevoir du client \*\*\");
>
> System.out.println
> (\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

// calculer montant en cours de crédit

while (e.hasMoreElements()) {

> Commande chaque = (Commande) e.nextElement();
>
> coursDeCrédit += chaque.getMontant();
>
> }
>
> // afficher details
>
> System.out.println (\"nom:\" + \_nom);
>
> System.out.println (\"montant \" + coursDeCrédit);

}

 

## Exercice \#1 Solution 


void afficherCréance() {

Enumeration e = \_commandes.elements();

double coursDeCrédit = 0.0;

afficherEntête();

// calculer montant en cours de crédit

while (e.hasMoreElements()) {

> Commande chaque = (Commande) e.nextElement();

coursDeCrédit += chaque.getMontant();

}

// afficher details

> System.out.println (\"nom:\" + \_nom); System.out.println (\"montant
> \" + coursDeCrédit);

}

void afficherEntête() {

// afficher entête

System.out.println
(\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

System.out.println (\"\*\* À recevoir du client \*\*\");

System.out.println
(\"\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\");

}

 

 

 
