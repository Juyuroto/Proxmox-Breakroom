# Impossible d'envoyer des fichiers

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/upload-413/`

## Énoncé

Ticket : « Les utilisateurs n'arrivent plus à envoyer de fichiers sur `http://localhost/upload` dès qu'ils dépassent quelques centaines de Ko. »

Objectif : un envoi de 5 Mo fonctionne : `curl --data-binary @fichier http://localhost/upload` répond « upload ok ».