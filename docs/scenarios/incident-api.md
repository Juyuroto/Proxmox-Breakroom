# Incident : le site et l'API sont tombés

**Type :** Panne · **Difficulté :** difficile · **Dossier :** `scenarios/incident-api/`

## Énoncé

Ticket (urgent) : « Après la maintenance de cette nuit, plus rien ne répond : ni le site, ni l'API. »

Objectif : `http://localhost` affiche la page Nginx, `http://localhost/api/health` renvoie `{"status": "ok"}`, et tout redémarre seul après un reboot.