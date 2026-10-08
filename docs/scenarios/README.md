# Scénarios

Une fiche par scénario (énoncé, causes, pistes, notions, solution).

Les notions seront mises à jour à chaque scénario réussi.

## Pannes (34)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | [Alice ne peut plus se connecter](user-locked-1.md) | `passwd -S`, `passwd -u`, `/etc/shadow` |
| facile | [Alice ne peut plus se connecter](user-locked-2.md) | `ls -l`, `chown`, propriétaire d'un dossier |
| facile | La commande report ne marche plus | ... |
| facile | [Le disque est plein](disk-full-log.md) | `df`, `du`, `lsof +L1`, `truncate`, fichier supprimé mais ouvert |
| facile | [Le site web est en panne](nginx-down-1.md) | ... |
| facile | Le tableau de bord est injoignable | ... |
| facile | Permission denied dans /tmp | ... |
| facile | localhost ne répond plus | ... |
| moyen | 502 Bad Gateway sur l'API | ... |
| moyen | Disque plein fantôme | ... |
| moyen | Impossible d'envoyer des fichiers | ... |
| moyen | L'application n'accède plus à sa base | ... |
| moyen | L'intranet affiche la mauvaise page | ... |
| moyen | La base de données ne démarre plus | ... |
| moyen | La sauvegarde ne tourne plus | ... |
| moyen | Le nettoyage automatique ne tourne plus | ... |
| moyen | Le rapport automatique n'est plus généré | ... |
| moyen | Le serveur rame | ... |
| moyen | Le service interne ne démarre plus | ... |
| moyen | Plus d'accès à Internet | ... |
| moyen | apt n'arrive plus à télécharger | ... |
| moyen | apt update est en erreur | ... |
| moyen | sudo ne marche plus pour deploy | ... |
| moyen | « No space left on device » | ... |
| moyen | Le moteur de recherche tombe en boucle | ... |
| moyen | [La boutique conteneurisée est injoignable](docker-port-1.md) | `docker ps`, `docker port`, `-p`, `0.0.0.0` vs `127.0.0.1` |
| moyen | Le site conteneurisé est tombé | ... |
| moyen | Le site est inaccessible depuis le réseau | ... |
| difficile | Activité suspecte sur le serveur | ... |
| difficile | Le conteneur de l'API redémarre en boucle | ... |
| difficile | Erreur de sécurité HTTPS | ... |
| difficile | Incident : le site et l'API sont tombés | ... |
| difficile | L'application ne joint plus sa base | ... |
| difficile | Le worker redémarre en boucle | ... |
| difficile | Too many open files | ... |

## Tâches (19)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | Base de données pour une appli · 🔧 sabotage | ... |
| facile | Compte de déploiement | ... |
| facile | Durcir SSH | ... |
| facile | Planifier une tâche | ... |
| facile | Retrouver un fichier égaré | ... |
| facile | Rotation des logs | ... |
| facile | Régler le fuseau horaire | ... |
| moyen | Accès SSH par clé | ... |
| moyen | Analyser des logs | ... |
| moyen | Conteneuriser un service web | ... |
| moyen | Dossier partagé d'équipe | ... |
| moyen | Exposer une API derrière Nginx · 🔧 sabotage | ... |
| moyen | Héberger deux sites · 🔧 sabotage | ... |
| moyen | Passer le site en HTTPS · 🔧 sabotage | ... |
| moyen | Protéger une page par mot de passe | ... |
| moyen | Restaurer une table supprimée | ... |
| moyen | Script de supervision | ... |
| moyen | Transformer un script en service · 🔧 sabotage | ... |
| difficile | Sauvegardes avec rotation | ... |