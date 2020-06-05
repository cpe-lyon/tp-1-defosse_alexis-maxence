**----------------------------------------------------------|Prise en main Linux & Bash|----------------------------------------------**

**Exercice 2: Prise en main de l'interpreteur de commandes**

**Manuel:**

1) A l’aide du manuel, identifiez le rôle de la commande which ?

        -> Le manuel *man* permet d'acceder au informations relative à une commande spécifique.

        Dans le cas de *wich*, la desciption est la suivante:

        " which  retourne  le  chemin des fichiers qui seraient exécutés dans
        l'environnement courant si ses arguments avaient été  donnés  comme
        commandes  dans un interpréteur de commandes strictement conforme à
        POSIX. Pour ce faire, which  cherche  dans  la  variable  PATH  les
        fichiers  exécutables  correspondants aux noms des arguments. which
        ne déréférence pas les liens symboliques."
     
2) Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme 
   option dans la page de manuel de which ?

         Pour faire l'action identique à *Ctrl-f" dans windows pour faire une recherche, dans linux et plus particulèrement
         dans le *man*, on peut utiliser "/pattern" pour rechercher en bas à partir de notre position ou "?pattern" pour la 
         recherche vers le haut. Dans cette question la réponse est donc **"/option"** ou **"?option"**.
   
3) Comment quitte-t-on le manuel ?

         Comme indiquer dans le manuel *"press h for help or q to quit"*, donc il faut appuyer sur la touche **q**.

4) Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la première page de la 
   section 6 ; de quoi parle cette section ?
   
         Pour savoir comment rechercher une page spécifique dans le man, on peut regarder le **man du man**, et ainsi regarder
         l'option correspondante.

         Dans le cas du *man*, on trouve: [-Z] [[section] page ...] ...

         On utilise donc **man 6 intro** pour afficher la section demandée, elle parle des *"programmes funs"* du système.
  
 **Navigation dans l'arborescence des fichiers:**
 
 1) allez dans le dossier /var/log : *cd /var/log*
 
 2) remontez dans le dossier parent (/var) en utilisant un chemin relatif : *cd /var*
 
 3) retournez dans le dossier personnel : **cd $home** ou $home est une variable d'environnement correspondant à notre répertoire personnel. On peut aussi utiliser **cd ~**.
 
 4) revenez au dossier précédent (/var) sans **utiliser de chemin** : **cd -**
 
 5) essayez d’accéder au dossier /root ; que se passe-t-il ? : **cd /root**
 
         Evidemment, on tombe sur un message d'erreur car nous n'avons pas les droits administrateurs...
    
 6) essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez : *sudo cd /root*
 
          Ne fonctionne pas car cd n'est pas un programme mais une commande: et sudo n'autorise que l'éxécution de
          programmes en mode root: sa ne marchera pas.
       
 7) à partir de votre dossier personnel, créez l’arborescence suivante...
 
         a) D'abord on créer les dossier via la commande *mkdir "nomDeDossier"*. Donc si on se trouve dans notre dossier personnel:
   
            mkdir Dossier1 Dossier2
   
            mkdir Dossier2/Dossier2.1 Dossier2/Dossier2.2
   
         b) Ensuite on créer les fichiers via la commande *touch*:
   
            touch Dossier1/Fichier1 Dossier2/Dossier2.2/Fichier2 Dossier2/Dossier2.2/Fichier3
 
  8) revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis
     Dossier1 ; que se passe-t-il ? 
   
   -> *rm* permet de supprimer un fichier, ici en l'occurence **Fichier1** mais elle ne permet pas de supprimer un dossier.
      Pour supprimer un dossier, il faut utiliser *rmdir*. (message d'erreur si on utilise *rm* sur un dossier.             
      
      Cela donne donc: 
      
      **rm Dossier1/Fichier1 ** et **rmdir Dossier1** 
      
   9) quelle commande permet de supprimer un dossier ? **rmdir**
   
   10) que se passe-t-il quand on applique cette commande à Dossier2 ?
   
       -> On obtient un message d'erreur *"rmdir: échec de suppression de «Dossier2»: Le dossier n'est pas vide"*
       (cohérent avec se qui à été expliquer précédement.)
       
   11) comment supprimer en une seule commande Dossier2 et son contenu ?
   
       -> Il faut dire à linux de supprimer *recursivement* le répertoire en utilisant l'option **-r**.
       
       Cela donne : **rm -r Dossier2**
       
   **Commandes importantes**

   1) Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?

      -> La commande *uptime* permet d'avoir l'heure et la commande *time* permet de
         connaitre le temps d'éxécution d'une commande/fichier.

   2) Dans votre dossier personnel, tapez successivement les commandes ls puis la ; 
      que peut-on en déduire sur les fichiers commençant par un point ?

      -> **ls** permet de lister les fichiers/répertoires d'un répertoire.

      -> **la** fait la même chose mais permet de voir les fichiers *cachés*.

   3) Où se situe le programme ls ? -> Dans le répertoire **bin/ls**.

   4) Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ?
      Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.

      -> **Alias ll='ls -alF'**

   5) Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ? -> **ls -F /bin**

   6) Que fait la commande ls .. ? -> Affiche le contenu du *répertoire parent*.

   7) Quelle commande donne le chemin complet du dossier courant ? -> **pwd**

   8) Que fait la commande echo 'yo' > plop exécutée 2 fois ?

      -> La première fois cela va créer le fichier *plop* et écrire 'yo' dedans.

      -> La seconde fois cela va ré-écrire le fichier *plop*, donc il restera inchangé.

   9) Que fait la commande echo 'yo' >> plop exécutée 2 fois ?

      -> Idem sauf que l'on va *ajouter* du contenu et non le ré-écrire. Ducoup, le fichier va contenir *yo* deux fois.

   10) A quoi sert la commande file ? Essayez la sur des fichiers de types différents.

      -> Cette commande permet d'avoir des précisions sur des fichiers/dossiers particuliers.

      Exemple dossier: *plop: ASCII text*, fichier: *Dossier1: directory *.

      Executable: **kill: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), 
      dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID 
      [sha1]=d05fe4924aacc4d09192ac08443a2c796194f392, stripped**

   11) Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien
       titi vers ce fichieravec la commande ln toto titi. Modifiez à présent le contenu de
       toto et affichez le contenu de titi : qu’observe-t-on ? Supprimez le fichier toto ;  
       quelle conséquence cela a-t-il sur titi ?

       -> Un lien ici va liée les deux fichiers: si on modifie l'un, on modifie l'autre.
          Supprimer l'un des deux fichier n'a pas d'incidence sur l'autre.

   12) Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu.
       Modifiez le contenu de titi ; quelle conséquence pour tutu ? Et inversement ? 
       Supprimez le fichier titi ; quelle conséquence cela a-t-il sur tutu ? 

       -> Ici on créer un *raccourci*: le fonctionnement est identique que le précédent mais
          si on supprimer le fichier le **raccourci n'est plus utilisable**.

   13) Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent
       d’interrompre et reprendre le défilement à l’écran ?

       -> **CTRL + S**

   14) Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, 
       puis seulement les lignes 10 à 20.

       -> 5 première ligne : **head -5 /var/log/syslog**
        
       -> 5 dernière ligne : **tail -n 15 /var/log/syslog**
   
       -> entre 10 et 20 : **tail -n 10 | head -20 /var/log/syslog**

   15) Que fait la commande dmesg | less ? -> Permet devoir les logs relatifs au kernel (noyau).

   16) Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet
      d’afficher la page de manuel de ce fichier ?                                                                           
      
      -> Ce dossier stocke l'intégralité des compte utilisateurs. (base de données)
         Cette base de données est liée à l'éxécutable *passwd*, consultable via le *man* avec **man 5 passwd**.

   17) Affichez seulement la première colonne triée par ordre alphabétique inverse

       -> Tri inverse première colonne **sort -d -r | cut -c1  /etc/passwd**.

   18) Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine 
       (pas seulement les utilisateurs connectés) ?

       -> **wc /etc/passwd**
   
   19) Combien de pages de manuel comportent le mot-clé conversion dans leur description ?

       -> **man -k conversion | wc -l**                                                                                                             
       
    20) A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents 
        sur la machine

        -> **find / -name passwd**                                                                                           
        
    21) Modifiez la commande précédente pour que la liste des fichiers trouvés soit 
        enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient 
        redirigées vers le fichier spécial /dev/null.

        -> **find / -name passwd > list_passwd_files.txt 2> /dev/null**                                                                           
        
    22) Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini 
        l’alias ll vu précédemment.

        -> **cat .bashrc | grep ll**                                                                                         
        
    23) Utilisez la commande locate pour trouver le fichier history.log.

        -> **locate -A history.log**                                                                                         
       
    24) Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. 
        Apparaît-il ? Pourquoi ?

        -> **touch testDeFichier**

        -> **locate -a testDeFichier** (aucun résultats) 
        Locate utilise une **base de donnée** pour rechercher des fichiers... Il faut mettre à jours cette base de données
        manuellmenent pour que *locate* puisse trouver notre fichier. Il faut faire : **updatedb**.


**Exercice 3**

1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec
nano

  -> sudo cp /var/log/syslog /home/TP1/log.txt

  -> sudo nano /TP1/log.txt

//ROOT//

sudo passwd root //créer un mdp pour root 

su root //Utiliser root 

2. Remplacez toutes les occurrences du mot kernel par le mot noyau

**ctrl + altgr + \**

Ensuite précise que le mot a changer est *kernel*, et ensuite on met *noyau* pour le remplacement.
Puis appuyer sur "A" pour l'appliquer a toutes les occurances.


3. Déplacer les 10 premières lignes à la fin du fichier

Au début du fichier, CTRL + K (10 fois)
Et ensuite ctrl + U à la fin 
(Pour aller à la fin on peut faire CTRL + _ et on rentre 9999)


4. Annulez cette action

ALT+U

5. Enregistrez le fichier avant de quitter nano

CTRL + O
CTRL + X

**Exercice 4. Personnalisation du shell**


3. Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter
puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite
de commande devrait immédiatement passer en couleurs.

 Enlever les commentaire de "force_color_prompt=yes"  dans ~./bashrc 
 puis faire source ~./bashrc
 L'invite de commande passe de blanc à vert.

4. Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc,
cherchez les lignes commençant par PS1= ; elles indiquent la mise en forme de l’invite de commande(selon que l’on est en couleurs ou non).


Pour rajouter l'heure il faut mettre au début (aprés ) : \[\e[91m\]\t  

                               -> heures avec les secondes en rouge light.

Pour le tirer il faut mettre \[\e[00m\]-

                               -> créer un tiret simple sans couleur

Pour mettre le répértoire courant avec un bleu plus claire il faut mettre 36m pour le répértoire (\w) -> \[\e[01;36m\]\w

PS1 complet :
'${debian_chroot:+($debian_chroot)} \[\e[91m\]\t \[\e[00m\]- \[\e[01;32m\]\u@\h\[\e[00m\]:\[\e[01;36m\]\w\[\033[00m\]\]$'

   

