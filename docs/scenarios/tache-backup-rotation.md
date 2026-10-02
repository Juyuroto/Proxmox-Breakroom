# Sauvegardes avec rotation

**Type :** Tâche · **Difficulté :** difficile · **Dossier :** `scenarios/tache-backup-rotation/`

## Énoncé

Objectif : écris le script exécutable `/usr/local/bin/backup-www` qui :
- crée `/backup/www-AAAA-MM-JJ.tar.gz` (date du jour) contenant `/var/www` ;
- ne garde que les **7** archives `www-*.tar.gz` les plus récentes dans `/backup`.

Puis planifie-le avec cron **chaque nuit à 2 h**.