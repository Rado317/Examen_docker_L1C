## <h1>Volumes en docker</h1>

 1) petit explication d utilisation:

-----[on a ici un conteneur : [avec dossier 1 et 2 et 3 et 4] ]

->a) on supprime le conteneur mais on veut garder un dossier ex: 1.
->b) on utilise le volume alors le dossier sera stocker dans le volumes et ne sera pas supprimer.

## <h1>commande de volumes:</h1>

 1) expretion MAPPER un volume:

 conteneur1: /home et ordinateur: /test
->mapper test vers home alors home contiendra tous les contenues de test.   
->et si on modifier les donnees puis sauvegarder meme si le conteneur est supprimer 
->les modification et les contenue de home sera dans notra machine local /test
 
 ## 1-1/ creer test:

 -- mkdir volumes  

 -- cd volumes   

 -- touch index.html  

 -- pwd (chemin du fichier test pour mapper)

 ## volumes: 
 -- docker run -it --name [name] -v [chemin du fichier local [:] chemin dans notre conteneur] [image name]

## dans conteneur: VA DANS le fichier pour voir les contenues.

bonus(  
    -- apt update  
    -- apt install -y nano  
    -- nano [fichier] "tu peux modifier les contenues du fichier"  
    )

 ## ensuite :
 -- docker rm [name ou id conteneur]

 ## dans machine local:
 -- ouvre le fichier et tu vas voir les donners sauvegarder et modifier.



 2) expretion volumes manager:

 ## creer volumes
 -- docker volume create [name] 

  ## lister volumes
 -- docker volume ls

  ## detruire un columes

 -- docker volume rm [name]

## petit test: 

-- docker volume create test_volume

-- docker run -it---rm --name testVolume -v test_volumes:[pwd] [images] (docker va direct comprendre que c est un dossier manager)

-- exit puis -docker ps -a (voir si conteneur a bien ete supprimer)

-- aller dans docker desktop dans volume trouver le test_volume et voir les fichiers s'ils sont la.

## on va manager les donnees de cette volume:

--docker run -it --name [name] -v test_volume:[pwd] [images] 
-> il devrait y avoir tous les donnees dans notre test_volume.

## REMARQUE:
    S'il y avait deja un dossier dans pwd qui existe deja avec des donnes et qu'on manage un volumes qui porte les meme nom alors docker va prendre en compte le dossier manager et ecraser les dossier existant voir meme tous supprimer et remplacer.


 3) details dans volumes:
    
 -- docker volume inspect [name volume]


 ## <h1>PETIT RESUMER:</h1>

 -- si on a volume vide et dossier local remplis => volume sera remplis par dossier local.

 -- si on a volume remplis et dossier local vide => volume remplira dossier local.
