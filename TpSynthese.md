Pèje est un utilisateur un peu curieux ,il aime se balader dans les répertoires de la direction et dans ceux des autres services.
Le chef de l’esi vous demande donc de cloisonner les différents répertoires présents sur le serveur afin que seuls les membres du groupe puissent y avoir accès.
Il vous demande donc de créer une nouvelle arborescence pour que les fichiers soient séparés par service (direction ,logistique,intex,pts).
Le directeur insiste sur le fait que les répetoires ne doivent êtres lisibles que si l’on appartient au service.
La direction à également un droit de lecture sur les fichiers de chaque services.
Afin de garantir la sécurité des données, il vous est demandé de réaliser une sauvegarde toutes les nuits des différents répertoires. Les sauvegardes devront se nommer « groupe-JJMMAAA.tar.gz ». 
Les users suivants doivent êtres présents sur les serveurs afin de réaliser les différents tests :
-peje
-intex
-pts
-logistique
-direction

Création des utilisateurs:
Useradd peje
Useradd intex
Useradd pts
Useradd logistique
Useradd direction –G intex,pts,logistique

