## Installer et utiliser Keepass

# 1 Ou et quoi ?
Pour installer rendez-vous sur la page : https://keepass.info/.

/!\ Attention le site keepass.fr est un site d'hamonçennage !
Vous pourrez installer une traduction de Keepass en suivant le lien https://keepass.info/translations.html.

# 2 Quelles versions ?

Sur la page https://keepass.info/download.html vous trouverez deux versions téléchargeable. 
Je vous recommande la version 2 comptible avec tous les OSs et une belle application Android.

Choisir "Installer" pour l'installer sur un ordinateur et "Portable" si vous souhaitez créer une clé USB en standalone.
Vous aurez besoin de retrouver le répertoire d'installation de KeePass2 (généralement ProgrammsFile sur windows 
et /usr/lib/keepass2 sur Linux)

# 3 Installation Linux

Vous pourrez télécharger un .deb précompilé pour un OS basé Debian à la page : 
https://packages.debian.org/sid/utils/keepass2

Bien que ce packet propose d'installer les libraries mono nécessaires pour un fonctionnement minimaliste, 
il faut installer les lib mono pour que tout fonctionne bien sur Linux 
notamment les plugins de liaison avec les navigateurs. 

Pour celà :
sudo apt install mono-complete
Bien que basé Windows, KeePass2 fonctionne parfaitement sur Linux.

# 4 Au lancement

Lors du premier lancement, KeePass2 vous proposera de lier les extensions de fichier .kdbx à KeePass2 
(l'OS les ouvrira par défaut avec KeePass2 si vous acceptez). 

Les fichiers .kdbx créés et gérés par KeePass2 sont des fichiers bases de données. Ils sont chiffrés, 
KeePass2 vous demandera donc le mot de passe maître du fichier à la création et à l'ouverture.

A la création d'un fichier .kdbx, KeePass2 vous fera définir un mot de passe et vous l'évaluera (score entropique, 
le nombre de tentatives à faire pour trouver le mot de passe par force brute et dictionnaire est approximatiovement 
2 puissance le nombre de bits indiqués, le maximum est 256). 

Il n'y a aucun restriction par KeePass2 sur la qualité du mot de passe maître mais il doit être fort :
en effet le fichier qu'il protège contient tous vos autres mots de passe en clair. Vos autres mots de passe,
aussi forts soient-ils, deviennent faibles si le mot de passe maître est faible. En revanche, il faut toujours 
pouvoir le retrouver car il n'existe aucun autre moyen de le retrouver que de fouiller votre mémoire jusqu'à épuisement 
de vos idées.


Conseil pour créer un mot de passe fort facile à retenir : https://xkcd.com/936/
Préférez donc les mots longs sans rapport les uns aux autres pour produire un mot de passe fort facile à retenir.

# 4 Installer une traduction ou des plugins

* Depuis le répertoire d'installation :
    * Télécharger French.lngx, à la page https://keepass.info/translations.html (choisir la bonne version)
    * Dans le répertoire Languages, déposer le fichier French.lngx

* Pour les plugins :
    * Télécharger le plugin voulu de préférence depuis la page https://keepass.info/plugins.html
    * Déplacer le contenu dans le répertoir Plugins dans le répertoire d'installation de KeePass2
