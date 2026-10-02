# Analyser des logs

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-log-analysis/`

## Énoncé

Le fichier `/root/analyse/access.log` contient des logs Nginx d'une attaque supposée.

Objectif : écris dans `/root/reponse.txt`
- ligne 1 : l'adresse IP qui a fait le plus de requêtes ;
- ligne 2 : le nombre total de réponses avec le code HTTP 500.