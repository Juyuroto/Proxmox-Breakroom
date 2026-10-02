# Exposer une API derrière Nginx

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-reverse-proxy/`

## Énoncé

Une API tourne en local : `curl 127.0.0.1:5000/health`.

Objectif : la publier via Nginx sous `/api/`. `curl http://localhost/api/health` doit renvoyer `{"status": "ok"}`, et la page d'accueil Nginx doit rester accessible.