# Le nettoyage automatique ne tourne plus

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/timer-broken/`

## Énoncé

Ticket : « Le timer systemd `cleanup` doit lancer `/usr/local/bin/cleanup` chaque minute. Il ne se passe plus rien. »

Objectif : le nettoyage tourne de nouveau chaque minute via le timer (la vérification prend environ 70 s).