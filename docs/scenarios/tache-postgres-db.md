# Base de données pour une appli

**Type :** Tâche · **Difficulté :** facile · **Dossier :** `scenarios/tache-postgres-db/`

## Énoncé

Objectif : créer une base `shop` appartenant à un utilisateur `shop` (mot de passe `Sh0pPass`), qui doit pouvoir s'y connecter en TCP : `psql -h 127.0.0.1 -U shop -d shop`. L'utilisateur ne doit pas être superuser.