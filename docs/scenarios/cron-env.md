# Le rapport automatique n'est plus généré

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/cron-env/`

## Énoncé

Ticket : « La tâche cron de root doit produire un rapport dans `/var/reports/` chaque minute. Rien n'arrive, alors que la commande fonctionne quand on la lance à la main. »

Objectif : un nouveau rapport apparaît dans `/var/reports/` chaque minute (la vérification prend environ 70 s).