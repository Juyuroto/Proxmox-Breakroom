# L'application n'accède plus à sa base

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/pg-access/`

## Énoncé

Ticket : « L'application n'arrive plus à se connecter à sa base PostgreSQL. Ses paramètres de connexion sont dans `/etc/app/db.env`. »

Objectif : la connexion fonctionne avec ces paramètres (`psql -h 127.0.0.1 -U app -d app`), sans modifier `/etc/app/db.env` et sans méthode `trust`.