# Le timer ne met plus à jour le log de santé

**Type :** Panne · **Difficulté :** facile · **Variante :** 2/3

## Énoncé

Ticket : « Un timer systemd, `sante.timer`, doit lancer toutes les 10 secondes `sante.service`, qui ajoute une ligne dans `/var/log/sante.log`. Le fichier ne bouge plus. »

Objectif : le log de santé est de nouveau mis à jour toutes les 10 secondes, et ça doit rester vrai après un redémarrage du serveur.

## Ce qui est cassé

Le timer est correct : il est actif, il se déclenche à l'heure prévue et il lance bien `sante.service`. C'est le service qui échoue : le script `/usr/local/bin/sante.sh` n'a pas le droit d'exécution (`-rw-r--r--`), donc systemd ne peut pas le lancer.

## Diagnostic

```bash
systemctl status sante.timer
# Active: active (waiting) ... → le timer tourne
# Triggers: sante.service → il vise le bon service
systemctl status sante.service
journalctl -u sante.service -n 20
# Failed at step EXEC spawning /usr/local/bin/sante.sh: Permission denied
ls -l /usr/local/bin/sante.sh
# -rw-r--r-- 1 root root ... sante.sh → pas de « x » : non exécutable
```

Un timer qui semble sain ne prouve rien : il faut lire l'état du **service** qu'il déclenche.

## Notions travaillées

- Un timer ne fait que déclencher un service : si le fichier de log ne bouge pas, vérifier les deux, `sante.timer` puis `sante.service`
- `systemctl status` du timer (`Trigger`, `Triggers`) pour écarter une faute de calendrier ou de nom d'unité
- `journalctl -u <service>` : lire l'erreur exacte (`Failed at step EXEC ... Permission denied`)
- Le bit d'exécution : un script lancé directement par systemd doit être exécutable (`ls -l`, `chmod +x`)

## Solution

<details>
<summary>Afficher</summary>

```bash
chmod +x /usr/local/bin/sante.sh
```

Vérification : attendre une dizaine de secondes, puis `tail /var/log/sante.log` doit montrer une nouvelle ligne et `systemctl status sante.service` ne doit plus signaler d'échec. Les droits d'un fichier survivent au redémarrage.

</details>
