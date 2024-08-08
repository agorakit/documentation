# Contribuer à la documentation

La documentation est écrite en markdown et le site web est construit statiquement en utilisant [Mkdocs material](https://squidfunk.github.io/mkdocs-material/)

NOTE : Nouveaux langages, meilleure formulation, nouvelles sections, plus de visuels, toutes les corrections même petites sont les bienvenues !

## Comment contribuer ?
- Créer un compte Github
- Créer un dépôt Agorakit (Fork)
- Editez les fichiers de documentation dans le répertoire /docs/.
- Créez une pull request pour demander à ce que vos changements soient fusionnés

CONSEIL : L'utilisation de [Visual Studio Code] (https://code.visualstudio.com/) pour travailler sur du code et des fichiers markdown est une option raisonnablement simple. Vous disposez en outre d'une interface utilisateur intégrée pour l'intégration de git et de github, ce qui est intéressant pour les débutants.

## Comment construire la documentation ?
Installez mkdocs material et quelques plugins.


    pip install mkdocs-material
    pip install markdown-callouts
    pip install mkdocs-static-i18n


Démarrez ensuite le serveur web intégré pour prévisualiser votre travail sur la documentation.

    mkdocs serve


La documentation est actuellement servie par des pages github. Le processus de publication est localisé ici : https://github.com/agorakit/documentation/actions/workflows/ci.yml

Comment cela fonctionne-t-il ?
A chaque fois qu'un commit est fait sur la branche principale ou master, la documentation est construite en utilisant https://github.com/mhausenblas/mkdocs-deploy-gh-pages
(c'est une action git qui fait le travail pour nous)

Les fichiers résultants sont placés dans la branche GH du dépôt de documentation qui est ensuite sérialisée en utilisant la fonctionnalité "pages" de github.

C'est un peu difficile à configurer mais il semble qu'une fois que c'est fait, ça fonctionne.


Voir https://squidfunk.github.io/mkdocs-material/getting-started/ pour plus d'informations sur le fonctionnement du constructeur de documentation.



