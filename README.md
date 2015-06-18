# Marionette-tutorial
![MNX icon](http://mnemotix.com/v2/assets/images/logo.svg)

## Overview
L'objectif de ce tutoriel est d'apprendre à créer une simple application Backbone/Marionette en utilisant des outils de productivité tels que Yeoman/Gulp.

### Installation

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
	

### Application

#### Initialisation

	mkdir my-webapp
	cd my-webapp
	yo gulp-webapp
	
#### Apprendre à utiliser Gulp

##### Les commandes de base

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

#### Apprendre à utiliser Bower

##### Les commandes de base
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