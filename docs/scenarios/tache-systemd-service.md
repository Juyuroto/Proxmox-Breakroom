# Transformer un script en service

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-systemd-service/`

## Énoncé

Le script `/opt/clock/clock.sh` écrit l'heure toutes les 5 s dans `/var/log/clock/clock.log`.

Objectif : en faire un service systemd `clock` qui démarre au boot, redémarre tout seul s'il plante, et tourne avec un utilisateur système `clock` (pas root).