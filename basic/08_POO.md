### POO - Programmation Orientée Objet

L'objectif de ce cours est de comprendre les bases de la [POO](https://developer.mozilla.org/fr/docs/Web/JavaScript/Introduction_%C3%A0_JavaScript_orient%C3%A9_objet).

> La POO est une manière d'organiser et de se réprésenter le code. Tout devient objet, 
cela permet de regrouper des fonctionnalités sous une même entité logique et de
rendre le code plus maintenable et compréhensible.

### Les class

Après cette petite intro très abstraite, entrons dans le vif du sujet. Comment se représente la POO en JavaScript ?

Lors de l'exercice sur les objets, nous avions créé plusieurs objets 'person'.
La problématique, c'est que du code se répétait plusieurs fois, c'est pas terrible.

```javascript
let person01 = {
    firstName: 'Alex',
    lastName: 'P',
    age: 28,
    gender: 'M',
    email: 'plop@gmail.com',
    fullName: function(){
        return this.firstName + ' ' + this.lastName;
    }
};
```

Si on change une méthode (ex fullName), cela veut dire qu'on doit la changer dans les N objets créés. Ce n'est pas viable sur le long terme.

Pour palier à ce problème, les class entre en jeu. Une class représente le modèle de notre objet. Une fois déclarée, nous pouvons créer N objets basés sur ce modèle. Et une modification de la class, entrainement une modification sur l'ensemble des objets.


```javascript
class Person {
    constructor(firstname, lastname, email, age, gender) {
        this.firstname = firstname;
        this.lastname = lastname;
        this.email = email;
        this.age = age;
        this.gender = gender;
    }
    
    fullName() {
        return this.firstname + ' ' + this.lastname;
    }
}


let p1 = new Person('Alex', 'P', 'plop@gmail.com', 29, 'M');

console.log('p1', p1)

```

Le terme `class` est le point d'entrée de notre nouveau modèle, il est suivi du nom de la class (ici Person, mais on aurait pu mettre Human, People... ce qui nous semble le plus explicite)

Vient ensuite le mot `constructor`. C'est la méthode qui est automatiquement appelée lorsqu'on fait un `new Person(...)`

Les paramètres du `new Person('Alex'...)` étant ceux que le constructor attend et qui vont définir chaque des propriétés de notre objet.

Le terme `this` est important également, il fait référence à l'objet en cours.

Exercice : 
- créez 3 à 5 nouvelles personnes.
- mettez les dans un tableau
- ajoutez une nouvelle méthode dans notre class 'isAdult', revoit un boolean si la personne a plus de 18 ans ou non
- parcourez le tableau et comptez le nombre de personnes adultes



 