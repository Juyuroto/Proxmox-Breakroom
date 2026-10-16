# Connexion refusée sur le site

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Depuis la modification de la configuration hier, `http://localhost` répond "connexion refusée". Pourtant Nginx tourne, on a vérifié. »

Objectif : `curl http://localhost` (port 80) affiche la page d'accueil de Nginx.

## Ce qui est cassé

Nginx fonctionne, mais la directive `listen` du site par défaut a été changée de `80` en `8080`. Il n'écoute donc plus sur le port 80 : le service est « actif » et pourtant la connexion est refusée, parce que personne n'attend sur le port demandé.

## Diagnostic

```bash
curl http://localhost
# curl: (7) Failed to connect to localhost port 80: Connection refused
systemctl status nginx
# active (running) → le service tourne, ce n'est pas lui le problème
ss -ltnp | grep nginx
# LISTEN ... *:8080 ... nginx → il écoute sur 8080, pas sur 80
grep -rn listen /etc/nginx/sites-enabled/
# listen 8080 default_server;
```

## Notions travaillées

- « Connexion refusée » ne veut pas dire « service arrêté » : il peut tourner sur un autre port
- `ss -ltnp` : voir quel processus écoute sur quel port
- La directive `listen` d'un bloc `server` fixe le port d'écoute de Nginx
- `nginx -t` pour vérifier la syntaxe, puis `systemctl reload nginx` pour appliquer

## Solution

<details>
<summary>Afficher</summary>

Dans `/etc/nginx/sites-available/default`, remettre le port 80 :

```nginx
server {
        listen 80 default_server;
        listen [::]:80 default_server;
```

Puis :

```bash
nginx -t && systemctl reload nginx
curl http://localhost
```

</details>
