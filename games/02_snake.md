### Snake

Nous allons créer notre premier jeu en JavaScript, inspiré du snake du Nokia 3310.

#### Le serpent

L'élément principal du jeu est le serpent, qui se déplace automatiquement d'une case toutes les n millisecondes.
Il peut se déplacement dans 4 directions (haut, bas, droite, gauche)

Dans un premier temps, notre serpent ne sera qu'un carré de 20x20 pixel;

Copiez le code suivant pour avoir le html de base du projet :

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Snake</title>
    <style>
        html, body{
            width: 100%;
            height: 100%;
            margin: 0;
            padding: 0;
        }

        #container{
            position: relative;
            width: 100%;
            height: 100%;
            box-sizing: border-box;
        }

        #snake{
            position: absolute;
            top: 50px;
            left: 50px;

        }

        .snake-part{
            display: block;
            width: 20px;
            height: 20px;
            background-color: darkgreen;
        }

    </style>
</head>
<body>
    <div id="container">
        <div id="snake">
            <div class="snake-part"></div>
        </div>
    </div>
</body>
</html>
```

Maintenant, la structure de base du code JS à mettre juste avant </body>

```
<script type="text/javascript">
    // Déclaration des variables globales à notre programme
    const snake = document.querySelector('#snake');
    
    function initKeyboardListener() {
        // écoute des event clavier
    }
    
    function moveSnake() {
        // déplacement du serpent
    }
    
    function init() {
        initKeyboardListener();
    
        // on lance la fonction de déplacement au rythme de 3 images par seconde
        setInterval(function() {
            moveSnake();
        }, 1000 / 3)
    }
    
    init();
</script>
```


Un exemple pour les enfants que ne connaissent pas : [lien](http://patorjk.com/games/snake/)