### Events

L'objectif de ce cours est de comprendre les évènements en JavaScript.

> Le JavaScript est basé sur un modèle évènementiel.
>
> La lecture et l'interprétation du code ne se font pas de manière linéaire mais en fonction des évènements.
>
> Les évènements sont des "choses" qui se produisent sur les éléments du DOM. 
> A chaque intéraction de l'utilisateur, à chaque mouvement de souris, 
> tapotement sur le clavier, vous pouvez être sur qu'un [évènement est lancé](https://developer.mozilla.org/fr/docs/Web/Events).
>
> Pour "écouter" un évènement, on utilise la méthode `monElement.addEventListener('monEvent', fonctionAExecuter)`.


### Premier event

Utilisons le code et le formulaire de l'exercice précédent.

Nous allons écouter les évènements qui se produisent sur le formulaire pour le valider puis le soumettre.

Ajoutez ces lignes :

```javascript
let form = document.getElementById('form__register'); // on sélectionne notre form

form.addEventListener('submit', onSubmitForm); // on écoute l'event de la soumission

function onSubmitForm(event) { // fonction exécuté lors de la soumission
    event.preventDefault(); // on bloque le comportement par défaut
    
    // [...]
}
```

Ici on écoute la validation, et on bloque la soumission (pour pas que la page ne se recharge).

A chaque click sur le bouton submit, notre fonction prend la place du comportement normal.

On autorisera la soumission qu'une fois que toutes les données auront été validées.

Maintenant pour chaque champ du formulaire, créez une fonction qui va valider la données.
- Le nom
    - requis
    - pas de caractère spéciaux
    - entre 3 et 30 caractères
    
- Le prénom
    - pas de caractère spéciaux
    - entre 3 et 30 caractères
    
- L'email
    - Requis
    - est un email valide
    
- Mot de passe et répétition
    - Requis
    - entre 7 et 20 caractères
    - identique à la répétition
    - Bonus : contient au moins 1 chiffre, 1 lettre majuscule, 1 lettre minuscule, 1 caractère spécial (_-"'~|&%#@*+=:;.,?!(){}[]) \
    
 