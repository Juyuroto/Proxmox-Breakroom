# Le site web est en panne

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le site de l'entreprise (`http://localhost`) ne fonctionne plus. »

Objectif : La page d'accueil Nginx s'affiche, et le site revient tout seul après un redémarrage du serveur.

## Ce qui est cassé

Un ancien service resté actif occupe le port 80 au démarrage, ce qui empêche nginx de démarrer.

## Pistes de diagnostic

1. `systemctl status nginx` : lis les dernières lignes de log, l'erreur y est explicite.
2. Trouve quel processus écoute sur le port concerné (`ss -tlnp` ou `lsof -i`).
3. Ce processus n'est pas lancé à la main : cherche ce qui le démarre au boot.

## Notions travaillées

systemctl, journalctl, ss, lsof, ps, ports et bind(), services systemd (enable/disable/mask), conflit de ports

## Solution

<details>
<summary>Afficher la solution</summary>

```bash
ss -tlnp 'sport = :80'                      # python3 http.server sur :80
systemctl status <PID>                      # → legacy-web.service
systemctl disable --now legacy-web.service  # (ou mask)
systemctl restart nginx
curl -I localhost                           # Server: nginx
```

</details>