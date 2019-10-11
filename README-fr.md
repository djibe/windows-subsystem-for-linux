# Windows Subsystem for Linux et le Sous-système Windows pour Linux pour les nuls
Tout ce qu'il vous faut pour maîtriser Windows Subsystem for Linux, le Sous-système Windows pour Linux, ou plus simplement, WSL.

Le mot d'ordre ici, c'est rendre la chose accessible aux plus nuls, comme moi.
Si vous ne comprenez pas, cliquez sur l'onglet Issues en haut de la page et écrivez moi.
Allez, c'est parti.

J'ai découvert WSL il y a une semaine et je ne suis pas informaticien. Voilà tout ce que j'aurais aimé savoir.
(Pourquoi je me suis lancé dedans ? Pour pouvoir compiler Android pour des smartphones ancien.)



## À quoi ça sert WSL ?
Ca vous permet d'utiliser tout l'environnement Linux depuis Windows 10.
Pour coder, mais aussi utiliser certains logiciels qui ne sont que sur Linux ou compiler des logiciels Open Source comme Android.

Plus loin je parle de distribution, dans le monde Linux, une distribution est un ensemble d'applications ajoutées au noyau (le vrai Linux). Il en existe beaucoup, les distributions les plus connues sont Ubuntu, Debian, Arch, Cinnamon ...
Je vais ici utiliser Ubuntu puisque je débute.



**Ce que vous allez apprendre ici, le plus simplement du monde**
* Utiliser Ubuntu depuis Windows
* Installer WSL avec PowerShell
* Installer WSL depuis les menus Windows
* Installer Ubuntu dans WSL sans passer par le Windows Store (installation hors ligne)
* Installer Ubuntu dans WSL sur le disque ou la partition de votre choix
* Utiliser différents Ubuntu WSL en parallèle
* Déplacer de partition une distribution WSL
* Cloner un Ubuntu WSL
* Faire une sauvegarde de votre Ubuntu WSL
* Maitriser toutes les commandes WSL
* Éditer les fichiers d'Ubuntu WSL avec VS Code (Visual Studio Code de Microsoft)


<hr>


### Installer WSL avec PowerShell (2 minutes)
Votre Windows 10 doit être en version 1903
(Pour le savoir, cliquer sur l'icône du menu démarrer, en bas à gauche de l'écran, taper winver puis cliquer sur le raccourci affiché. Dans la fenêtre qui s'ouvre, il est indiqué 1903. Si ce n'est pas le cas, lancez les mises à jour de Windows).

Maintenant, on installe le Windows Subsystem for Linux, qui est un composant additionnel de Windows 10.
Aller dans le Menu démarrer > taper Powershell > Cliquer sur Exécuter en tant qu'administrateur dans la panneau droit des résultats de la recherche.

Faire un copier coller de la commande suivante :

```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```

Valider toutes les commandes de ce guide en appuyant sur la touche Entrée.

Patienter pendant l'installation du module, puis confirmer avec Y pour redémarrer le PC.

C'est fait.


### Installer WSL depuis les menus Windows (2 minutes)
Cliquer sur le menu démarrer > taper *Activer ou désactiver des fonctionnalités Windows* > cliquer sur le raccourci.

Dans la liste, cocher le *Sous-système Windows pour Linux* et valider avec OK, redémarrer le PC
