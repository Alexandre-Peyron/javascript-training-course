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
paddle.style.left = currentPaddlePositionX + 'px';
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


### Mouvement de la balle

Maintenant, qu'on a une barre fonctionnelle, il nous faut une balle.

Nous allons créer une nouvelle fonction `moveBall` 
à la suite de `movePaddle` et qu'on va appeler dans la fonction `loop`;

Dans la même optique, en début de script, nous allons déclarer 3 nouvelles variables globales

```javascript
// Ball config
let ballRadius = 10;
let ballDx = 2;
let ballDy = -2;
```

- `ballRadius` est le rayon de la ball, cela va nous servir dans les calculs de limites
- `ballDx` est la vitesse de déplacement de la balle en X
- `ballDy` est la vitesse de déplacement de la balle en Y

Comme pour la paddle, pour calculer le mouvement, il nous faut :
- la position actuelle de la balle en X et Y
- ajouter ballDx et ballDy
- attribuer les nouvelles valeurs

```javascript
let currentPositionLeft = ball.offsetLeft;
let currentPositionTop = ball.offsetTop;

currentPositionLeft += ballDx;
currentPositionTop += ballDy;

ball.style.left = currentPositionLeft + 'px';
ball.style.top = currentPositionTop + 'px';
```

Voilà, notre balle se déplace. Problème, elle sort rapidement de la zone de jeu.

### Limite de la balle

Il faut maintenant calculer les limites de la balle sur chacun des bords du jeu : top, left, bottom et right.

Définition des différentes limites :

- Top
    - La position Y de la balle, ne doit pas être inférieure à 0
    - ballDy devient -ballDy
- Bottom
    - La position Y de la balle, ne doit pas être supérieure à la hauteur du jeu
    - ballDy devient -ballDy
- Left 
    - La position X de la balle, ne doit pas être inférieure à 0
    - ballDx devient -ballDx
- Right
    - La position X de la balle, ne doit pas être supérieure à la largeur du jeu
    - ballDx devient -ballDx
    
A présent, votre balle doit rebondir sur les murs.

Nouveau problème, à droite et en bas, on a l'impression qu'elle passe à travers le mur.

Ce comportement est normal, car le point de référence n'est pas le centre de la balle mais son top left.

Le ballRadius a toute son importance ici. Sur le calcul du right c'est bien la partie droite de la balle que l'on veut. Idem pour le bottom. 
Modifiez les conditions pour que ce problème visuel n'apparaisse plus.


### Collision entre la balle et la barre

Maintenant que la balle et la barre restent dans la zone de jeu. Nous allons détecter la collision entre elle.

En français, une collision signifie que "le cendre de la balle se trouve dans la zone de la barre".

Autrement dit, si 
- la position centreX de la balle se situe entre la positionLeftX et la positionRightX de la barre
ET
- la position centreY de la balle se situe entre la positionTopY et la positionBottomY de la barre

Liste des variables nécessaires pour ces calculs :

```
let ballCenterX = ...
let ballCenterY = ...

let paddleWidth = paddle.offsetWidth;
let paddleHeight = paddle.offsetHeight;

let paddleLeftX = ...
let paddleRightX = paddleLeftX + paddleWidth;
let paddleTopY = ...
let paddleBottom = paddleTopY + paddleHeight;

```

Ecrivez maintenant la condition qui détermine la collision.

Lors d'une collision `ballDy` devient `-ballDy`.

Le comportement est maintenant fonctionnel, mais pas terrible encore.

Faites en sorte que lorsque :
- la balle tape sur la moitié gauche de la barre, `ballDx` devient négatif
- la balle tape sur la moitié droite de la barre, `ballDx` devient positif