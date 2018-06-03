# Comment importer les mots de passe depuis Firefox dans une base de donnée KeePass ?

KeePass propose d'importer des mots de passe conservés dans certaines base de données. 
Par défaut KeePass ne propose pas d'outils pour importer les mots de passe des navigateurs.
Dans ce tuto, nous allons détailler une solution qui fonctionne toujours quelquesoit l'OS et la version de Firefox.

## 1. Utiliser un module Firefox

Il existe des modules permettant d'importer ses mots de passe Firefox dans différent format (XML notamment).
Dans le menu Fichier de KeePass, vous trouverez une option "Importer". 
La seule condition est que le module exporte vos mots de passe dans un format disponible dans KeePass 

## 2. Utiliser un module KeePass

Sur https://keepass.info/plugins.html vous trouverez deux plugins permettant d'importer directement 
des mots de passe de Firefox :
   - KeePassBrowserImporter est certainement le plus recommandable car il prétend gérer tous les navigateurs et offre des options supplémentaires
   - Firefox to KeePass Password Importer est spécifique Firefox mais ne semble pas gérer les dernière versions du navigateur
   
## 3. Si rien ne fonctionne (car OS linux par exemple ou plugins pas à jour) :

Si vous ne trouvez aucun moyen d'exporter vos mos de passe firefox vous pouvez suivre la procédure ci-dessous qui est plus compliquée mais garantie de fonctionner :

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
Une fenêtre s'affiche alors avec une grande ligne de texte et le nombre de mots de passe trouvés. Validez, Firefox vous proposera de télécharger le fichier `firefox-logins.json` qui contiendra tous vos mots de passe, identifiants ainsi que les URL associées.

Il faut ensuite convertir le fichier JSON en CSV soit par Excel soit en utilisant des convertisseurs en ligne ou programmes (la bibliothèque Python pandas vous permet par exemple d'ouvrir un fichier JSON et de l'exporter en CSV, très pratique pour les ordinateur Linux).

Il faut ensuite créer une base de données dans KeePass et selectionner "Importer" dans le fichier "Nouvelle" et choisir l'import par CSV générique.
