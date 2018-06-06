### Tasks Runner - Gulp

Ici nous allons aborder la notion de Task Runner.

> Outils indispensable du développeur, les Task Runner servent à automatiser 
> bon nombre de tâches répétitives :
> - compression des fichiers
> - minification (JS et CSS)
> - traitement sur des images
> - déploiement

> Il existe pléthore d'outils.
> 
> [Grunt](https://gruntjs.com/) fut le premier, mais est aujourd'hui dépassé.
> [Gulp](https://gulpjs.com/) arriva ensuite. Aujourd'hui un peu dépassé également 
> mais il reste des cas d'usages où il est encore très utile.
> Il est de même très facile d'accès pour une première approche.
> 
> [WebPack](https://webpack.js.org/) est la nouvelle référence. 
> Sa force ? Proposer un tas de fonctionnalités déjà en place, 
> et parfaites pour des projets Front avec les frameworks récents.


### Prérequis

Pour utiliser ce genre d'outil, il vous faut [NodeJS](https://nodejs.org/fr/) sur votre machine.

Si ce n'est pas encore le cas, installez-le.


### NPM

Dans un terminal/console placez vous dans votre projet.

Faites la commande suivante :

```bash
npm init
```

Répondez aux questions. Un nouveau fichier vient d'apparaitre à la racine de votre projet : `package.json`

Ce fichier liste tous les modules node externes (les dépendances) nécessaires à votre projet.

Quelqu'un qui récupérera votre projet depuis Git, aura juste à faire un `npm install` pour télécharger toutes les dépendances

Ces dépendances vont être téléchargées dans un dossier `node_modules` à la racine de votre projet.

### Gulp - Installation

Installez Gulp ainsi :

```bash
npm install gulp-cli -g
npm install gulp -D
```

Créez un fichier `gulpfile.js` à la racine de votre projet.

Lancez cette commande pour voir si gulp est correctement installé.

```bash
gulp --help
```

Si tout fonctionne vous avez l'aide de Gulp qui apparait

### Gulp - Module

La puissance de Gulp vient de ses modules. 
Peu importe la tâche que vous voulez automatiser quelqu'un à déjà surement développé un plugin pour ça.

Nous allons ici regrouper tous nos fichiers JS en un seul pour améliorer les performances en front.


Installons les modules nécessaires. Faites les commandes suivantes :

```bash
npm install --save-dev gulp-concat
npm install --save-dev gulp-uglify
```

*gulp-concat* va concaténer les fichiers, autrement dit, les regrouper en un seul.
*gulp-uglify* va rendre nos fichiers moches : reduire leurs poids et les rendre illisible. 


Si vous regardez votre fichier package.json et le dossier node_modules, ils ont normalement changé.

### Première tâche

Nous allons créer notre première tâche de concaténation.

Dans votre fichier `gulpfile.js`


```javascript

const gulp = require('gulp');
const concat = require('gulp-concat');

gulp.task('app-js', function() {                // déclaration de la tâche, son nom : app-js
    return gulp.src('./js/*.js')                // liste des fichiers qu'on va chercher (tous les fichiers .js contenus dans le dossier /js)
               .pipe(concat('all.min.js'))      // action de concaténation et nom du fichier en sortie
               .pipe(gulp.dest('./web/js'));    // déplacement du fichier généré dans le dossier voulu
});
```

Dans le terminal, faites la commande suivante :

```bash
gulp app-js
```

Normalement, un nouveau fichier vient d'être généré dans `web/js`

### Watcher

Trouvez comment mettre en place un watcher sur vos fichiers JS.


### Sources

[http://putaindecode.io/fr/articles/js/gulp/](http://putaindecode.io/fr/articles/js/gulp/)
[https://www.alsacreations.com/tuto/lire/1686-introduction-a-gulp.html](https://www.alsacreations.com/tuto/lire/1686-introduction-a-gulp.html)
[https://github.com/gulpjs/gulp](https://github.com/gulpjs/gulp)
[https://la-cascade.io/gulp-pour-les-debutants/](https://la-cascade.io/gulp-pour-les-debutants/)
