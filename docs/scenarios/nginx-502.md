# 502 Bad Gateway sur l'API

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/nginx-502/`

## Énoncé

Ticket : « L'API publiée par Nginx sur `/api/` renvoie 502 Bad Gateway. »

Objectif : `curl http://localhost/api/health` renvoie `{"status": "ok"}`, et tout redémarre seul après un reboot.