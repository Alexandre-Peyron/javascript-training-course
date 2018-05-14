### Manipulation du DOM

L'objectif de ce cours est de comprendre ce qu'est le DOM et comment on le manipule.

> Le DOM d'après Wikipedia :
> Le Document Object Model (ou DOM) est une recommandation du W3C qui décrit une interface indépendante de tout langage de programmation et de toute plate-forme, permettant à des programmes informatiques et à des scripts d’accéder ou de mettre à jour le contenu, la structure ou le style de documents XML. Le document peut ensuite être traité et les résultats de ces traitements peuvent être réincorporés dans le document tel qu’il sera présenté.
>
> Personnellement, j'ai rien compris.
>
> De manière plus simple, le DOM c'est la structure de votre page HTML, tout ce qui se trouve entre les 2 balises `<html>`.
> Toutes les balises qui se trouvent dans le DOM peuvent être sélectionnées, modifiées, déplacées, incorporées, (re)créées, supprimées... ça ouvre un champs des possibles très large.


### Premier sélecteur

Récupérer le code suivant :

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>06 DOM</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
</head>
<body>
<div class="container">
    <div clas="row">
        <h1>Inscription</h1>
        <form id="form__register" action="/" method="post" class="col-6" novalidate="novalidate" >
            <div class="form-group is-invalid">
                <label for="form__register_lastname">Nom*</label>
                <input type="email" class="form-control" id="form__register_lastname" value="Un nom comme un autre" required>
                <div class="form-errors"></div>
            </div>
            <div class="form-group">
                <label for="form__register_firstname">Prénom</label>
                <input type="email" class="form-control" id="form__register_firstname">
                <div class="form-errors"></div>
            </div>
            <div class="form-group">
                <label>Sexe</label>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="form__register_gender" id="form__register_gender01" value="M" >
                    <label class="form-check-label" for="form__register_gender01">
                        Homme
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="form__register_gender" id="form__register_gender02" value="F">
                    <label class="form-check-label" for="form__register_gender02">
                        Femme
                    </label>
                </div>
                <div class="form-check disabled">
                    <input class="form-check-input" type="radio" name="form__register_gender" id="form__register_gender03" value="A" checked>
                    <label class="form-check-label" for="form__register_gender03">
                        Non renseigné
                    </label>
                </div>
            </div>
            <div class="form-group">
                <label for="form__register_email">Email*</label>
                <input type="email" class="form-control is-invalid" id="form__register_email" value="ploporange.com" required>
                <div class="form-errors">
                    <small class="text-danger">
                        Cet email n'est pas valide
                    </small>
                </div>
            </div>
            <div class="form-group">
                <label for="form__register_password">Mot de passe*</label>
                <input type="password" class="form-control" id="form__register_password" required>
                <div class="form-errors"></div>
            </div>
            <div class="form-group">
                <label for="form__register_password-repeat">Validation mot de passe*</label>
                <input type="password" class="form-control" id="form__register_password-repeat" required>
                <div class="form-errors"></div>
            </div>
            <div class="form-group row">
                <label class="col-6" for="form__register_conditions">
                    Accepter les conditions*
                </label>
                <input type="checkbox" class="col-6 form-control" id="form__register_conditions" required>
                <div class="form-errors col-12">
                    <small class="text-danger">
                        Vous devez accepter les conditions générales
                    </small>
                </div>
            </div>
            <hr>
            <button type="submit" class="btn btn-success">Valider</button>
        </form>
    </div>
</div>
<script type="text/javascript">
</script>
</body>
</html>
```

Il s'agit d'une page simple avec un formulaire d'inscription. Pour explication, les class utilisées proviennent du framework CSS [bootstrap 4](https://getbootstrap.com/).

Comme dit précédemment, chaque élément de la page est sélectionnable. Soit grace à son ID, sa class, son type/balise, son état...

Commençons par sélectionner l'input avec le nom.

```
let inputLastname = document.getElementById('form__register_lastname');

console.log('Input Lastname', inputLastname);
```

Voici notre premier sélecteur :
- `document` indique qu'on commence la recherche de notre sélecteur à la racine du DOM.
- `getElementById` va chercher l'élément dont l'ID est `form__register_lastname` et le met dans une variable.

Au console.log, cela affiche le HTML de l'élément, on est en présence d'un DOM Element.

Sur [ce lien](https://www.w3schools.com/jsref/dom_obj_all.asp) vous pouvez voir l'ensemble des propriétés et méthodes d'un object DOM Element. 

### Manipulation simple

Dans le HTML, ajoutez une value="mon nom ou autre chose" à l'input `form__register_lastname`. Ajoutez ensuite le code suivant :

```javascript
let inputLastnameValue = inputLastname.value;
console.log('Valeur : ', inputLastnameValue);
```

On peut voir que en JS, on vient de récupérer le contenu de l'input.

A présent, testez la valeur de l'input, les conditions sont :
- la chaine de caractères ne peut contenir que des lettres, des chiffres, des - et des espaces
- elle doit faire entre 3 et 30 caractères

Si les toutes les conditions sont bonnes **ajoutez** la class `is-valid` sur l'input. 

Si ce n'est pas le cas :
- mettre `is-invalid` 
- ajoutez un message d'erreur dans `<div class="form-errors"></div>` en dessous de l'input

### Manipulations multiples par class

Nous venons de tester un input, le problème c'est que actuellement au chargement, des messages d'erreurs sont déjà présents.

Faisons une sélection multiple

```javascript
let inputErrors = document.getElementsByClassName('form-errors');
```

Nous venons de sélectionner l'ensemble des éléments qui possèdent la class `form-errors`.

`inputErrors` est donc un tableau de DOM Element.

Maintenant il faut supprimer les messages d'erreurs :
- parcourir l'ensemble des éléments 
- supprimer le contenu texte


### Manipulations multiples par type

Les messages d'erreurs ne sont plus. Mais certains input possèdent en encore la class `is-invalid`.

La ligne suivante sélectionne l'ensemble des input de la page :

```javascript
let inputs = document.getElementsByTagName('input');
```

A présent supprimez la class `is-invalid` pour tous les inputs




