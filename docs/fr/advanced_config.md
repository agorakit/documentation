## Configurer les courriels entrants

Cette étape supplémentaire vous permet d'avoir une boîte aux lettres pour chaque groupe afin que les membres puissent envoyer des messages par courriel pour créer des discussions et répondre aux courriels des discussions pour créer de nouveaux commentaires.

! !! note
    Le support des emails entrants est expérimental mais utilisé sur plusieurs instances. Il est possible que vous rencontriez des bogues, veuillez les signaler si cela se produit dans votre installation.


- Vous avez besoin d'une adresse email sur un serveur supportant l'imap. Il doit s'agir d'une adresse "catch all" sur un sous-domaine (ou même sur un domaine) ou d'un serveur supportant l'adressage "+" (gmail par exemple le permet).
- Vous avez besoin de l'extension php imap
- La configuration se fait dans votre .env

Disons que vous avez installé Agorakit sur agora.example.org :

- Créer une boîte aux lettres catchall sur * .@agora.example.org
- Editez votre fichier .env et ajoutez/définissez les paramètres suivants :

```
# Paramètres du serveur de la boîte aux lettres, à utiliser pour les courriels entrants.
# Définissez INBOX_DRIVER à null pour désactiver cette fonctionnalité
INBOX_DRIVER=imap
INBOX_HOST=votremailhost.tld
INBOX_USERNAME=nom d'utilisateur de la boîte aux lettres
INBOX_PASSWORD=mot de passe de la boîte aux lettres
INBOX_PREFIX=
INBOX_SUFFIX=@agora.example.org

```


### Définir les préfixes et les suffixes
Vous devez renseigner le préfixe et le suffixe. Il y a deux cas de figure :


- Pour un catch all, il n'y a pas de préfixe. Le suffixe dans l'exemple ci-dessus serait `@agora.example.org` . Cela créera des courriels comme `group-slug@agora.example.com`

- En revanche, si vous utilisez l'adresse "+" (une boîte gmail par exemple, appelons-la agorakit@gmail.com),

    - le préfixe sera `agorakit+`
    - le suffixe sera `@gmail.com`.

    Cela créera des emails comme `agorakit+group-slug@gmail.com`

Si vous activez les emails entrants, la boîte aux lettres sera automatiquement vérifiée et les emails traités seront placés dans un dossier "processed" sous INBOX. Les courriels échoués seront également placés dans un dossier "failed" sous INBOX pour inspection.


## Authentification externe

! !! info
    L'authentification externe a été supprimée. Je n'ai que très peu (voire pas du tout) de personnes qui l'ont demandée. Il s'agit d'une fonctionnalité qui porte atteinte à la vie privée, c'est pourquoi aucun développement n'a été fait dans ce sens. N'hésitez pas à soumettre un PR si vous le souhaitez.


