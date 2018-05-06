### Objets

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [objet](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Utiliser_les_objets) en JavaScript.

> En JavaScript, un object est un ensemble propriétés (variables) et de méthodes (function)
> regroupées sous une même entité logique.
>
> Vous pouvez vous représenter un object en JS comme un objet réel avec ses caractéristiques propres et actions propres

### Premier exemple

Un exemple vaut mieux qu'un long discours.

```javascript
let o = {};
// ou
let oo = new Object();
```

On vient de créer un objet vide. Ajoutons des propriétés à notre objet.

```javascript
let myCar = {
    brand: 'Peugeot',
    model: '308',
    year: 2015,
    
    honk: function() {
        console.warn('TUT TUT !!');
    }
}
```

Pour utiliser les propriétés d'un objet, on procède ainsi :

```
//...

console.log('Marque : ', myCar.brand);
console.log('Modèle : ', myCar.model);

myCar.honk();

```

### Manipulation

Créez 3 personnes (object), dont les propriétés seront : 
- firstName
- lastName 
- age 
- email
- gender

```javascript
let people01 = {
    firstName: 'Patrick',
    // ...
};
```

Créez une méthode `fullName` qui renvoie le nom et prénom.


Mettez ces 3 personnes dans un Array :

```
let people = [
    // ...
];
```

Créez une fonction pour chacune des actions demandées, prennant en paramètre un tableau :
- le nombre de fille(s)
- le nombre de garçon(s)
- donner le nom de la personne la plus agée
- donner le nom de la personne la plus jeune
- le nombre de personne dont l'email se termine par 'gmail.com'


