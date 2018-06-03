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

