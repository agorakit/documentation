# Installation

NOTE : **Essayer Agorakit sans l'installer**
    Si vous souhaitez simplement essayer Agorakit, vous pouvez le faire sans avoir à l'installer. Il suffit de créer un compte sur <https://app.agorakit.org>, une instance d'Agorakit pour les citoyens-activistes et à des fins d'évaluation.

    Vous pouvez également contacter le développeur si vous êtes intéressé par l'hébergement géré d'une instance privée d'Agorakit. Contactez info [at] agorakit.org pour plus de détails.

    Continuez à lire si vous souhaitez installer une instance d'Agorakit sur votre propre serveur.

## Exigences

Vous avez besoin d'un bon fournisseur d'hébergement web qui fournit les éléments suivants :

- php >= 8 avec les extensions habituelles
- Mysql ou MariaDb ou SQlite
- Composer
- Git
- la possibilité d'exécuter des tâches cron
- accès ssh

NOTE : Toutes ces fonctionnalités réunies sont difficiles à trouver, c'est pourquoi les gens sont obligés d'utiliser un VPS et de tout configurer eux-mêmes. C'est une proposition plus risquée si vous ne savez pas comment cela fonctionne. Nous avons eu beaucoup de succès avec l'hébergement partagé [Alwaysdata] (https://www.alwaysdata.com). Ils hébergent d'ailleurs à un tarif réduit [l'instance gratuite d'Agorakit](https://app.agorakit.org).


## Installer

Actuellement, vous devez savoir comment installer une application Laravel en utilisant la ligne de commande.
Ceci est parfaitement standard et documenté ici : https://laravel.com/docs/master/installation.

### Cloner le dépôt

    git clone https://github.com/agorakit/agorakit

Cela créera un répertoire `agorakit` dans le chemin courant.

### Créer le fichier .env
Tous les paramètres sont stockés dans un fichier .env. Ce fichier n'est pas fourni dans le dépôt Git, parce qu'il est spécifique à votre installation, et parce que vous ne voulez pas que votre configuration soit écrasée lors d'une mise à jour :-)

Créez et éditez le fichier de configuration à partir du fichier d'exemple fourni :


    cp .env.example .env
    nano .env

Nano est un simple éditeur de texte disponible sur la plupart des serveurs. N'hésitez pas à utiliser autre chose pour éditer votre fichier .env.

### Configurer les informations d'identification de la base de données

NOTE : Vous devez au moins définir les identifiants de votre base de données et le nom de votre site. Vérifiez que votre base de données existe et qu'elle est accessible avec ces identifiants.

```
APP_ENV=local // local ou production
APP_DEBUG=true // affiche ou non la barre de débogage et les erreurs étendues
APP_KEY=SomeRandomString // sera généré automatiquement
APP_NAME='Agorakit' // nom de votre application
APP_URL=http://locahost // url de base
APP_LOG=daily // rotation du journal
APP_DEFAULT_LOCALE=en // locale par défaut si elle n'est pas détectée par le navigateur de l'utilisateur

DB_HOST=localhost // hôte de votre serveur mysql
DB_DATABASE=agorakit // nom de votre base de données SQL
DB_USERNAME=root // login de mysql
DB_PASSWORD= // mot de passe de mysql

CACHE_DRIVER=file // driver à utiliser pour la mise en cache
SESSION_DRIVER=file // pilote à utiliser pour stocker les sessions
QUEUE_DRIVER=sync // pilote à utiliser pour les files d'attente
```

### Configurer l'envoi d'emails

Vous pouvez maintenant configurer votre serveur de messagerie. Pour le pilote de messagerie, vous pouvez utiliser `mail` pour utiliser la fonction de messagerie intégrée de php ou `smtp` pour utiliser n'importe quel serveur smtp. Choisissez le bon port (sur la plupart des serveurs, il s'agit de 25), l'hôte et le nom d'utilisateur / mot de passe.

```
MAIL_DRIVER=mail // pilote à utiliser pour envoyer des emails. Utilisez mail pour utiliser la fonction mail intégrée de php
MAIL_HOST=mailtrap.io // nom d'hôte si vous utilisez smtp pour envoyer des mails
MAIL_PORT=2525 // port si vous utilisez smtp pour envoyer des mails
MAIL_USERNAME=null // login si vous utilisez smtp pour envoyer des mails
MAIL_PASSWORD=null // mot de passe si vous utilisez smtp pour envoyer des mails
MAIL_ENCRYPTION=null // cryptage si vous utilisez smtp pour envoyer des mails

MAIL_FROM=admin@localhost // adresse email utilisée pour l'envoi d'emails d'administration
MAIL_FROM_NAME=Agorakit // nom de l'expéditeur des emails d'administration
MAIL_NOREPLY=noreply@localhost // pas d'adresse de réponse pour les messages de service

MAPBOX_TOKEN=null // Créer un compte Mapbox et générer un jeton pour permettre la géolocalisation et l'affichage des cartes.
```

ASTUCE : Vous devez disposer d'un serveur de courrier électronique opérationnel pour pouvoir vérifier tout compte utilisateur enregistré. Si vous ne pouvez pas vérifier votre compte utilisateur, vous pouvez toujours mettre la colonne `verified` à `1` dans la table `users`.


### Installer les paquets

Téléchargez tous les paquets nécessaires :

```
composer install
```



### Générer une clé

```
php artisan key:generate
```

Cette étape est très importante car la clé est utilisée pour générer différents tokens et sessions.


### Créer les tables dans la base de données

Migrer (créer toutes les tables dans) la base de données :

```
php artisan migrate
```

### Stockage des fichiers de liens

Lier le dossier public de stockage au dossier public visible par l'utilisateur :

```
php artisan storage:link
```

### Créer un contenu factice

(Facultatif) Créer un exemple de contenu dans la base de données :

```
php artisan db:seed
```

! !! avertissement
    Ne faites pas cette dernière étape pour une installation en production car elle créera un utilisateur admin avec un mot de passe par défaut et des groupes et contenus factices.


## Configurez votre serveur web

Vous pouvez maintenant configurer votre serveur web pour qu'il serve le répertoire `/public`. Ceci est très important, car vous ne voulez pas exposer le reste des répertoires (par exemple, vous ne voulez PAS exposer votre fichier .env !).


## Configurer un job cron

Une tâche cron est une tâche que votre serveur exécute à des intervalles spécifiques pour exécuter des choses en arrière-plan.

Agorakit a besoin d'effectuer périodiquement certaines tâches, comme l'envoi de résumés par email, le nettoyage de la base de données, la suppression d'anciennes versions du contenu, la suppression d'anciens fichiers, etc...

Le script `php artisan schedule:run` doit être exécuté au moins toutes les 5 minutes en utilisant une tâche cron.

Suivez la documentation de Laravel cron ici : https://laravel.com/docs/master/scheduling


NOTE : Sans job cron, votre application n'enverra **PAS** de résumés, ne nettoiera pas la base de données, ne rappellera pas aux utilisateurs les événements à venir, etc. Les jobs cron sont nécessaires pour une exploitation correcte.

