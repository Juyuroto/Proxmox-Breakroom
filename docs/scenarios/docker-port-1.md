# La boutique conteneurisée est injoignable

**Type :** Panne · **Difficulté :** moyen

## Énoncé

Ticket : « La boutique en ligne tourne dans un conteneur Docker nommé `web` sur ce serveur. Depuis ce matin, plus personne n'arrive à l'ouvrir sur le port 8080, alors que le conteneur est bien démarré. »

Objectif : `curl http://<IP du serveur>:8080` (l'adresse réseau du serveur, pas seulement `localhost`) affiche la page « Boutique en ligne ». Le conteneur s'appelle toujours `web`, utilise l'image `nginx`, sert toujours le contenu de `/srv/boutique` et redémarre tout seul après un reboot.

## Ce qui est cassé

Le port du conteneur est publié **uniquement sur `127.0.0.1`** (`-p 127.0.0.1:8080:80`) : la boutique répond depuis le serveur lui-même, mais pas depuis le réseau.

## Diagnostic

```bash
netstat -tuln
# tcp  0  0 127.0.0.1:8080   0.0.0.0:*   LISTEN   → écoute seulement en local
# tcp  0  0 0.0.0.0:80       0.0.0.0:*   LISTEN   → à comparer : toutes les interfaces
# udp  0  0 192.168.20.23:68 0.0.0.0:*            → client DHCP, sans rapport

docker ps
# PORTS : 127.0.0.1:8080->80/tcp

docker port web
# 80/tcp -> 127.0.0.1:8080

# Avant de recréer le conteneur, noter comment il a été lancé :
docker inspect web --format '{{json .Mounts}}'
# "Source":"/srv/boutique","Destination":"/usr/share/nginx/html","Mode":"ro"

docker inspect web --format '{{.HostConfig.RestartPolicy.Name}}'
# unless-stopped
```

## Notions travaillées

- Dans `netstat -tuln` / `ss -ltnp`, l'adresse devant le port dit **qui peut se connecter** : `0.0.0.0` = tout le réseau, `127.0.0.1` = la machine elle-même
- Le port 68 en UDP est le client DHCP : présent sur toute machine en DHCP, à ignorer
- `docker ps` (colonne PORTS) et `docker port <conteneur>` montrent les ports publiés
- Format de l'option : `-p <adresse>:<port du serveur>:<port du conteneur>` ; sans adresse, Docker publie sur toutes les interfaces
- On ne modifie pas les ports d'un conteneur existant : il faut le supprimer et le recréer
- `docker inspect` permet de retrouver les options d'origine (volume, politique de redémarrage) pour recréer le conteneur à l'identique
- Un dossier monté avec `-v` est sur le serveur : supprimer le conteneur ne le fait pas disparaître

## Solution

<details>
<summary>Afficher</summary>

```bash
docker rm -f web
docker run -d --name web --restart unless-stopped \
  -p 8080:80 \
  -v /srv/boutique:/usr/share/nginx/html:ro \
  nginx

docker ps                          # PORTS : 0.0.0.0:8080->80/tcp
curl http://192.168.20.23:8080     # <h1>Boutique en ligne</h1>
```

</details>
