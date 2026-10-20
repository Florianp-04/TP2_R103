# TP2_R103
Notre projet consiste à configurer une **image ISO** comprenant plusieurs outils pré-installés. 
Notre cahier des charges a été représenté sous forme de **barre de tâche**.

**Barre des tâches** concernant notre *projet de SAE1.03* : Préparer une image ISO
- [ ] Installer Cubic sur notre machine.
- [ ] Installer LAMP sur l'image ISO.
- [ ] Installer Forgejo sur l'image ISO.
- [ ] Système de sauvegarde automatique : Restic.
- [ ] Configuration du /var/www/html.
- [ ] Personnalisation du système (fond d'écran, .bashrc, .bash_profile, ...).
- [ ] Installer l'image ISO.
- [ ] Terminer la configuration.

1. Installer Cubic sur notre machine.
- Installer Cubic est simple, on se rend sur le site officiel, et on suit le tuto pas a pas pour la machine correspondante.
- Une fois Cubic installer, on installe l'image ISO de trisquel12 et on créer un projet.
2. Installer LAMP et PHPMyAdmin sur l'image ISO.
- Dans Cubic, installer LAMP est assez simple, il suffit de suivre le tuto deja vu.
- Pour PHPMyAdmin, il y a plusieurs tuto en ligne donc c'était aussi assez facile.
3. Installer Forgejo sur l'image ISO.
- Il suffit de suivre le tuto sur le site de forgejo encore une fois pour la machine correspondante.
4. Système de sauvegarde automatique : Restic.
   Restic est un système de sauvegarde chiffré qui a la possibilité d'être configurer pour devenir automatique. De notre côté, nous avons trouvé utile d'avoir une sauvegarde tous les matins à 9h.
   * Premièrement, il a fallu installer Restic sur la machine :
     La démarche est simple, il faut récupérer tous les paquets puis installer restic.
   * Deuxièmement, dans Cubic, il faut paramétrer 6 éléments au total :
      * Un script qui initialise Restic directement une fois l'installation de l'IOS.
      * Un script qui fait une sauvegarde avec Restic, et qui ne garde que les 3 dernières.
      * Un script systemd en .timer qui donne le cycle de sauvegarde.
      * Un script systemd en .service qui fait exécute le script de sauvegarde en fonction du timer.
      * Le dossier /media/backup/restic pour stocker les sauvegardes.
      * Le fichier dans /etc/restic/password pour stocker le mot de passe.
   * La dernière étape est après l'installation de l'image ISO. On doit ainsi lancer le script restic-init pour initialiser Restic. Puis il faut activer le .timer pour la sauvegarde automatique. Et pour finir, il faut configurer le fichier /etc/restic/password de façon sécurisé.

   Une fois toutes ces étapes réalisés, Restic fera des sauvegardes tous les jours à 9h, en gardant seulement les 3 dernières sauvegardes.
     
5. Configuration du /var/www/html.
   

6. Personnalisation du système.
   Une modification du système a été appliquée à différents endroits : Le fond d'écran par défaut a été changé, ainsi    que le thème du bureau et les icônes. De plus, le terminal a été personnalisé.
7. Installer l'image ISO.

8. Terminer la configuration.
   
