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
<body>
    <head>
        <title>Les Variables en JavaScript</title>
    </head>
    <body>
        <!-- Ici vos futures balises html -->
        <script type="text/javascript">
            // ici votre code javascript
            // ...
        </script>
    </body>
</body>
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


