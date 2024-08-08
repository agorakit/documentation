# Contribuer à Agorakit

Vous voulez contribuer au projet ? C'est très bien ! Toute idée est la bienvenue.

- Veuillez d'abord discuter du bogue ou de la demande de fonctionnalité dans la file d'attente des problèmes.
- Vérifiez la licence (AGPL) pour voir si elle correspond à votre modèle de contribution.
- Suivez les meilleures pratiques de Laravel
- Nous utilisons Unpoly js pour les fonctionnalités de type spa, lisez un peu à son sujet car il n'est pas aussi populaire que les autres options (pensez-y comme des turbolinks sur les stéroïdes).
- Nous utilisons Bootstrap aromatisé par tabler.io


# Serveur de développement

## Utilisation de Laravel Sail
Sail est un wrapper docker pour faciliter le développement local. C'est un moyen vraiment cool et facile d'avoir un serveur local parfait pour les développeurs.
Laravel Sail fonctionne d'emblée dans ce projet. Lisez la documentation de Sail pour plus d'informations.

C'est ce que j'utilise sur ma station de travail principale (basée sur linux) car c'est très reproductible.

En gros, `sail up` va démarrer un serveur de développement


## Utilisation de artisan serve

Si vous voulez démarrer un serveur local pour le développement :

    $ php artisan serve

L'installation sera disponible pour 127.0.0.1:8000

Il y a beaucoup d'autres options, consultez la documentation et l'écosystème de Laravel pour avoir une vue d'ensemble des options pour le développement local.

# Création de la base de données
Suivez d'abord les instructions d'installation, y compris la création d'un échantillon de contenu en utilisant :

    $ php artisan db:seed


# Travailler sur le design et les css

J'ai supprimé toutes les étapes de construction, maintenant tout se passe dans un fichier custom.css plat.

Tous les JS et CSS externes sont servis par différents CDN. A un moment donné, les fichiers seront re-servis en local, quand tout sera stabilisé, et s'il y a de réels avantages à le faire.

Pas de npm, pas de node, pas de tailwind, pas de purge, pas de minifier, pas de problème :)


# Tester votre code

Agorakit est testé en utilisant le framework de test Laravel.

Pour tester, vous devez avoir une base de données de test existante. Il suffit de créer une nouvelle base de données vide, par exemple agorakit_testing et de vérifier dans le fichier phpunit.xml que tout correspond.

Avant de commencer le code, vous devriez soit écrire plus de tests (dans ce cas, vous méritez un cookie). Ou au moins vérifier que vous n'avez rien cassé en tapant simplement: :

    php artisan test

...à la racine de votre projet.

Aucune erreur ne devrait apparaître (à condition que tout soit correctement configuré).

Nous utilisons travis ci pour exécuter tous ces tests lors du commit, donc cela sera fait automatiquement pour vous à un moment donné :-)

# Ecriture des tests

N'hésitez pas à écrire des tests. Nous privilégions les tâches bien définies qu'un utilisateur final accomplirait réellement, comme l'inscription, la création d'un compte, la publication, le téléchargement, etc... Cela nous a très bien servi dans le passé pour repérer les erreurs et cela reflète vraiment les cas d'utilisation réels. Bien que nous soyons ouverts à d'autres types de tests...
