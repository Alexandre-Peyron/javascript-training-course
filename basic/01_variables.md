### Variables

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [variables](https://fr.wikipedia.org/wiki/Variable_(informatique)) en JavaScript.

> La notion de variable est présente dans tous les langages de programmation.

> Une variable est une association clé/valeur. 
> Autrement dit, c'est un espace pour stocker une information.
>
> Exemple en js :
> `let maVariable = "Une valeur de texte"`
> ou encore
> `let encoreUneVariable = 5`
>
> Pour vous l'imager encore plus, imaginez toute une série de casiers le long d'un mur. Chaque casier est une variable, le nom inscrit sur le casier étant le nom de la variable et l'intérieur du casier la valeur.


#### Premier script

Pour comprendre rien de mieux que la pratique.

Créez un nouveau fichier vide : `variables.html` par exemple.

Ouvrez le fichier dans votre éditeur de texte et ajoutez ça :

```
<html>
    <head>
        <title>Les Variables en JavaScript</title>
        <meta charset="UTF-8">
    </head>
    <body>
        <!-- Ici vos futures balises html -->
        <script type="text/javascript">
            // ici votre code javascript
            // ...
        </script>
    </body>
</html>
```

Sauvegardez.

Maintenant ouvrez ce fichier dans votre navigateur web (Chrome, Firefox...).

Rien de s'affiche, normal.

Ouvrez les **outils pour développeur**, pour l'onglet **console**.

Toujours rien ne s'affiche, normal.

Dans la balise script de votre fichier html, ajoutez ceci :

``` 
console.log("Un texte pour voir si ça s'affiche");
```

Sauvegardez, retournez dans le navigateur et actualisez (touche F5 ou CTRL+R)

Si le message s'affiche dans la console, félicitation votre premier script en JS fonctionne.

#### Les variables - Number

> La valeur d'une variable peut être de différents types :
> Un nombre (Number)
> Une chaine de caractère (String)
> Un tableau (Array)
> Un objet (Object)
> Un booléen, (Boolean, true ou false) 

Voyons maintenant comment réagissent les variables lorsqu'on les utilise.

Déclarez une nouvelle variable au début de votre script :

```
let monNombre = 5;
```

Logguez `monNombre`. Sauvegardez, actualisez (il faut que ça devienne automatique pour vous, on va faire ça des milliers de fois :D )

Ca doit afficher 5.

A la suite, ajoutez : `monNombre += 2`. Logguez à nouveau `monNombre`.

Notre variable a changé.

> En effet, une variable possède une valeur à sa déclaration, Exemple 5, "mon texte" ou encore `null` si on ne met rien.
> Mais cette valeur n'est pas figée dans le temps. On peut la modifier, la transformer, la réattribuer.

Effectuez le même travail pour les lignes suivantes :

`monNombre = monNombre * 3`
`monNombre -= 1`
`monNombre = monNombre / 5`
`monNombre = monNombre % 3`

On vient de voir ici les différents opérateurs utilisables en javascript pour additionner, multiplier, soustraire, diviser ou encore donner le reste d'une division euclidienne.

#### Les variables - String

Créez une nouvelle variable contenant une chaine de caractères :

`let monTexte = "Je m'appelle :"`

Logguez, sauvegardez, actualiser.

Maintenant, sans toucher à la déclaration de la variable, essayez d'ajouter votre prénom à la fin de la chaine.

Une fois que c'est fait, mettez votre prénom dans une variable et essayez à nouveau de l'ajouter en fin de chaine.

Ajoutez 'Bonjour,' en début de chaine.

Nouvelle problématique, le "Je" au milieu de la chaine est en majuscule, ce n'est pas très propre.
En fouillant un peu dans la [documentation de JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript), je suis tombé sur cette [méthode](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/String/toLowerCase) pour enlever les majuscules d'une chaine de caractères.

Utilisez la.

#### Conclusion

Vous venez de coder vos premières lignes de JavaScript, Bravo.
