### Fonctions

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [fonctions](https://fr.wikiversity.org/wiki/Introduction_g%C3%A9n%C3%A9rale_%C3%A0_la_programmation/Fonctions) en JavaScript.

> La notion de fonction (function) est présente dans tous les langages de programmation.
>
> Une fonction permet de créer du code réutilisable et éviter ainsi la répétition

Sur les exercices précédents, nous avons déjà utiliser des fontions :
- alert()
- prompt()
- console.log()
- Math.pow()

Mais nous pouvons écrire nos propres fonctions.

```
// déclaration de la fonction
function nomDeLaFonction(argument, paramètre) {
    // code a exécuter
    
    return monResultat;
}

// appel de la fonction et enregistrement du résultat dans une variable
let result = nomDeLaFonction(a1, p0);

```

Si la fonction Math.pow n'existait pas, on aurait pu la récréer nous même :

```
/**
* @param nombreInitial
* @param puissance étant un nombre entier positif
*/
function puissanceDe(nombreInitial, puissance) {
    for(var i = 0; i < puissance; i++) {
        nombreInitial = nombreInitial * nombreInitial;
    } 
    
    return nombreInitial;
}
```





