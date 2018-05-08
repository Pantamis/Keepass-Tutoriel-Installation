# Le Plugin Kee pour le navigateur Firefox

KeePass2 n'est pas intégrer au navigateur web mais il est intégrable. Je traîte ici le cas de Firefox.

## 1. KeePass2 aussi flexible que les outils de mots de passe Firefox

Kee est disponible sur le site https://www.kee.pm/ avec quelque tutoriel sur la page https://tutorial-addon.kee.pm/.
Kee permet à Firefox de communiquer avec KeePass2 pour vous éviter de devoir taper les mots de passe.

## 2. Installation et liaison Firefox

Quelque soit l'OS, vous devez tlécharger le plugin KeePassRPC.plgx à la page https://github.com/kee-org/keepassrpc/releases/ 

Il faut ensuite déplacer le plugin KeePassRPC.plgx dans le répertoire Plugins dans le répertoire d'installation.

Sur Firefox vous devez installer l'addon Kee qui se trouve ici : https://addons.mozilla.org/fr/firefox/addon/keefox/

La base de donnée qui contient vos mots de passe doit être ouverte sur le logiciel KeePass pour que Firefox puisse vous proposez de remplir les champs.

## 3. Pourquoi devrait-on l'installer ?

Si vous désirez une sécurité maximale, vous ne devez pas avoir à copier-coller votre mot de passe car c'est une très grosse faille de sécurité :

Si le système est vérolé, le virus (cheval de Troie classique) peut enregistrer l'état de la mémoire dont le presse-papier (zone de mémoire où le contenu mis en attente de collage est en attente). Cela signifit que votre mot de passe est vu en clair par le virus tant que vous n'avez pas modifié le contenu du presse papier (cad fait un Copier) !! Bien sur KeePass2 est prévoyant et ne laisse le mot de passe que temporairement dans le presse-papier le temps de le copier (12 seconde par défaut), mais vous sentez bien que c'est une faille. 

Conclusion : si désirez un maximum de protection (c'est le cas, vous lisez ce tutoriel), interdiction de copier-coller !

Le plugin KeePassRPC permet une connection chiffré entre KeePass et d'autres applications (Firefox via Kee). Ainsi un logiciel tier (malveillant) ne peut pas écouter ce qu'échange KeePass et l'application


## Importer mot de passe Firefox

Pour extraire en JSON voir la page :

https://support.mozilla.org/fr/questions/1077630#answer-834769


Utiliser le script : 
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
