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
* Installer Ubuntu depuis le Windows Store
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
Aller dans le Menu démarrer > taper Powershell > Cliquer sur *Exécuter en tant qu'administrateur* dans la panneau droit des résultats de la recherche.

(Windows PowerShell est un outil assez puissant qui permet de contrôler Windows en tapant simplement des commandes au lieu de se balader dans des menus. Imaginez la configuration de 1000 PCs avec seulement des clics :-( )

Faire un copier coller de la commande suivante :

```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```

Valider toutes les commandes de ce guide en appuyant sur la touche Entrée.

Patienter pendant l'installation du module, puis confirmer avec Y pour redémarrer le PC.

C'est fait.

<hr>

### Installer WSL depuis les menus Windows (2 minutes)
Alternative à la méthode avec PowerShell.
Cliquer sur le menu démarrer > taper *Activer ou désactiver des fonctionnalités Windows* > cliquer sur le raccourci.

Dans la liste, cocher le *Sous-système Windows pour Linux* et valider avec OK, redémarrer le PC.

<hr>

### Installer Ubuntu depuis le Windows Store
C'est la méthode la plus facile mais il y a 2 limitations : vous ne pouvez installer qu'un seul système à la fois et il sera placé sur le disque système (le plus souvent C:\, là où est installé Windows). Moi je manque d'espace disque, alors j'évite.

Cliquer sur le menu démarrer > taper Store > cliquer sur le raccourci vers le *Microsoft Store*.
Dans le Store, taper dans la barre de recherche en haut : Ubuntu 18.04 LTS.
L'installer et le lancer.

Au 1er lancement, il vous demande de choisir un nom d'utilisateur et un mot de passe pour *UNIX*, choisissez ce que vous voulez mais ne les oubliez pas !!!

Et voilà, vous êtes sous Ubuntu depuis Windows 10.

Mais où est l'interface graphique ? Voyez plus loin dans mes cours.

<hr>

### Installer Ubuntu dans WSL sans passer par le Windows Store (installation hors ligne, 30 minutes)
Cette méthode vous permet :
* d'installer plusieurs distributions en parallèle, soit des distributions différentes, soit la même mais avec des environnements différents, ce qui permet d'avoir une machine pour compiler Android 7 et une pour compiler Android 9. Yessss.
* d'installer la distribution de votre choix sur le disque de votre choix (quand vous manquez de place sur C:\)
* de se passer des sudo en installant une distribution root (si vous ne comprenez pas c'est normal, c'est pour les geeks)

Et tout ça sans quitter Windows 10. C'est parti.

**CHANTIER EN COURS, ça arrive**
