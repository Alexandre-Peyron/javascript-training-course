### AJAX

L'objectif de ce cours est de comprendre le fonctionnement et l'utilité de [l'ajax](https://www.w3schools.com/xml/ajax_intro.asp).

> La puissance et l'intérêt de JavaScript réside en grande partie dans l'AJAX (Asynchronous JavaScript And XML).
> L'AJAX est un concept qui repose principalement dans le fait d'effectuer des échanges (envoi et réception de données) avec un serveur sans rechargement de page.
>
> On peut ainsi :
> - demander des données
> - envoyer des données pour enregistrement
> - modifier une page (complètement ou en partie)
 
> Pour faciliter l'approche, nous allons au cours de cet exercice utiliser jQuery et sa méthode $.ajax
> mais cette méthode utilise l'objet natif de JavaScript XMLHttpRequest qu'on pourrait tout à fait utiliser sans jQuery.

### Premier appel

Pour ce premier exemple, nous allons faire appel à une API distante qui va nous donner la météo du jour.

Créer un compte sur ce site : [https://home.openweathermap.org/users/sign_up](https://home.openweathermap.org/users/sign_up)

> Pour utiliser la plupart des APIs, il faut pouvoir être authentifié lors d'un appel.
> C'est pour cela qu'il est nécessaire de créer un compte et de récupérer un token (jeton) d'authentification
> à transmettre lors d'un appel.

Créez un nouveau fichier html et **hébergez le sur un serveur local**.

Ajoutez le JS suivant :

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript">
    $(document).ready(function(){
        callOpenWeatherMap();
    });

    function callOpenWeatherMap(){
        let apikey = "votre clé d'api";

        $.ajax({
            method: "GET",
            url: "https://api.openweathermap.org/data/2.5/weather?q=Lyon&units=metric&APPID=" + apikey,
            dataType: "JSON"
        }).done(function(data) {
            // fonction lancée au retour de l'appel
            console.log('data', data)
        }).fail(function(error) {
            // Si une erreur survient lors de l'appel
            console.warn(error);
        });
    }
</script>
```
Dans la console s'affiche l'objet JSON de la réponse avec toute ses data. Parcourez le.

Pour explications, au chargement de la page, nous lançons la fonction `callOpenWeatherMap` qui elle même fait un appel ajax `$.ajax`.

Notre appel Ajax prend 1 paramètre qui est un objet avec plusieurs propriétés :
- method : le type d'appel, ici GET signifie qu'on veut récupérer des données
- dataType : le format que l'on souhaite en réponse
- url : l'url d'appel avec elle aussi différents paramètres
    - https://api.openweathermap.org/ : url de base l'API
    - data/2.5/weather : méthode utilisée sur l'API
    - ?xxx=yyy : options passés à la méthode weather
    
    
Si on entre dans le détail des paramètres passés : 
- q=Lyon : on détermine sur quelle ville on souhaite récupérer la météo
- units=metrics : change l'affichage de la réponse, notemment pour afficher les dégrés en Celcius
- APPID : token d'authentification qui vous permet d'accéder à l'API. Sans ça, vous tombez sur une page 401 (Unauthorized)


Voilà, votre premier appel ajax vers une API distante.


### Icons

L'API Open Weather Map fournit un pack d'icon pour l'affichage des données.

[https://openweathermap.org/weather-conditions](https://openweathermap.org/weather-conditions)

Dans votre page, faites en sorte d'afficher l'icon correspondante au Weather.

Son nom se trouve dans la réponse JSON dans `weather[i].icon`.

Affichez également le nom de la ville dans la page.


### Champ de recherche

A présent, nous allons faire évoluer notre page pour afficher la météo, 
plus seulement pour Lyon, mais pour chaque ville recherchée.

Ajoutez un formulaire avec un `input type text` et un `submit` de recherche.

A la validation de l'input, il faut :
- récupérer la valeur (qui sera la nom d'une ville) 
- appliquer ce nom de ville à l'appel vers l'API.
- mettre à jour le DOM avec les nouvelles données



