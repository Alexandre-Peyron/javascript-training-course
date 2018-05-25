### jQuery

L'objectif est de comprendre le fonctionnement de la librairie [jQuery](https://jquery.com/)

> jQuery est aujourd'hui de moins en moins utilisé sur des projets neufs, mais est encore présent sur une grande majorité de sites web.
> Pour comprendre l'importance qu'à eu jQuery, il faut revenir 10 ans en arrière.
> A cette époque le JS était bien moins développé qu'aujourd'hui et surtout il y avait un écart monstrueux entre les navigateurs en termes de compatibilité et de performances.
>
> jQuery est arrivé et a gommé tout ça. 
>
> On avait un code unique pour l'ensemble des navigateurs, jQuery s'occupant de la compatibilité.
> Et surtout, on avait un pannel d'outils qui facilité grandement le travail (sélecteurs, ajax).
>
> Aujourd'hui, la plupart de ces outils ont été intégrés nativement dans JavaScript, jQuery a donc perdu de son intérêt. 
> Mais cela reste intéressant de comprendre son usage.

### Intégrer jQuery

Pour ajouter jQuery à un projet, rien de plus simple. Il suffit d'ajouter une balise script
 
```html
 <!DOCTYPE html>
 <html lang="en">
 <head>
    <meta charset="UTF-8">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script type="text/javascript" src="monScript.js"></script>
 </head>
 <body>
 
 </body>
 </html>
 
```
 
Voilà, jQuery est utilisable dans votre projet.


### Les sélecteurs

Pour utiliser un sélecteur jQuery, on utilise `$()`.

```javascript
let menu = $('#menu'); // Sélection de l'élément dans le DOM qui possède l'ID #menu
```

Attention, ce qui est présent dans la variable `menu`, c'est un objet jQuery, pas un DOM Element comme avec un sélecteur JS classique.

Exercice : récupérez le HTML suivant et utilisez les sélecteurs jQuery pour trouver les 
 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
</head>
<body>
    <section id="sidebar">
        <a href="/accueil" class="logo" ><img src="" alt="LOGO"></a>
        <ul>
            <li>
                <a href="/accueil">Accueil</a>
            </li>
            <li>
                <a href="/blog">Blog</a>
            </li>
            <li>
                <a href="/contact">Contact</a>
            </li>
        </ul>
    </section>
    <main>
        <h1>Mon titre</h1>
        
        <p class="text-top">"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>
        <p class="text-middle lead">"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>
        <p class="text-middle">"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>
        <p class="">"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>    
    </main>
    <footer>
        <ul>
            <li>
                <a href="/accueil">Accueil</a>
            </li>
            <li>
                <a href="/blog">Blog</a>
            </li>
            <li>
                <a href="/contact">Contact</a>
            </li>
        </ul>
    </footer>
</body>
</html>
```

Les sélecteurs à créer :
- la sidebar
- le main
- le footer
- le h1
- les `a` du menu de la sidebar
- tous les `a` sauf celui avec la class `logo
- les `p`
- les `p` dans avec la class `lead`
- les `p` dont la class commence par `text-``


# Manipulation

On vient de voir les sélecteurs, mais on en fait quoi de ces éléments sélectionnés.

On les manipule.

jQuery propose toute une série de méthode pour travailler sur nos éléments (cacher, afficher, annimer...)

```javascript
$('#menu').hide(); // cache la div dont l'ID est menu
```

Les animations :
- .show() : affiche le(s) élément(s) sélectionné(s).
- .hide() : masque le(s) élément(s) sélectionné(s).
- .toggle() : affiche ou masque le(s) élément(s) sélectionné(s) en fonction de son/leur état actuel.
- .fadeIn() : fait apparaître en fondu le(s) élément(s) sélectionné(s).
- .fadeOut() : fait disparaître en fondu le(s) élément(s) sélectionné(s).
- .slideUp() : masque le(s) élément(s) sélectionné(s) avec un défilement vers le haut.
- .slideDown() : masque le(s) élément(s) sélectionné(s) avec un défilement vers le bas.
- .slideToggle() : affiche ou masque 

Les manipulations :
- .html() : remplace le contenu HTML de le l'élément
- .text() : remplace le texte de la page
- .replaceWith() : remplace le(s) élément(s) sélectionné(s) entièrement, pas juste le texte ou le HTML à l'intérieur
- .remove() : supprime les éléments de la page
- .before() : insère du contenu avant le(s) élément(s) sélectionné(s)
- .after() : insère du contenu après le(s) élément(s) sélectionné(s)
- .prepend() : insère du contenu à l'intérieur du/des élément(s) sélectionné(s) (après la balise HTML ouvrante)
- .append() : insère du contenu à l'intérieur du/des élément(s) sélectionné(s) (avant la balise HTML fermante)
- .attr() : définit un attribut et sa valeur ou simplement récupère sa valeur
- .removeAttr() : supprime un attribut, RIP
- .addClass() : ajoute une nouvelle classe à/aux élément(s) sélectionné(s) (sans remplacer sa classe actuelle)
- .removeClass() : supprime une classe du/des élément(s) sélectionné(s)
- .css() : liste les propriétés CSS

Le DOM :
- .find() : trouve un/des élément(s) correspondant au paramètre dans la sélection actuelle
- .parent() : accède au parent direct d'un/des élément(s) ou à ses parents si on utilise .parents()
- .children() 

Les propriétés de l'élément :
- .height() 
- .width ()
- .innerHeight() : hauteur en comptant les marges intérieures
- .innerWidth() : largeur en comptant les marges intérieures
- .outerHeight() : hauteur en comptant les marges intérieures et les bords
- .outerWidth() : largeur en comptant les marges intérieures et les bords
- .offset() : définit les coordonnées d'un élément relativement au coin en haut à gauche de l'objet document
- .position() : définit les coordonnées d'un élément relativement à son parent direct