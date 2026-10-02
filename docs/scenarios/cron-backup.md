# La sauvegarde ne tourne plus

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/cron-backup/`

## Énoncé

Ticket : « Une tâche cron doit créer `/backup/etc.tar.gz` chaque minute via `/usr/local/bin/backup.sh`. Plus aucune sauvegarde n'est produite. »

Objectif : la sauvegarde est régénérée automatiquement chaque minute (la vérification prend environ 70 s).