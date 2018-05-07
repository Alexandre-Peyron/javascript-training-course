### Casse brique

Nous allons créer notre premier jeu en JavaScript, un casse briques.

#### Structure de base

Notre jeu va être composé de plusieurs éléments :
- un contenant `container` qui va donner les limites visuelles et physique du jeu
- une barre `paddle`, à déplacer au clavier qui sert à renvoyer la balle
- une balle `ball`, qui se déplace et rebomdie sur les murs, les bricks et la barre. Lorsqu'elle touche le bas du container, c'est Game Over.
- des briques `bricks, placées en haut du container, qui disparaissent lorsque la balle les touche.


Copiez le code suivant pour avoir le html de base du projet, vous avez toute liberté de modifier les couleurs :

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Casse Brique</title>
    <style>
        html, body{
            width: 100%;
            height: 100%;
            margin: 0;
            padding: 0;
        }

        #container{
            position: relative;
            width: 800px;
            height: 800px;
            box-sizing: border-box;
            background-color: aliceblue;
            margin: 0 auto; /* centrage horizontal */
        }

        #paddle {
            position: absolute;
            bottom: 50px;
            left: 200px;
            width: 100px;
            height: 20px;
            background-color: brown;
        }

        #ball {
            position: absolute;
            left: 300px;
            bottom: 200px;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: darkgreen;
        }

        .brick {
            position: absolute;
            background-color: midnightblue;
        }


    </style>
</head>
<body>
    <div id="container">
        <div id="ball"></div>
        <div id="paddle"></div>
    </div>
</body>
</html>
```

Maintenant, la structure de base du code JS à mettre juste avant </body>

```javascript
    // Elements HTML
    const container = document.querySelector('#container');
    const paddle = document.querySelector('#paddle');
    const ball = document.querySelector('#ball');
    const bricks = [];


    // Variable globales
    // ...        
            
           
    /**
     * Keyboard event
     */
    function initKeyboardListener() {
        document.addEventListener('keydown', onKeyDown, false);
        document.addEventListener('keyup', onKeyUp, false);
    }

    /**
     * On key down keyboard
     */
    function onKeyDown(event) {
        
    }

    /**
     * On key up keyboard
     */
    function onKeyUp(event) {
        
    }


    /**
     * Move Paddle
     */
    function movePaddle() {
        
    }
            
    /**
     * 60 FPS rendering
     */ 
    function loop(){
        window.requestAnimationFrame(function() {
            movePaddle();

            loop();
        })
    }

    /**
     * Init game
     */
    function init() {
        //Init
        initKeyboardListener();
        
        loop();
    }

    init();
```

A présent, vous avez une zone de jeu et une structure de base.

### Mouvement de la barre

Première étape, nous allons animer le mouvement de la barre grâce aux touches du clavier

On a besoin de pour ça, de 2 variables globales. Ajoutez les, au début du script, à la suite des autres :

```javascript
// [...]

// Paddle config
let moveLeft = false;
let moveRight = false;
```

Celles-ci vont déterminer si on est en train d'appuyer ou non sur les touches du clavier pour un déplacement latéral.

Mettons à jour les fonctions `onKeyDown` et `onKeyUp`.

Sur `onKeyDown` on va agir ainsi : 
- ArrowLeft appuyée -> moveLeft = true
- ArrowRight appuyée -> moveRight = true

Sur `onKeyUp` comportement inverse. On passe les variables à false au relachement du bouton.

Maintenant qu'on a ça, on peut modifier `movePaddle`

De quoi on a besoin pour déplacer la barre ?
- De sa position initiale
- de la valeur du "pas" à chaque déplacement

```javascript
const step = 4;

let currentPaddlePositionX = paddle.offsetLeft;
```

A partir de là, changez la valeur de `currentPaddlePositionX` d'un "pas" ou ("-pas") en fonction de `moveLeft` et `moveRight`

Attribuez la nouvelle valeur à la barre

```javascript
paddle.style.left = currentPositionLeft + 'px';
```

A présent votre barre bouge de droite à gauche.


### Limites de la barre

Nouveaux problème, la barre sort de la zone de jeu.

Il faut fixer les limites, comme avec les enfants.

Les règles sont :
- si la position left de la barre est inférieure à 0, la position left est 0
- si la position left (+ la largeur de la barre) est supérieure à la largeur du container, la position left et la largeur du container, moins la largeur de la barre :D

Tout se passe dans movePaddle encore une fois.

Déterminez de quelles variables vous avez besoin :

```
let paddleWidth = ...;
let paddleLeft = ...;
let paddleRight = paddleLeft + paddleWidth;

let containerWidth = ...;
```

A vous de jouer.