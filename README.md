## Keepass-Tutoriel-Installation

* Keepass est un gestionnaire de mot de passe. Il est certifié par l'ANSSI depuis 2013 et recommandé par la CNIL : 
    * https://www.youtube.com/watch?v=XTnDKJl1zOQ
    * https://www.ssi.gouv.fr/entreprise/certification_cspn/keepass-version-2-10-portable/
    * https://www.cnil.fr/fr/les-conseils-de-la-cnil-pour-un-bon-mot-de-passe
    
Keepass est open-source, donc gratuit, compatible windows linux et mac. Il est disponible aussi sur Android 
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

# 2. Pourquoi l'installer ? J'ai pas confiance ...


KeePass est un gestionnaire de mot de passe open source certifié OSI (il est donc bien maintenu par le créateur et la communauté) et certifié par l'ANSSI (Agence Nationale de la Sécurité des Systèmes d'Information). Cette certification (dites de sécurité de premier niveau) assure que la version du logiciel testé (la 2.10 pour KeePass, mais le logiciel n'a pas changé sensiblement sur son système de sécurité) est conforme à ce que prétend assurer le logiciel en terme de sécurité. Donc c'est du sérieux ! Le fichier contenant vos mots de passe est très bien sécurisé si vous choississez un mot de passe maître.

Une bonne raison d'utiliser ce type de logiciel est la suivante : https://xkcd.com/792/. La réutilisation chronique des même mots de passe est dangereuse car en cas de fuite de vos mot de passe sur des sites même anecdotique, on peut réussir à deviner comment vous formez vos mots de passe et donc prendre possession de tous vos comptes pour usurper votre identité et/ou vous volez (il suffit notamment de prendre possession du compte mail utilisé en récupération de vos mots de passe). KeePass dispose d'un générateur de mots de passe aléatoires. Les mots de passe générés aléatoirement sont de TRÈS LOIN les PLUS FORTS, et pour cause le fait d'être généré de cette façon à pour conséquence que :

   -Même si par inadvertence ils s'afficheraient en clair temporairement (comme sur les smartphones par un copier-coller) une personne qui regarderait l'écran aurait une (très) grande difficulté à les lire et donc les mémoriser
   -Ils imposent aux potentiels hackeurs de vous attaquer par pure brute-force, aucune technique de dictionnaire ou social engeneering ne permet d'éventuellement gagner du temps. Celà à pour conséquence que :
   -Ils seront forcément les derniers mots de passe essayés par un éventuel hackeur tenace, ils sont donc les PLUS FORT DE TOUS. A ce niveau là, si vos mots de passe sont assez longs, ce n'est plus un individu qui attaque vos mots de passe mais une organisation (entreprise ou État...)
   -Ils évitent de tomber dans l'usage le plus déconseilé des mots de passe : la réutilisation. La réutilisation d'un mot de passe ou de variantes de celui-ci sur plusieurs sites rendent tous ces mots de passe faibles dés lors que deux sites sur lesquelles vous êtes inscrit ont vu leurs identifiants et mots de passe fuiter (on peut alors identifier les éléments communs à ses mots de passes et la façon de créer les variantes). Les mots de passe généré aléatoirement ne sont PAS REPRODUCTIBLES, chaque site à un mot de passe très différent, risque 0.
   -Vous vous dépendez en revanche de KeePass pour retrouver vos mots de passe (n'espérez pas retrouver de tête des mots de passe que vous n'avez pas choisi et que vous ne saisirez jamais). Il faudra donc créer dupliquer et synchroniser les fichiers de base de données cryptée pour disposer de sauvegardes accessible partout tant que vos mots de passe sont générés ainsi (remarquez que c'est peut être déjà le cas alors que vos mots de passe sont faibles...)

Enfin, pourquoi KeePass plus qu'un autre ? Dernièrement LastPass, une entreprise proposant un gestionnaire de mot de passe, a été hackée ! L'entreprise promet que les mots de passe de ces utilisateurs n'ont pas fuité mais personne ne peut vérifier puisqu'on n'a pas le code source (logiciel propriétaire) !! Vous avez compris : avec KeePass vous avez un logociel dont des pointures peuvent vérifier qu'il fait le job. Vous avez le controle de vôtre de base de donnée chiffrée, vous la savez bien sécurisée, vous avez votre sécurité en main. KeePass est le seul logiciel libre dont le niveau de sécurité est officiellement éprouvé et libre.

# 3. Installation Logiciel de base

A télécharger sur keepass.info. Après installation du logiciel en anglais par défaut, 
une traduction française est diponible ici : https://keepass.info/translations.html

# 4. Sur ce dépôt Git :

* Vous trouverez des informations pour :
    * Installer Keepass
    * Installer le plugin Kee pour Firefox et comment l'utiliser
    * Synchroniser avec les changements réalisé sur votre ordinateur en local avec une base de données dans le cloud
    * Un script pour importer les mots de passe Firefox et les intégrer à Keepass


