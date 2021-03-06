## Le Plugin Kee pour le navigateur Firefox

KeePass2 n'est pas intégrer au navigateur web mais il est intégrable. Je traîte ici le cas de Firefox.

# 1. KeePass2 aussi flexible que les outils de mots de passe Firefox

Kee est disponible sur le site https://www.kee.pm/ avec quelque tutoriel sur la page https://tutorial-addon.kee.pm/.
Kee permet à Firefox de communiquer avec KeePass2 pour vous éviter de devoir taper les mots de passe.

Kee repère les champs à remplir avec le nom d'utilisateur et le mot de passe. L'icône de Kee apparaît alor dans le champs et en cliquant dessus vous pourrez choisir parmi une liste d'entrées filtrées avec laquelle il faut remplir le champs.

Kee peut aussi prendre plus de type de champs si nécessaire pour l'identification (code postal, date de naissance ...) mais il faudrait l'aider à les configurer, nous verrons comment.

# 2. Installation et liaison Firefox

Quelque soit l'OS, vous devez télécharger le plugin KeePassRPC.plgx à la page https://github.com/kee-org/keepassrpc/releases/ 

Il faut ensuite déplacer le plugin KeePassRPC.plgx dans le répertoire Plugins dans le répertoire d'installation.

Sur Firefox vous devez installer l'addon Kee qui se trouve ici : https://addons.mozilla.org/fr/firefox/addon/keefox/

La base de donnée qui contient vos mots de passe doit être ouverte sur le logiciel KeePass pour que Firefox puisse vous proposez de remplir les champs.

# 3. En pratique

Lorsque la base de données est ouverte dans KeePass2, Firefox demande à la base de données via le plugin si l'adresse URL de la page consultée est en adhéquation avec une adresse URL dans celle-ci. 

Si une seule adresse correspond, Kee remplira automatiquement les champs du formulaire de connection au site. 
Si plusieurs adresses correspondent, l'icône de Kee apparaîtra dans les champs à remplir et vous pourrez choisir l'entrée de votre choix parmis celles qui correspondent en cliquant dessus.

Kee vous indiquera dés lors qu'il y a des champs à remplir sur le site si des entrées correspondent à l'adresse URL dans l'option "Entrée correspondantes" du menu de Kee (accessible en cliquant sur le bouton Kee dans la barre Firefox ou par clic-droit). Depuis ce menu vous pourrez copier le nom d'utilisateur ou le mot de passe en cliquant sur le menu à trois traits à côté de l'entrée pertinente.

# 4. Avantages, inconvéniants

Le plugin KeePassRPC permet une connection chiffrée entre KeePass et d'autres applications (Firefox via Kee). Ainsi un logiciel tier (malveillant) ne peut pas écouter ce qu'échange KeePass et l'application.

Lorsque KeePass ouvre une base de donnée, il faut la conserver en mémoire, mais KeePass chiffre certains champs dans la mémoire (mot de passe notamment, et champs additionnels pour lesquels l'option est activée dans le menu Avancé de l'entrée). Un logiciel malveillant générique copiant la mémoire vive ne peut pas en lire le contenu.

Kee vous permet ainsi de faire transiter le mot de passe dans Firefox depuis un conteneur chiffré (la base de données KeePass ouverte mais chiffré en mémoire vive) via un canal de communication chiffré lui aussi (grâce à KeePassRPC). Ainsi, sous réserve que Firefox n'est pas corrumpu, toutes les étapes de saisie du mot de passe se font de manière sécurisée.

Avertissement : Une telle fonctionnalité est assurément pratique mais introduit une faille, un plugin firefox malveillant spécifiquement créé pour peut recupérer les mots de passe transmit par KeePassRPC. De manière générale, un logiciel malveillant spécifiquement créé pour compromettre KeePass y parviendra toujours dés lors qu'il est installé sur votre ordinateur.


# 5. Changer ses mots de passe pour des mots de passe aléatoires

Dans Kee, il suffira de cliquer sur l'option "Générer un nouveau mot de passe" (ou par clic-droit et Kee dans le menu contextuel) et choisir le profil de mot de passe désiré pour que le mot de passe soit enregistré dans le presse papier.

En pratique :
   * Une fois connecté au compte sur le site, on demande le changement du mot de passe
   * Dans les champs "retaper votre mot de passe actuel", utiliser Kee pour saisir le mot de passe actuel. Il est possible que Kee reconnaisse mal le champ (qui peut être identifié différemment pour la page de changement de mot de passe), dans ce cas copier depuis Kee le mot de passe en cliquant sur "Entrées correspondantes" dans le menu Kee puis copier le mot de passe de l'entrée pertinente en cliquant sur le bouton dans le menu à trois bar à côté de cette entrée.
   * Cliquer sur "Générer un nouveau mot de passe" dans Kee, cliquer sur le profil de mot de passe desiré.
   * Puis coller (Ctrl + V) dans tous les champs demandant le nouveau mot de passe et sa confirmation
   * Une fois que le site valide votre changement de mot de passe, déconnectez vous du compte.
   * Reconnectez vous sur votre compte par la procédure normale en collant une nouvelle fois le nouveau mot de passe (toujours dans le presse-papier).
   * Cliquez sur "Sauvegarder le dernier identfiant" puis "modifier une entrée existante" et on clique sur l'entrée qui contenait le mot de passe. On clique sur "Mettre à jour".
   * Vous avez donc changé votre mot de passe sur le site et dans la base de donnée KeePass ! (vous pouvez reprendre une navigation normale sans vous souciez du contenu du presse-papier)

# 6. J'ai oublié de mettre à jour la base de donnée et le mdp généré n'est plus dans le presse papier, que faire ?

Pas de panique, votre mot de passe n'est pas perdu ! Kee génère toujours un souvenir du mot de passe généré aléatoirement par la procédure précédente !

Il suffit de chercher dans le dossier "Kee Generated Password Backup" une entrée dont l'URL est celle du site en question et qui est la dernière modifiée ! Elle contiendra cette URL et uniquement le mot de passe généré ! (Aucune possibilité d'embrouille sur ce coup là, mais cette entrée est incomplète car il manque le login)

Vous pourrez donc modifier manuellement depuis KeePass l'entrée utilisée par Kee pour vous connecter au dit site pour y mettre le bon mot de passe et login. Vous devriez pouvoir vous reconnecter normalement avec Kee.

Remarque : lorsque vous êtes sur que les entrées que vous utilisez contiennent bien les mots de passe à jour et vous permettent une connection normale, vous pouvez bien sur supprimer les entrées créées par Kee pour sauvegarder les mots de passe générés bien sûr.
