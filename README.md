# Marionette-tutorial
![MNX icon](http://mnemotix.com/v2/assets/images/logo.svg)

## Overview
L'objectif de ce tutoriel est d'apprendre à créer une simple application Backbone/Marionette en utilisant des outils de productivité tels que Yeoman/Gulp.

### Step 1 - Installation

#### Git

	brew install git
	
#### NodeJS
	
	brew install node
	node --version && npm --version
	npm install --global npm@latest
	
#### Yeoman

	npm install --global yo bower grunt-cli
	yo --version && bower --version && grunt --version
	
#### Installer le générateur Yeoman

	npm install --global generator-gulp-webapp
	

#### Générer le squelette de l'application

	mkdir my-webapp
	cd my-webapp
	yo gulp-webapp

### Step 2 - Gulp

#### Présentation
[Gulp](http://gulpjs.com/) est un gestionnaire de build pour les projets Javascript.

C'est un équivalent Javascript de Ant/Maven en Java. Gulp est le successeur direct d'un autre outil de build JS très connu : [Grunt](http://gruntjs.com/). La différence principale entre les deux se résume à la manière dont les tâches vont être résolues en interne. [Gulp est plus performant](http://tech.tmw.co.uk/2014/01/speedtesting-gulp-and-grunt/) sur les tâches complexes. Si ce sujet vous intéresse, voici [un article](http://www.hongkiat.com/blog/gulp-vs-grunt/) qui traite de ce sujet en profondeur.

Tout comme Grunt, Gulp permet de définir des tâches, de les chaîner dans des workflows et de les exécuter. Gulp dispose de nombreux modules qui permettent de l'interfacer avec tous les outils modernes pour la création d'applications JS/HTML.

Gulp permet notamment de compiler les fichiers Coffeescript/Less/SASS et les templates à la volée, de minifier les fichiers CSS et JS, de packager une distribution ``production-ready`` du projet, d'exécuter les tests, de valider le code Javascript avec JSLint, etc, etc. 

La liste des plugins se trouve ici : <http://gulpjs.com/plugins/>

Autre fonctionnalité très intéressante, Gulp permet d'excuter le projet directement dans un serveur NodeJS embarqué avec un système de watchers sur les fichiers du projet, ce qui permet un développement continu très confortable.

#### Les commandes de base

Exécution de la tâche "default"

	gulp
	
Lister les tâches disponibles

	gulp --tasks
	
Lancer le serveur local de ****dévleoppement**** sur le port 9000

	gulp serve
	
Lancer les tests dans le navigateur
	
	gulp serve:test

Prévisualiser l'application en mode "production-ready"

	gulp serve:dist

### Step 3 - Bower

#### Présentation
Bower est un gestionnaire de dépendances.

 Il donne accès très simplement à un très grand nombre de librairies Javascript, de frameworks JS/CSS/Web Fonts.
 
 Chaque module Bower doit présenter un fichier ``package.json`` qui liste ses dépendances internes. Grâce à ce fichier, Bower sait résoudre l'abre de dépendances en entier. Il peut néanmoins y avoir quelques problèmes de compatibilité entre les versions des dépendances. Dans ce cas, ce sera à vous de spécifier quelle version vous voulez vour apparaître dans votre projet.
 
 Bower se présente sous la forme d'une ligne de commande qui permet d'interagir avec le repository local de dépendance ou bien directement avec des repository distants, notamment Github. 
 
 Les dépendances Bower se présentent toujours sous la forme :  
``<package>#<version>``

#### Les commandes de base
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

	
Supprimer une dépendance

	bower

Les dépendances Bower sont installées par défaut dans le répertoire ``bower_components`` et seront référencées dans le fichier ``bower.json`` si l'option ``--save``est utilisée lors de l'installation.

	bower install jquery --save