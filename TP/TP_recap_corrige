# Détarrage automatique

1. Créer un répertoire "depot" sous votre dossier d'accueil, vérifier que les autres ont les droits r et x sur le dossier.
2. Créer un répertoire "extraction" sous votre dossier d'accueil. 
3. Toutes les 10 minutes, vérifier la présence de fichiers archives en xz ou gz dans le répertoire depot et les décompresser dans le répertoire extraction. L'archive devra être supprimée.
```
find /home/user/depot -type f -regex '.*\.[gx]z$' -exec tar -xvf {} -C /home/user/extraction --remove-files \;
```

