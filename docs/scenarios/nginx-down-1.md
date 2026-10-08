# Le site web est en panne

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le site de l'entreprise (`http://localhost`) ne fonctionne plus. »

Objectif : La page d'accueil Nginx s'affiche, et le site revient tout seul après un redémarrage du serveur.

## Ce qui est cassé

La page d'accueil `/var/www/html/index.nginx-debian.html` n'a plus aucun droit (`----------`) : Nginx ne peut plus la lire et renvoie une erreur **403 Forbidden**.

## Diagnostic

```bash
systemctl status nginx
nginx -t
ss -ltnp

tail /var/log/nginx/access.log
# "GET / HTTP/1.1" 403        → accès refusé

tail /var/log/nginx/error.log
# open() "/var/www/html/index.nginx-debian.html" failed (13: Permission denied)

ls -la /var/www/html/
# ---------- 1 root root 615 index.nginx-debian.html   → aucun droit
```

## Notions travaillées

- Éliminer les causes une par une : service, config, port, puis logs
- `error.log` donne la cause exacte, `access.log` le code HTTP renvoyé
- Erreur 403 + `Permission denied` = problème de droits sur les fichiers
- Nginx tourne avec l'utilisateur `www-data` : le fichier doit être lisible par « les autres » (`r--` en dernière position)
- `chmod 700` ne suffit pas : seul root peut lire ; il faut `644` (`rw-r--r--`)

## Solution

<details>
<summary>Afficher</summary>

```bash
chmod 644 /var/www/html/index.nginx-debian.html
curl -I http://localhost     # HTTP/1.1 200 OK
```

</details>