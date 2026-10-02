# Scénarios

Une fiche par scénario (énoncé, causes, pistes, notions, solution).

Les notions seront mises à jour à chaque scénario réussi.

## Pannes (27)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | [Alice ne peut plus se connecter](user-locked-1.md) | `passwd -S`, `passwd -u`, `/etc/shadow` |
| facile | [La commande report ne marche plus](script-broken.md) | ... |
| facile | [Le disque est plein](disk-full-log.md) | ... |
| facile | [Le site web est en panne](nginx-down.md) | ... |
| facile | [Le tableau de bord est injoignable](app-bind.md) | ... |
| facile | [Permission denied dans /tmp](tmp-perms.md) | ... |
| facile | [localhost ne répond plus](localhost-broken.md) | ... |
| moyen | [502 Bad Gateway sur l'API](nginx-502.md) | ... |
| moyen | [Disque plein fantôme](disk-full.md) | ... |
| moyen | [Impossible d'envoyer des fichiers](upload-413.md) | ... |
| moyen | [L'application n'accède plus à sa base](pg-access.md) | ... |
| moyen | [L'intranet affiche la mauvaise page](nginx-vhost-broken.md) | ... |
| moyen | [La base de données ne démarre plus](postgres-down.md) | ... |
| moyen | [La sauvegarde ne tourne plus](cron-backup.md) | ... |
| moyen | [Le nettoyage automatique ne tourne plus](timer-broken.md) | ... |
| moyen | [Le rapport automatique n'est plus généré](cron-env.md) | ... |
| moyen | [Le serveur rame](cpu-hog.md) | ... |
| moyen | [Le service interne ne démarre plus](app-service.md) | ... |
| moyen | [Plus d'accès à Internet](net-no-route.md) | ... |
| moyen | [apt n'arrive plus à télécharger](dns-broken.md) | ... |
| moyen | [apt update est en erreur](apt-broken.md) | ... |
| moyen | [sudo ne marche plus pour deploy](sudo-broken.md) | ... |
| moyen | [« No space left on device »](inodes.md) | ... |
| difficile | [Erreur de sécurité HTTPS](cert-expired.md) | ... |
| difficile | [Incident : le site et l'API sont tombés](incident-api.md) | ... |
| difficile | [Le worker redémarre en boucle](worker-env.md) | ... |
| difficile | [Too many open files](fd-limit.md) | ... |

## Tâches (18)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | [Base de données pour une appli](tache-postgres-db.md) | ... |
| facile | [Compte de déploiement](tache-sudo-user.md) | ... |
| facile | [Durcir SSH](tache-ssh-hardening.md) | ... |
| facile | [Planifier une tâche](tache-cron-job.md) | ... |
| facile | [Retrouver un fichier égaré](tache-find-secret.md) | ... |
| facile | [Rotation des logs](tache-logrotate.md) | ... |
| facile | [Régler le fuseau horaire](tache-timezone.md) | ... |
| moyen | [Accès SSH par clé](tache-ssh-key-user.md) | ... |
| moyen | [Analyser des logs](tache-log-analysis.md) | ... |
| moyen | [Dossier partagé d'équipe](tache-shared-folder.md) | ... |
| moyen | [Exposer une API derrière Nginx](tache-reverse-proxy.md) | ... |
| moyen | [Héberger deux sites](tache-nginx-vhosts.md) | ... |
| moyen | [Passer le site en HTTPS](tache-https.md) | ... |
| moyen | [Protéger une page par mot de passe](tache-basic-auth.md) | ... |
| moyen | [Restaurer une table supprimée](tache-db-restore.md) | ... |
| moyen | [Script de supervision](tache-healthcheck-script.md) | ... |
| moyen | [Transformer un script en service](tache-systemd-service.md) | ... |
| difficile | [Sauvegardes avec rotation](tache-backup-rotation.md) | ... |