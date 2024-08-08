# Mise à jour d'Agorakit
Il est important de maintenir une installation d'Agorakit à jour. Le processus est sûr

Nous essayons de garder la branche master toujours dans un bon état de fonctionnement (c'est ce qu'on appelle un modèle de "rolling release").

Cela signifie que les tests sont réussis et que vous obtenez les dernières fonctionnalités directement à partir de la branche master.

ATTENTION : Faites une sauvegarde de votre base de données SQL au cas où quelque chose tournerait mal. Faites également une sauvegarde de tous vos fichiers. Faites même deux sauvegardes et stockez-les sur un serveur séparé.


INFO : Vous pouvez choisir entre une procédure de mise à jour automatisée à partir de la ligne de commande, ou une procédure de mise à jour manuelle étape par étape.

## Option 1 : Utilisation du script de mise à jour
Il existe un script d'aide qui effectue la mise à jour pour vous :

```
./update
```

! !! avertissement
    Attention, le script migrera votre base de données sans vous demander confirmation. Faites toujours une sauvegarde de la base de données au cas où quelque chose se passerait mal.


## Option 2 : Procéder à la mise à jour manuellement
Vous pouvez à tout moment procéder à la mise à jour de votre installation :

```
php artisan down
git pull
composer install
php artisan migrate
php artisan up
```


# Si quelque chose ne va pas
Restaurez la sauvegarde de votre base de données et faites un git checkout d'une version précédente (fonctionnelle). Puis réexécutez composer install.

Contactez-nous si une mise à jour échoue (cela n'est jamais arrivé, donc ce genre d'échec est une information très intéressante pour le projet).

# Instructions spécifiques à la version
## Mise à jour vers la version 1.5
Après la mise à jour normale, il se peut que vous obteniez une erreur mentionnant la duplication de la clé du nom d'utilisateur dans la table des utilisateurs.

Exécutez `php artisan agorakit:enforceuniqueusernames` pour corriger le problème.
Puis réexécutez le script de mise à jour.

Ceci n'arrive que sur les grosses installations et peut être exécuté plusieurs fois sans problème. C'est une solution à l'épreuve du temps pour ce problème.

! !! note
    La plupart des mises à jour ponctuelles comme celle mentionnée ci-dessus sont maintenant effectuées dans le cadre de migrations afin de réduire la quantité de documentation que vous devez lire pour mettre à jour correctement votre installation. Asseyez-vous, détendez-vous et appréciez l'automatisation au travail :-)
