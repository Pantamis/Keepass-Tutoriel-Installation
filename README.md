## Keepass-Tutoriel-Installation

* Keepass est un gestionnaire de mot de passe. Il est certifié par l'ANSSI depuis 2013 et recommandé par la CNIL : 
    * https://www.youtube.com/watch?v=XTnDKJl1zOQ
    * https://www.ssi.gouv.fr/entreprise/certification_cspn/keepass-version-2-10-portable/
    * https://www.cnil.fr/fr/les-conseils-de-la-cnil-pour-un-bon-mot-de-passe
    
Keepass est open-source, donc gratuit, compatble windows linux et mac. Il est disponible aussi sur Android 
et bien qu'il soit installé en standalone il existe des plugins permettant de l'intégrer aux navigateur et 
particulièrement Firefox via Kee (plugin téléchargeable sur le site Mozilla).


# 1 Principe de base :

Un mot de passe pour les retenir tous !
Keepass permet de créer et gérer des bases de données chiffrées contenant des codes d'accès. 
Un mot de passe est donc nécessaire pour ouvrir la base de données (chiffrés AES-256 par défaut, 
un standard de chiffrement très sûr).
Il sera imposible de retrouver les mots de passes contenu dans le fichier sans ce mot de pass maître, ne le perdez pas !

Vous savez peut être que les navigateurs propose une telle possibilité mais l'algorithme de chiffrement est assez faible 
(des logiciels permettent de cracker le mot de passe de manière assez fiable) et peut être n'accorderiez vous pas 
une confiance infaillible à votre navigateur pour retenir vos mot de passe sans risque de les divulger.

# 2 Installation Logiciel de base

A télécharger sur keepass.info. Après installation du logiciel en anglais par défaut, 
une traduction française est diponible ici : https://keepass.info/translations.html

# 3 Sur ce dépôt Git :

* Vous trouverez des informations pour :
    * Installer Keepass
    * Installer le plugin Kee pour Firefox
    * Créer une base de donnée sur votre serveur personnel en SAMBA (partage Windows)
    * La synchroniser avec les changements réalisé sur votre ordinateur en local

