### Condition

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité des [conditions](https://fr.wikipedia.org/wiki/Instruction_conditionnelle_(programmation)) en JavaScript.

> Comme pour les variables, ma notion de condition est présente dans tous les langages de programmation.

> if/else : voici les éléments de base d'une condition
> 
> Si une condition est vraie, j'execute tel script, sinon j'execute celui là.


#### Première condition


On repart de zéro. Créez un nouveau fichier vide : `conditions.html`.

Ouvrez le fichier dans votre éditeur de texte et ajoutez ça :

```
<html>
    <head>
        <title>Les Conditions en JavaScript</title>
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

Déclarer une nouvelle variable `monAge` contenant un nombre.

Notre première condition va tester si on est majeur ou non.

```
if (monAge > 18) {
    alert("Vous êtes majeur, tout est ok :) ");
}
else {
    alert("Vous êtes mineur, vous n'avez rien à faire ici.");
}

```

Testez votre script.

> Le chevron > permet de crer une comparaison et renvoit ensuite un Boolean (true ou false) qui permet d'exécuter la condition.
> Il existe plusieurs opérateur de comparaison
>
> `>` supérieur
>
> `<` inférieur
>
> `>=` supérieur ou égal
>
> `<=` inférieur ou égal
>
> `==` égaux
>
> `!=` différent
>

Nous allons maintenant rendre ça plus dynamique.

Modifier la déclaration de votre varible monAge, ainsi :

```
let monAge = prompt('Quel âge avez-vous ?');
```

Retestez votre script.


#### Exercice IMC

Nous allons créer un calculateur de IMC (Indice de Masse corporelle).

Pour cela, il faut : 
- connaitre la taille (centimètre)de l'utilisateur
- connaitre le poids (kg) de l'utilisateur

L'IMC est égale à IMC (kg/m-2)

Liste des valeurs comparatives :
- moins de 16,5	-> dénutrition
- 16,5 à 18,5 -> maigreur
- 18,5 à 25	-> corpulence normale
- 25 à 30 -> surpoids
- 30 à 35 -> obésité modérée
- 35 à 40 ->obésité sévére
- plus de 40 -> obésité morbide ou massive

A vous de jouer
