![MNX icon](http://mnemotix.com/v2/assets/images/logo.svg =300x)

```
  ____                _     _                               _   _____  
 |  _ \              | |   | |                             | | / ____| 
 | |_) |  __ _   ___ | | __| |__    ___   _ __    ___      | || (___   
 |  _ <  / _` | / __|| |/ /| '_ \  / _ \ | '_ \  / _ \ _   | | \___ \  
 | |_) || (_| || (__ |   < | |_) || (_) || | | ||  __/| |__| | ____) | 
 |____/  \__,_| \___||_|\_\|_.__/  \___/ |_| |_| \___| \____/ |_____/  
             _                                                         
           _| |_                                                       
  __  __  |_   _|      _                      _    _                   
 |  \/  |   |_|       (_)                    | |  | |                  
 | \  / |  __ _  _ __  _   ___   _ __    ___ | |_ | |_  ___            
 | |\/| | / _` || '__|| | / _ \ | '_ \  / _ \| __|| __|/ _ \           
 | |  | || (_| || |   | || (_) || | | ||  __/| |_ | |_|  __/           
 |_|  |_| \__,_||_|   |_| \___/ |_| |_| \___| \__| \__|\___|           
```

                                                                                           

Overview
========

L'objectif de ce tutoriel est d'apprendre à créer une simple application Backbone/Marionette en utilisant des outils de productivité tels que Yeoman/Gulp.



Step 1 - Installation
---------------------

### Git

	brew install git
	
### NodeJS
	
	brew install node
	node --version && npm --version
	npm install --global npm@latest
	
### Yeoman

	npm install --global yo bower grunt-cli
	yo --version && bower --version && grunt --version
	
#### Installer le générateur Yeoman

	npm install --global generator-gulp-webapp
	

#### Générer le squelette de l'application

	mkdir my-webapp
	cd my-webapp
	yo gulp-webapp

Step 2 - Gulp
-------------

### Présentation
[Gulp](http://gulpjs.com/) est un gestionnaire de build pour les projets Javascript.

C'est un équivalent Javascript de Ant/Maven en Java. Gulp est le successeur direct d'un autre outil de build JS très connu : [Grunt](http://gruntjs.com/). La différence principale entre les deux se résume à la manière dont les tâches vont être résolues en interne. [Gulp est plus performant](http://tech.tmw.co.uk/2014/01/speedtesting-gulp-and-grunt/) sur les tâches complexes. Si ce sujet vous intéresse, voici [un article](http://www.hongkiat.com/blog/gulp-vs-grunt/) qui traite de ce sujet en profondeur.

Tout comme Grunt, Gulp permet de définir des tâches, de les chaîner dans des workflows et de les exécuter. Gulp dispose de nombreux modules qui permettent de l'interfacer avec tous les outils modernes pour la création d'applications JS/HTML.

Gulp permet notamment de compiler les fichiers Coffeescript/Less/SASS et les templates à la volée, de minifier les fichiers CSS et JS, de packager une distribution ``production-ready`` du projet, d'exécuter les tests, de valider le code Javascript avec JSLint, etc, etc. 

La liste des plugins se trouve ici : <http://gulpjs.com/plugins/>

Autre fonctionnalité très intéressante, Gulp permet d'excuter le projet directement dans un serveur NodeJS embarqué avec un système de watchers sur les fichiers du projet, ce qui permet un développement continu très confortable.

Les tâches Gulp sont définies dans le fichier [gulpfile.js](https://github.com/Mnemotix/Marionette-tutorial/blob/step1/gulpfile.babel.js).

### Les commandes de base

Exécution de la tâche "default"

	gulp
	
Lister les tâches disponibles

	gulp --tasks
	
Lancer le serveur local de ****dévleoppement**** sur le port 9000

	gulp serve
	
Lancer les tests dans le navigateur
	
	gulp serve:test

Packager le projet dans sa version "production-ready"
	
	gulp build

Prévisualiser l'application en mode "production-ready"

	gulp serve:dist
	
Ajouter un plugin gulp avec NPM

	npm install gulp-coffee
	
Step 3 - Bower
--------------
### Présentation
Bower est un gestionnaire de dépendances.

 Il donne accès très simplement à un très grand nombre de librairies Javascript, de frameworks JS/CSS/Web Fonts.
 
 Chaque module Bower doit présenter un fichier ``bower.json`` qui liste ses dépendances internes. Grâce à ce fichier, Bower sait résoudre l'abre de dépendances en entier. Il peut néanmoins y avoir quelques problèmes de compatibilité entre les versions des dépendances. Dans ce cas, ce sera à vous de spécifier quelle version vous voulez vour apparaître dans votre projet.
 
 Bower se présente sous la forme d'une ligne de commande qui permet d'interagir avec le repository local de dépendance ou bien directement avec des repository distants, notamment Github. 
 
 Les dépendances Bower se présentent toujours sous la forme :  
``<package>#<version>``

Bower organise les dépendances du projet dans un fichier [bower.json](https://github.com/Mnemotix/Marionette-tutorial/blob/step1/bower.json) qui se trouve à la racine du projet. Nous voyons que dans ce fichier les dépendances de développement dites ``devDependencies`` sont traitées séparément des autres. Les ``devDependencies`` ne seront tout simplement pas ajoutées dans la version packagée du projet, résultante de la commande ``gulp build``

### Les commandes de base
Chercher une dépendance

	bower search jquery*

Voir les infos d'une dépendance

	bower info jquery

Voir les infos d'une version en particulier

	bower info jquery#2.1.4

Lister les dépendances

	bower list
	
Installer une dépendance dans sa dernière version

	bower install jquery

Installer une dépendance dans une version spécifique

	bower install jquery#2.1.4

Installer une dépendance et l'ajouter au fichier ``bower.json`` du projet

	bower install jquery#2.1.4 --save

Installer une dépendance et l'ajouter en tant que dépendance de développement dans le fichier ``bower.json``. Par définition, les dépendances de développement ne seront pas déployées dans la distribution finale dédiée à la production. Cette fonctionnalité est intéressante notamment pour les dépendances liées aux tests, par exemple mocha.

	bower install mocha --save-dev
	
Mettre à jour une dépendance

	bower update jquery
	
Supprimer une dépendance

	bower uninstall chai

Les dépendances Bower sont installées par défaut dans le répertoire ``bower_components`` et seront référencées dans le fichier ``bower.json`` si l'option ``--save``est utilisée lors de l'installation.

	bower install jquery --save
	

Step 4 - Backbone
-----------------
### Présentation
---
[BackboneJS](http://backbonejs.org/) est un framework Javascript destiné à structurer et à faciliter le développement de Single Page Application (SPA).

Il propose un ensemble de fonctions utilitaires qui le rendent particulièrement intéressant pour les interactions avec des API de type REST.

### Installation
---
Première chose à faire, installer Backbone dans notre application avec les outils fournis par Yeoman.

	bower search backbone
	bower info backbone

Le résultat de la dernière commande devrait comporter une section ressamblante à ça :

```
{
  name: 'backbone',
  version: '1.2.1',
  main: 'backbone.js',
  dependencies: {
    underscore: '>=1.7.0'
  },
  ignore: [...],
  homepage: 'https://github.com/jashkenas/backbone'
}
    'docs',
```

On voit ici que Backbone est en version 1.2.1 par défaut et qu'elle dépend d'une autre librairie ``underscore: '>=1.7.0'``. Bower devrait donc nous installer tout ça automatiquement.

	bower install backbone --save
	cat bower.json
	
On voit que Bower a effectivement ajouté Backbone à la liste des dépendances du projet.

```
{
  "name": "marionette",
  "private": true,
  "dependencies": {
    "bootstrap-sass": "~3.3.1",
    "modernizr": "~2.8.1",
    "backbone": "~1.2.1"
  },
  "devDependencies": {
    "chai": "~3.0.0",
    "mocha": "~2.2.5"
  }
}
```
Un coup oeil au répertoire des dépendances

	ls -l bower_components/
	
```
drwxr-xr-x   8 nico  staff   272B Jun 18 13:44 backbone/
drwxr-xr-x  12 nico  staff   408B Jun 18 12:59 bootstrap-sass/
drwxr-xr-x  13 nico  staff   442B Jun 18 12:59 chai/
drwxr-xr-x   7 nico  staff   238B Jun 18 12:59 jquery/
drwxr-xr-x  14 nico  staff   476B Jun 18 12:59 mocha/
drwxr-xr-x  12 nico  staff   408B Jun 18 12:59 modernizr/
drwxr-xr-x   9 nico  staff   306B Jun 18 13:44 underscore/
```
Underscore a bien été téléchargé. Lançons l'application pour voir si nos dépendances ont bien été ajoutées automatiquement : 

	gulp serve
	open http://localhost:9000
	
En inspectant le code source de la page : 

![no-deps](http://puu.sh/itrrF/250582b31d.png =600x)

On voit que les dépendances Bootstrap et Jquery ont été ajoutées, mais pas de trace de Backbone ni de Underscore...

Pas de panique __c'est normal__!

La liaison des dépendances se fait automatiquement dans Gulp seulement sil
 le serveur est actif (après un `gulp serve`). Sinon il faut dire à Gulp de lier les dépendances manuellement :

	gulp wiredep
	gulp serve
	open http://localhost:9000

![with-deps](http://puu.sh/itrss/c31557bcda.png =600x)

C'est beaucoup mieux ! Ce n'est pas magique mais c'est quand même sympa non ?   
OK mais comment ça marche ?

Jetons un coup d'oeil au fichier `app/index.html`

```
<!doctype html>
<html class="no-js" lang="">
  <head>
    <meta charset="utf-8">
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>marionette</title>

    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    <!-- Place favicon.ico in the root directory -->

    <!-- build:css styles/vendor.css -->
    <!-- bower:css -->
    <!-- endbower -->
    <!-- endbuild -->

    <!-- build:css styles/main.css -->
    <link rel="stylesheet" href="styles/main.css">
    <!-- endbuild -->
    
    <!-- build:js scripts/vendor/modernizr.js -->
    <script src="/bower_components/modernizr/modernizr.js"></script>
    <!-- endbuild -->
  </head>
  <body>
  	[...HTML...]
   
    <!-- Google Analytics: change UA-XXXXX-X to be your site's ID. -->
    [...Google Analytics...]

    <!-- build:js scripts/plugins.js -->
    [...Dépendances Bootstrap...]
    <!-- endbuild -->

    <!-- build:js scripts/vendor.js -->
    <!-- bower:js -->
    <script src="/bower_components/jquery/dist/jquery.js"></script>
    <script src="/bower_components/underscore/underscore.js"></script>
    <script src="/bower_components/backbone/backbone.js"></script>
    <!-- endbower -->
    <!-- endbuild -->
  </body>
</html>

```
On voit dans le fichier qu'il y a des commentaires un peu particuliers : 

    <!-- build:css styles/vendor.css -->
    <!-- bower:css -->
    <!-- endbower -->
    <!-- endbuild -->

et 

    <!-- build:js scripts/vendor.js -->
    <!-- bower:js -->
    <!-- endbower -->
    <!-- endbuild -->

Ces commentaires sont en réalité des balises pour le module [wiredep](https://www.npmjs.com/package/wiredep) qui viendra automatiquement ajouter les modules/styles dits "vendors" à cet endroit là précisément.

>__IL EST DONC TRES IMPORTANT DE NE PAS SUPPRIMER CES COMMENTAIRES !!__


### Premiers pas avec Backbone
---

Commençons par faire un peu de ménage dans notre page d'accueil : 
