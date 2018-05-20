## Le Plugin Kee pour le navigateur Firefox

KeePass2 n'est pas intégrer au navigateur web mais il est intégrable. Je traîte ici le cas de Firefox.

# 1. KeePass2 aussi flexible que les outils de mots de passe Firefox

Kee est disponible sur le site https://www.kee.pm/ avec quelque tutoriel sur la page https://tutorial-addon.kee.pm/.
Kee permet à Firefox de communiquer avec KeePass2 pour vous éviter de devoir taper les mots de passe.

# 2. Installation et liaison Firefox

Quelque soit l'OS, vous devez télécharger le plugin KeePassRPC.plgx à la page https://github.com/kee-org/keepassrpc/releases/ 

Il faut ensuite déplacer le plugin KeePassRPC.plgx dans le répertoire Plugins dans le répertoire d'installation.

Sur Firefox vous devez installer l'addon Kee qui se trouve ici : https://addons.mozilla.org/fr/firefox/addon/keefox/

La base de donnée qui contient vos mots de passe doit être ouverte sur le logiciel KeePass pour que Firefox puisse vous proposez de remplir les champs.

# 3. Pourquoi l'installer ?

Si vous désirez une sécurité maximale, vous ne devez pas avoir à copier-coller votre mot de passe car c'est une très grosse faille de sécurité :

Si le système est vérolé, le virus (cheval de Troie classique) peut enregistrer l'état de la mémoire dont le presse-papier (zone de mémoire où le contenu mis en attente de collage est en attente). Cela signifit que votre mot de passe est vu en clair par le virus tant que vous n'avez pas modifié le contenu du presse papier (cad fait un Copier) !! Bien sur KeePass2 est prévoyant et ne laisse le mot de passe que temporairement dans le presse-papier le temps de le copier (12 seconde par défaut), mais vous sentez bien que c'est une faille. 

Conclusion : si désirez un maximum de protection (c'est le cas, vous lisez ce tutoriel), interdiction de copier-coller !

Le plugin KeePassRPC permet une connection chiffrée entre KeePass et d'autres applications (Firefox via Kee). Ainsi un logiciel tier (malveillant) ne peut pas écouter ce qu'échange KeePass et l'application.

Remarque : Naturellement, lorsque KeePass ouvre une base de donnée, il faut la conserver en mémoire, mais KeePass chiffre certains champs dans la mémoire (mot de passe notamment, et champs additionnels pour lesquels l'option est activée dans le menu Avancé de l'entrée). Un logiciel malveillant générique copiant la mémoire vive ne peut pas en lire le contenu.

Avertissement : Une telle fonctionnalité est assurément pratique mais introduit une faille, un plugin firefox malveillant spécifiquement créé peut recupérer les mots de passe transmit par KeePassRPC. De manière général, un logiciel malveillant spécifiquement créé pour compromettre KeePass y parviendra toujours dés lors qu'il est installé sur votre ordinateur.

# 4. En pratique

Lorsque la base de données est ouverte dans KeePass2, Firefox demande à la base de données via le plugin si l'adresse URL de la page consultée est en adhéquation avec une adresse URL dans celle-ci. 

Si une seule adresse correspond, Kee remplira automatiquement les champs du formulaire de connection au site. 
Si plusieurs adresses correspondent, l'icône de Kee apparaîtra dans les champs à remplir et vous pourrez choisir l'entrée de votre choix parmis celles qui correspondent en cliquant dessus.

Kee vous indiquera dés lors qu'il y a des champs à remplir sur le site si des entrées correspondent à l'adresse URL dans l'option "Entrée correspondantes" du menu de Kee (accessible en cliquant sur le bouton Kee dans la barre Firefox ou par clic-droit). Depuis ce menu vous pourrez copier le nom d'utilisateur ou le mot de passe en cliquant sur le menu à trois traits à côté de l'entrée pertinente.

# 5. Changer ses mots de passe pour des mots de passe aléatoires

KeePass dispose d'un générateur de mots de passe aléatoires. Les mots de passe générés aléatoirement sont de TRÈS LOIN les PLUS FORTS, et pour cause le fait d'être généré de cette façon à pour conséquence que :

    * Même si par inadvertence ils s'afficheraient en clair temporairement (comme sur les smartphones par un copier-coller) une personne qui regarderait l'écran aurait une (très) grande difficulté à les lire et donc les mémoriser
    * Ils imposent aux potentiels hackeurs de vous attaquer par pure brute-force, aucune technique de dictionnaire ou social engeneering ne permet d'éventuellement gagner du temps. Celà à pour conséquence que :
    * Ils seront forcément les derniers mots de passe essayés par un éventuel hackeur tenace, ils sont donc les PLUS FORT DE TOUS. A ce niveau là, si vos mots de passe sont assez longs, ce n'est plus un individu qui attaque vos mots de passe mais une organisation (entreprise ou État...)
    * Ils évitent de tomber dans l'usage le plus déconseilé des mots de passe : la réutilisation. La réutilisation d'un mot de passe ou de variantes de celui-ci sur plusieurs sites rendent tous ces mots de passe faibles dés lors que deux sites sur lesquelles vous êtes inscrit ont vu leurs identifiants et mots de passe fuiter (on peut alors identifier les éléments communs à ses mots de passes et la façon de créer les variantes). Les mots de passe généré aléatoirement ne sont PAS REPRODUCTIBLES, chaque site à un mot de passe très différent, risque 0.
    * Vous vous dépendez en revanche de KeePass pour retrouver vos mots de passe (n'espérez pas retrouver de tête des mots de passe que vous n'avez pas choisi et que vous ne saisirez jamais). Il faudra donc créer dupliquer et synchroniser les fichiers de base de données cryptée pour disposer de sauvegardes accessible partout tant que vos mots de passe sont générés ainsi (remarquez que c'est peut être déjà le cas alors que vos mots de passe sont faibles...)
    
A vous de mesurer avantages et inconvenients. La réutilisation de mots de passe est en tout cas très fortement déconseillée comme le décrit : https://xkcd.com/792/

KeePass vous propose quelques profils de génération de mots de passe aléatoires mais il est bon de créer les vôtres. Pour celà, rendez vous dans le générateur de mots de passe dans KeePass (outils, générer un nouveau mot de passe).
Choisissez le nombre de charactères, les différents types (maj, min, chiffres, paranthèses, espace ....) et cliquer sur la disquette pour enregistrer en donnant un nom clair à ce profil de mot de passe.

Dans Kee, il suffira de cliquer sur l'option "Générer un nouveau mot de passe" (ou par clic-droit et Kee dans le menu contextuel) et choisir le profil de mot de passe désiré pour que le mot de passe soit enregistré dans le presse papier.

En pratique :
   * Une fois connecté au compte sur le site, on demande le changement du mot de passe
   * Kee ne parvient pas toujours à réécrire l'ancien mot de passe dans les champs "retaper votre mot de passe actuel". Il faut donc en général copier depuis Kee le mot de passe en cliquant sur "Entrées correspondantes" dans le menu Kee puis copier le mot de passe de l'entrée pertinente en cliquant sur le bouton dans le menu à trois bar à côté de cette entrée.
   * Cliquer sur "Générer un nouveau mot de passe" dans Kee, cliquer sur le profil de mot de passe desiré.
   * Puis coller (Ctrl + V) dans tous les champs demandant le nouveau mot de passe et sa confirmation
   * Une fois que le site valide votre changement de mot de passe, on clique sur "Sauvegarder le dernier identfiant" puis "modifier une entrée existante" et on clique sur l'entrée qui contenait le mot de passe. On clique sur "Mettre à jour".
   * Vous avez donc changé votre mot de passe sur le site et dans la base de donnée KeePass. Vérifiez cependant que KeePass a changé correctement les bons champs (par défaut le dernier champs remplit est le nouveau mot de passe mais certains sites demandent des captchas ce qui embrouille Kee qui ne communique pas les champs pertinants).

# 6 J'ai oublié de mettre à jour la base de donnée et le mdp généré n'est plus dans le presse papier, que faire ?

Pas de panique, votre mot de passe n'est pas perdu ! Kee génère toujours un souvenir du mot de passe généré aléatoirement par la procédure précédente !

Il suffit de chercher dans le dossier "Kee Generated Password Backup" une entrée dont l'URL est celle du site en question et qui est la dernière modifiée ! Elle contiendra cette URL et uniquement le mot de passe généré ! (Aucune possibilité d'embrouille sur ce coup là, mais cette entré est incomplète car il manque le login)

Vous pourrez donc modifier manuellement depuis KeePass l'entrée utilisée par Kee pour vous connecter au dit site pour y mettre le bon mot de passe et login. Vous devriez pouvoir vous reconnecter normalement avec Kee.

Remarque : lorsque vous êtes sur que les entrées que vous utilisez contiennent bien les mots de passe à jour et vous permettent une connection normale, vous pouvez bien sur supprimer les entrées créées par Kee pour sauvegarder les mots de passe générés bien sûr.


# Importer les mot de passe de Firefox

Cetains addons permettent d'extraire les mots de passe firefox et de les sauvegarder dans un fichier XML. Ce fichier pourra être ensuite lu par KeePass pour importer tous vos mot de passe.

Cependant celà ne marche pas toujours pour Linux. Si vous ne trouvez aucun moyen d'exporter vos mos de passe firefox vous pouvez suivre la procédure ci-dessous :

Nous allons extraire en JSON vos mots de passe firefox comme à la page :

https://support.mozilla.org/fr/questions/1077630#answer-834769

Vous devez notamment ouvrir la console du navigateur Firefox. 

Vous devez débloquer les options dévelloppeur, pour celà taper `about:config` dans la barre d'adresse et valider que vous prenez le risque (Firefox vous previens que vous allez manipuler des paramètres avancés).

Cherchez dans la barre de recherche la valeur `devtools.chrome.enable` et double cliquez sur la ligne pour passer la valeur sur `true`.

La console du navigateur est maintenant accessible via `Ctrl + Maj + J` ou dans le menu Firefox -> Développement Web -> Console Navigateur.

Maintenant copier-coller le script suivant dans la ligne d'entrée en bas de la console : 
```
/* export the names and passwords in JSON format to firefox-logins.json */
var tokendb = Cc["@mozilla.org/security/pk11tokendb;1"].createInstance(Ci.nsIPK11TokenDB);
var token = tokendb.getInternalKeyToken();

try {token.login(true)} catch(e) {Cu.reportError(e)}

if (!token.needsLogin() || token.isLoggedIn()) {
 var passwordmanager = Cc["@mozilla.org/login-manager;1"] .getService(Ci.nsILoginManager);
 var signons = passwordmanager.getAllLogins({});
 var json = JSON.stringify(signons, null, 1);

 var ps = Services.prompt;
 var txt = 'Logins: ' + signons.length;
 var obj = new Object; obj.value = json;

 if (ps.prompt(null, 'Logins - JSON', txt, obj, null, {})){
 var fp=Cc["@mozilla.org/filepicker;1"].createInstance(Ci.nsIFilePicker);
 fp.init(window,"",Ci.nsIFilePicker.modeSave);
 fp.defaultString = "firefox-logins.json";

 fp.open((rv) => {
 if (rv == Ci.nsIFilePicker.returnOK || rv == Ci.nsIFilePicker.returnReplace) {
 var fos = Cc['@mozilla.org/network/file-output-stream;1'].createInstance(Ci.nsIFileOutputStream);
 fos.init(fp.file, 0x02 | 0x08 | 0x20, 0666, 0);
 var converter = Cc['@mozilla.org/intl/converter-output-stream;1'].createInstance(Ci.nsIConverterOutputStream);

 converter.init(fos, 'UTF-8', 0, 0);
 converter.writeString(json);
 converter.close();
}})
}}
```
Une fenêtre s'affiche alors avec une grande ligne de texte et le nombre de mots de passe trouvé. Validez, firefox vous proposera de télécharger le fichier `firefox-logins.json` qui contiendra tous vos mots de passe, identifiants ainsi que les URL associées.

Il faut ensuite convertir le fichier JSON en CSV soit par Excel soit en utilisant des convertisseurs en ligne ou programmes (la bibliothèque Python pandas vous permet par exemple d'ouvrir un fichier JSON et de l'exporter en CSV, très pratique pour les ordinateur Linux).

Il faut ensuite créer une base de données dans KeePass et selectionner "Importer" dans le fichier "Nouvelle" et choisir l'importe par CSV générique.
