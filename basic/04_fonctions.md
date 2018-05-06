### Fonctions

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [fonctions](https://fr.wikiversity.org/wiki/Introduction_g%C3%A9n%C3%A9rale_%C3%A0_la_programmation/Fonctions) en JavaScript.

> La notion de fonction (function) est présente dans tous les langages de programmation.
>
> Une fonction permet de créer du code réutilisable et éviter ainsi la répétition.
> C'est une sorte de boite à outils, à qui l'on fourni des données (paramètres de la fonction) et qui calcul un résultat

Sur les exercices précédents, nous avons déjà utiliser des fontions fournies par le langage JavaScript :
- alert()
- prompt()
- console.log()
- Math.pow()

Mais nous pouvons écrire nos propres fonctions.

```javascript
// déclaration de la fonction
function nomDeLaFonction(argument, paramètre) {
    // code a exécuter
    
    return monResultat; // le mot clé return est très important, puisqu'il marque la fin de la fonction et renvoi le résultat
}

// appel de la fonction et enregistrement du résultat dans une variable
let result = nomDeLaFonction(a1, p0);

```

Un exemple simple, une fonction permettant de convertir des degrés Celcius en Fahrenheit

```javascript
function convertCelciusToFahrenheit(degree) {
    return 9 / 5 * degree + 32;
}

let f = convertCelciusToFahrenheit(50);

```

Autre exemple, si la fonction Math.pow n'existait pas, on aurait pu la récréer nous même :

```javascript
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

### Is Pair ?

Créez une fonction qui peut recevoir un nombre en paramètre et vérifier que celui est paire `isPair()`. 

La fonction va donc retourner un Boolean.

Si le nombre rentré est un nombre à virgule, celui-ci est arrondie à l'entier le plus proche.

Utilisez ensuite la fonction sur différents cas de tests (nombre entier, à virgule, négatif, Infinity...) et logguez les résultats.


### Factoriel

Créez une fonction qui calcule la factoriel d'un nombre.

> Factoriel : Produit des nombres entiers inférieurs ou égaux à un nombre donné.

Un exemple est toujours plus parlant, factoriel de 5, notée 5! : 

```
5! = 5 * 4 * 3 * 2 * 1 = 120
```








