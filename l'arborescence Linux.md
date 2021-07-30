Arborescence du système LinuxWiki   

Arborescence du système Linux
=============================

Introduction
------------

  
  
Notre système Linux possède des dossiers et des fichiers.  
Chaque dossier a son utilité, et tout n'est pas stocké n'importe comment.  
Dans cet article, je vais expliquer les notions de systèmes de fichiers, de racine, et de chemin.  
  

Le système de fichiers, racine, chemin
--------------------------------------

  
  
Notre système de fichiers sous Linux est organisé. Chaque dossier à la racine de l'arborescence a une utilité particulière.  
  
On appelle cela une «arborescence» car schématiquement, nous partons de la racine du système de fichiers, nous parcourons cette arborescence en allant de dossiers en dossiers. (Un peu comme un arbre)  
  
Il n'y a pas d'arbre sans racine ! Donc, tout chemin de fichiers dans le système Linux part de la racine. Cette racine est notée **/** (slash).  
  
Cette racine est "à peu près" comparable au **C:\\** de Windows, histoire de faire un grossier parallèle.  
  
A noter, quand on part de la racine puis qu'on parcours les dossiers, l'ensemble de la localisation est appelée chemin.  
  
Il existe 2 représentations d'un chemin :  
\- Chemin absolu, qui part de la racine : **/home/adrien/Documents/Comptes**  
\- Chemin relatif, qui part de l'endroit où on se situe. Exemple, si on se situe dans /home/adrien, un chemin relatif est **Documents/Comptes**  
  
  

Un répertoire pour chaque utilisation
-------------------------------------

  
  
Dans cette racine (/), on y trouve un certain nombre de répertoires, bien défini. Chacun à son rôle.  
  

*   **/ =>** Racine, elle contient les répertoires principaux
*   **/bin (binaries) =>** Exécutables essentiels au système, utilisables par tous les utilisateurs (ls pwd cp)
*   **/boot =>** fichiers permettant à Linux de démarrer
*   **/dev (device) =>** Fichiers spéciaux représentant les point d'entrées de tous les périphériques (fichiers spéciaux des disques dusr, écrans, partitions, consoles TTY, webcam)
*   **/etc (editing text config) =>** Contient les fichiers texte nécessaires à la configuration du système et des setvices (XXX.conf, passwd, inittab, fstab)
*   **/home =>** Répertoire personnel des utilisateurs
*   **/lib (librairies) =>** contient les bibliothèques partagées essentielles au système lors du démarrage (et modules noyau)
*   **/lib64 =>** idem /lib mais pour les 64bits (parfois, on trouvera lib et lib32. Dans ce cas, lib = 64bits et lib32 = 32bits)
*   **/mnt (mount) /media** \=> Là où les ressources peuvent être montées de manière permanente (/media) ou temporaire (/mnt)
*   **/opt (optional) =>** Répertoire générique pour l'installation de programmes installés hors dépôts de la distribution.
*   **/proc (process) =>** Répertoire virtuel ne prenant aucune place sur le disque. Contient des informations sur le système (noyau, processus).
*   **/root =>** Répertoire personnel du super utilisateur (le répertoire de root n'est pas dans /home, car bien souvent le /home est sur une partition à part. En cas d'échec de montage de /home, root à quand même accès à son répertoire personnel).
*   **/run (runtime system) =>** Contient des informations relatives au système concernant les utilisateurs et les services en cours d'exécution.
*   **/sbin (super binaries) =>** Contient les programmes système essentiels utilisables par l'admin uniquement.
*   **/srv (services) =>** N'est pas présent dans toutes les distributions. C'est un répertoire de données pour divers services (stockage des documents de comptes FTP, ou pages de sites web)
*   **/sys =>** Répertoire virtuel ne prenant aucune place sur le disque. Contient des informations entre le système et ses composants matériels.
*   **/tmp (temporary) =>** Répertoire fichier temporaires
*   **/usr (Unix System Resources) =>** Contient des programmes installés (**/usr/bin**) avec leur librairies (**/usr/lib** ou **/usr/lib64**) tels que firefox, libreoffice, ... quelques programmes réservés à l'admin système (**/usr/sbin**) et les fichiers de code source (**/usr/src**). On y retrouve **/usr/share** avec les éléments partagés indépendants de l'architecture (documentation, icônes, ...). Dans **/usr/local** on pourra installer les programmes compilés manuellement sur le système.
*   **/var (variable) =>** contient les données variables (fichiers de log dans **/var/log**) mais parfois les bases de données (/var/lib/mysql) et les pages de site web (/var/www/html)  
      
    

  
  
Il est tout à fait possible de créer d'autres dossiers dans la racine (par exemple /data), ce n'est pas interdit. Les dossiers présentés ci-dessus sont ceux qui sont là, par défaut, avec leurs utilité.  
  
Sur les distributions basées sur Red Hat, quelques modifications de l'arborescence ont eu lieu récemment.  
  
Vous avez peut être entendu parler du **_usermove_**, et bien c'est cette opération qui a eu pour but de déplacer les exécutables des dossiers ci-dessous dans le dossier /usr puis d'avoir un lien symbolique pour conserver la compatibilité avec les anciennes applications  
  

Code BASH :

ls \-l / | egrep "^l"
lrwxrwxrwx.   1 root root     7 25 août  14:45 bin -\> usr/bin
lrwxrwxrwx.   1 root root     7 25 août  14:45 lib -\> usr/lib
lrwxrwxrwx.   1 root root     9 25 août  14:45 lib64 -\> usr/lib64
lrwxrwxrwx.   1 root root     8 25 août  14:45 sbin -\> usr/sbin