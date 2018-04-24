### Boucles

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [boucles](https://fr.wikipedia.org/wiki/Boucle_for) en JavaScript.

> La notion de boucle est présente dans tous les langages de programmation.

> Boucle for et boucle while
> 
> Elle permette de répéter une même action n fois


#### Avant la première boucle

Pour bien comprendre l'intérêt des boucles, on va commencer par ne pas les utiliser.

Créer un nouveau fichier et un script qui va additionner 10 fois +2 à une variable.

C'est bon ? 100 fois maintenant, non je déconne. C'est chiant hein ?


### Première boucle while

Les boucles sont là pour ça.

Dans un premier temps, nous allons utiliser une boucle while

```
let monNombre = 0;

let i = 0;

while (i < 100) {
    monNombre += 2;
    i++;
    
    console.log(i + ' : ' + monNombre);
}
```

Vous comprenez mieux l'intérêt ? Pas besoin d'écrire 100 fois la même ligne de code.
On automatise ça en seulement 6 lignes.

Imaginez si vous aviez des traitements à faire sur les 36 000 communes françaises.


### Première boucle for

Nous allons maintenant travailler avec des tableaux.

Copiez le code suivant :

```
let alphabet = 'abcdefghijklmnopqrstuvwxyz';

console.log('alphabet : ', alphabet);

alphabet = alphabet.split('');

console.log('alphabet : ', alphabet);
console.log('alphabet index 0 : ', alphabet[0]);
console.log('alphabet index 1 : ', alphabet[1]);
console.log('alphabet index 2 : ', alphabet[2]);
//....
```

Au départ, on a donc une chaine de caractère avec toutes les lettres de l'alphabet.

Et dans un second temps, on un tableau avec la liste des lettres.

Votre travail maintenant, c'est de fouiller la doc et google pour trouver comment parcourir un tableau en Javascript avec une boucle `for` et logger chacune des lettres de manière indépendante.


### Suite de Fibonacci

> Définition
> La suite de Fibonacci est une suite d'entiers dans laquelle chaque terme est la somme des deux termes qui le précèdent. Elle commence généralement par les termes 0 et 1 (parfois 1 et 1) et ses premiers termes sont : 0, 1, 1, 2, 3, 5, 8, 13, 21, etc.

Générez et logguez les 20 premiers nombres de cette suite.


### Triangle et papillon

Dans le body de votre page, ajoutez la div suivante :

```
<div id="content"></div>
```

On va commencer à manipuler les éléments de la page. Dans le JS :

```
// on sélectionne un élément de notre page
let divContent = document.querySelector("#content");

console.log('divContent', divContent);

// on y ajoute du contenu
divContent.append('plop');

```

Votre travaille maintenant est de générer un triangle :

```
o
oo
ooo
oooo
ooooo
oooooo
ooooooo
oooooooo
ooooooooo
oooooooooo
ooooooooooo
```

Etape suivante, générer ceci : 

```
o
oo
ooo
oooo
ooooo
oooooo
ooooooo
oooooooo
ooooooooo
oooooooooo
ooooooooooo
oooooooooo
ooooooooo
oooooooo
ooooooo
oooooo
ooooo
oooo
ooo
oo
o
```

Etape suivante 

```
o                    o
oo                  oo
ooo                ooo
oooo              oooo
ooooo            ooooo
oooooo          oooooo
ooooooo        ooooooo
oooooooo      oooooooo
ooooooooo    ooooooooo
oooooooooo  oooooooooo
oooooooooooooooooooooo
oooooooooo  oooooooooo
ooooooooo    ooooooooo
oooooooo      oooooooo
ooooooo        ooooooo
oooooo          oooooo
ooooo            ooooo
oooo              oooo
ooo                ooo
oo                  oo
o                    o
```

Et voilà, vous avez un magnifique papillon.
