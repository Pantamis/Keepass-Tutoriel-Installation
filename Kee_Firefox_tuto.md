## Le Plugin Kee pour le naviagateur Firefox

KeePass2 n'est pas intégrer au navigateur web mais il est intégrable. Je traîte ici le cas de Firefox.

# 1. KeePass2 aussi flexible que les outils de mots de passe Firefox

Kee est disponible sur le site https://www.kee.pm/ avec quelque tutoriel.
Kee permet à Firefox de communiquer avec KeePass2 pour vous éviter de devoir taper les mots de passe



## Importer mot de passe Firefox

Pour extraire en JSON voir la page :

https://support.mozilla.org/fr/questions/1077630#answer-834769


Utiliser le script : 
`
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
`
