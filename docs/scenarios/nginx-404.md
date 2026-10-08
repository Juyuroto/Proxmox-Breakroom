# 404 sur toutes les pages

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le site renvoie "404 Not Found" sur toutes les pages depuis ce matin. Les fichiers du site n'ont pourtant pas bougé. »

Objectif : `curl http://localhost` affiche de nouveau la page d'accueil de Nginx (code 200).

## Ce qui est cassé

Une faute de frappe dans la directive `root` de `/etc/nginx/sites-available/default` : `root /var/www/htlm;` au lieu de `root /var/www/html;`. Nginx cherche ses pages dans un dossier qui n'existe pas.

## Diagnostic

```bash
curl -I http://localhost
# HTTP/1.1 404 Not Found      → Nginx tourne et répond, le problème est dans ce qu'il sert

ls /var/www/
# html                        → le seul dossier qui existe

grep -nE 'root|index' /etc/nginx/sites-enabled/default
# 41:    root /var/www/htlm;  → « htlm » : le l et le m sont inversés
```

## Mon erreur : du 404 au 403

En corrigeant, j'ai effacé `htlm` sans réécrire `html` : la ligne est devenue `root /var/www/;`.

```bash
curl -I http://localhost
# HTTP/1.1 403 Forbidden

tail -3 /var/log/nginx/error.log
# directory index of "/var/www/" is forbidden   → le chemin que Nginx utilise vraiment

ls -la /var/www/html/
# -rw-r--r-- 1 root root 615 index.nginx-debian.html   → la page est bien là et lisible
```

Le dossier `/var/www/` existe, mais il ne contient pas de page d'accueil : Nginx refuse d'afficher le contenu du dossier.

| Ligne `root` | Ce que Nginx trouve | Réponse |
|---|---|---|
| `/var/www/htlm` | rien, le dossier n'existe pas | 404 |
| `/var/www/` | un dossier sans page d'accueil | 403 |
| `/var/www/html` | `index.nginx-debian.html` | 200 |

## Notions travaillées

- La directive `root` indique le dossier où Nginx prend ses pages ; `index` donne les noms de fichiers à essayer
- 404 = « je ne trouve pas », 403 = « je trouve, mais je ne peux pas le montrer »
- `error.log` donne le chemin exact que Nginx essaie d'ouvrir : à regarder en premier sur un 403 ou un 404
- `nginx -t` vérifie la syntaxe, pas l'existence des dossiers : une faute dans un chemin passe sans erreur
- Après une modification, `systemctl reload nginx`, sinon Nginx garde l'ancienne configuration
- Relire la ligne modifiée avant de recharger

## Solution

<details>
<summary>Afficher</summary>

Dans `/etc/nginx/sites-available/default`, ligne 41 :

```
root /var/www/html;
```

```bash
nginx -t
systemctl reload nginx
curl -I http://localhost     # HTTP/1.1 200 OK
```

</details>
