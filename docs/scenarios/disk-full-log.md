# Le disque est plein

**Type :** Panne · **Difficulté :** facile · **Dossier :** `scenarios/disk-full-log/`

## Énoncé

Ticket : « Le disque est plein, plus rien ne s'écrit sur le serveur. »

Objectif : `/` utilisé à moins de 70 %, **sans supprimer** `/var/log/app/app.log` ni arrêter le service `app-logger` (l'application doit continuer à écrire dans son journal).