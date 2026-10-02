# Compte de déploiement

**Type :** Tâche · **Difficulté :** facile · **Dossier :** `scenarios/tache-sudo-user/`

## Énoncé

Objectif : créer l'utilisateur `deploy` (shell bash, dossier `/home/deploy`), membre du groupe `devops`. Il doit pouvoir lancer `sudo systemctl restart nginx` sans mot de passe, et **rien d'autre** en root.