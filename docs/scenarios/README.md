# Scénarios

Une fiche par scénario résolu (énoncé, cause, diagnostic, notions, solution).

Les scénarios sans lien sont ceux que je n'ai pas encore faits : la fiche est écrite après la résolution.

## Dépannage (39, dont 4 faits)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | 404 sur toutes les pages | ... |
| facile | [Alice ne peut plus se connecter](user-locked-1.md) | `passwd -S`, `passwd -u`, `/etc/shadow` |
| facile | [Alice ne peut plus se connecter](user-locked-2.md) | `ls -l`, `chown`, propriétaire d'un dossier |
| facile | Connexion refusée sur le site | ... |
| facile | La commande report ne marche plus | ... |
| facile | La sauvegarde dit qu'elle tourne déjà | ... |
| facile | [Le disque est plein](disk-full-log-1.md) | `df`, `du`, `lsof +L1`, `truncate`, fichier supprimé mais ouvert |
| facile | Le site de test conteneurisé ne répond plus | ... |
| facile | Le site ne revient pas après un redémarrage | ... |
| facile | [Le site web est en panne](nginx-down-1.md) | `nginx -t`, `error.log`, erreur 403, `chmod 644`, utilisateur `www-data` |
| facile | Le tableau de bord est injoignable | ... |
| facile | Paul n'a pas accès au fichier du service | ... |
| facile | Permission denied dans /tmp | ... |
| facile | Un fichier du site a été supprimé par erreur | ... |
| facile | localhost ne répond plus | ... |
| moyen | 502 Bad Gateway sur l'API | ... |
| moyen | Disque plein fantôme | ... |
| moyen | Impossible d'envoyer des fichiers | ... |
| moyen | L'application n'accède plus à sa base | ... |
| moyen | L'intranet affiche la mauvaise page | ... |
| moyen | La base de données ne démarre plus | ... |
| moyen | [La boutique conteneurisée est injoignable](docker-port-1.md) | `docker ps`, `docker port`, `-p`, `0.0.0.0` vs `127.0.0.1` |
| moyen | La sauvegarde ne tourne plus | ... |
| moyen | Le moteur de recherche tombe en boucle | ... |
| moyen | Le nettoyage automatique ne tourne plus | ... |
| moyen | Le rapport automatique n'est plus généré | ... |
| moyen | Le serveur rame | ... |
| moyen | Le service interne ne démarre plus | ... |
| moyen | Le site conteneurisé est tombé | ... |
| moyen | Plus d'accès à Internet | ... |
| moyen | apt n'arrive plus à télécharger | ... |
| moyen | apt update est en erreur | ... |
| moyen | sudo ne marche plus pour deploy | ... |
| moyen | « No space left on device » | ... |
| difficile | Activité suspecte sur le serveur | ... |
| difficile | Erreur de sécurité HTTPS | ... |
| difficile | Incident : le site et l'API sont tombés | ... |
| difficile | Le conteneur de l'API redémarre en boucle | ... |
| difficile | Le worker redémarre en boucle | ... |
| difficile | Too many open files | ... |

## Construction (33, dont 0 fait)

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | Base de données pour une appli | ... |
| facile | Compte de déploiement | ... |
| facile | Créer un compte utilisateur | ... |
| facile | Donner un nom local au site | ... |
| facile | Durcir SSH | ... |
| facile | Lancer un serveur web dans un conteneur | ... |
| facile | Mettre en ligne une page d'accueil | ... |
| facile | Mettre un dossier sous Git | ... |
| facile | Planifier une tâche | ... |
| facile | Publier une version avec une branche et un tag | ... |
| facile | Restreindre l'accès à un fichier | ... |
| facile | Retrouver un fichier égaré | ... |
| facile | Rotation des logs | ... |
| facile | Régler le fuseau horaire | ... |
| facile | Sauvegarder un dossier dans une archive | ... |
| moyen | Accès SSH par clé | ... |
| moyen | Analyser des logs | ... |
| moyen | Bloquer les mots de passe avec un hook pre-commit | ... |
| moyen | Conteneuriser un service web | ... |
| moyen | Conteneuriser une application avec un Dockerfile | ... |
| moyen | Dossier partagé d'équipe | ... |
| moyen | Exposer une API derrière Nginx | ... |
| moyen | Héberger deux sites | ... |
| moyen | Passer le site en HTTPS | ... |
| moyen | Planifier un script avec un timer systemd | ... |
| moyen | Protéger une page par mot de passe | ... |
| moyen | Relier deux conteneurs par un réseau privé | ... |
| moyen | Restaurer une table supprimée | ... |
| moyen | Script de supervision | ... |
| moyen | Transformer un script en service | ... |
| difficile | Déployer un site Nginx avec un playbook Ansible | ... |
| difficile | Sauvegardes avec rotation | ... |
| difficile | Stack web + base de données avec Docker Compose | ... |
