# Concours de sleep
1. Lancer plusieurs sleep 1000 en arrière plan sur votre système
```
for i in {1..5};do sleep 1000 &;done
```
3. retrouvez leur pids à l'aide de la commande pgrep.
```
pgrep sleep
```
4. tuez en une seule commande l'ensemble de ces sleep.
```
killall sleep
kill PID1....
kill $(pgrep sleep) 
pkill sleep
etc...
```
# Détarrage automatique

1. Créer un répertoire "depot" sous votre dossier d'accueil, vérifier que les autres ont les droits r et x sur le dossier.
2. Créer un répertoire "extraction" sous votre dossier d'accueil. 
3. Toutes les 10 minutes, vérifier la présence de fichiers archives en xz ou gz dans le répertoire depot et les décompresser dans le répertoire extraction. L'archive devra être supprimée.
```
find /home/user/depot -type f -regex '.*\.[gx]z$' -exec tar -xvf {} -C /home/user/extraction  \; -exec rm {} \;

sans la regexp (méta-caractères du bash):
find /home/lucas/depot -type f -iname "*.tar.[gx]z" -exec tar -xvf {} -C /home/lucas/extraction  \; -exec rm {} \;
```
4. Pour vérifier, créer les archives suivantes sous depot :
- archive du répertoire ~/Téléchargements en xz
```
tar -cvJf $HOME/depot/tele.tar.xz $HOME/Téléchargements
```
- archive du répertoire ~/Documents en gz 
```
tar -cvzf $HOME/depot/documents.tar.xz $HOME/Documents
```
# Quand est ce que je me connecte?
1. Au démarrage de ma session, je souhaite alimenter un fichier créé quotidiennement. A chaque connexion de mon user, l'heure de connexion devra être indiquée, pour chaque ligne dans le fichier j'aurai l'heure de connexion. Le nom du fichier doit prendre la forme sessions_AAMMJJ.log (example sessions_220323.log).

```
Dans le fichier .bashrc, ajouter la ligne:
echo "connexion à $(date +%H:%M:%S)" >> /home/lucas/session_$(date +\%Y\%m\%d).log
```

2. tous les soirs à 23h30, je souhaite mettre à la fin du fichier le nombre de fois ou je me suis connecté... Un ligne sous la forme : "nombre de connexions dans la journée = N"

```
30 23 * * *  echo "nombre de connexions dans la journée $(wc -l /home/lucas/session_$(date +\%Y\%m\%d).log | cut -d" " -f1)" >> /home/lucas/session_$(date +\%Y\%m\%d).log
```
