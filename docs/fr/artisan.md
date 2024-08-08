# Commandes artisanales utiles

Agorakit fournit quelques commandes [artisan](https://laravel.com/docs/7.x/artisan) utiles :

- `agorakit:checkmailbox` Vérifier le serveur email imap configuré pour permettre la fonctionnalité de postage par email
- `agorakit:cleanupdatabase` Nettoie la base de données, supprime pour toujours les modèles supprimés et les utilisateurs non vérifiés de plus de 30 jours.
- `agorakit:convertfiles` Convertit les fichiers de l'ancien stockage basé sur le chemin plat vers le nouveau stockage, en remettant leur nom de fichier initial et en déplaçant le fichier vers le répertoire public. Utilisez ceci **une fois** si vous avez déjà des fichiers sur votre installation et si votre installation est antérieure à novembre 2016.
- `agorakit:convertfolderstotags` Convertit tous les dossiers au nouveau système basé sur les tags. Ajouter les tags représentant le dossier parent à chaque fichier.
- `agorakit:deletefiles` Supprime les fichiers du stockage après 30 jours de suppression dans la base de données.
- `agorakit:export` Exporter un groupe vers un fichier zip (travail en cours)
- `agorakit:import` Importer un groupe depuis un fichier zip d'exportation Agorakit (travail en cours)
- `agorakit:populatefilesize` Fixe la taille des fichiers dans la table des fichiers en utilisant la taille réelle du système de fichiers. A utiliser si vous avez installé Agorakit avant novembre 2017.
- `agorakit:sendnotifications` Envoie toutes les notifications en attente à tous les utilisateurs qui l'ont demandé. Cela peut prendre du temps. Appelez ceci fréquemment pour éviter les problèmes
- `agorakit:sendreminders` Envoie tous les rappels aux participants qui l'ont demandé - appeler exactement toutes les 5 minutes, ni plus, ni moins :-)

ATTENTION : La plupart de ces commandes sont déjà utilisées par le job cron, elles n'ont donc pas besoin d'être appelées manuellement. Mais elles peuvent être utiles pour le débogage et le développement.
