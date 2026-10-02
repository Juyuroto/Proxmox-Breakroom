# L'intranet affiche la mauvaise page

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/nginx-vhost-broken/`

## Énoncé

Ticket : « Après une mise à jour, l'intranet (`http://localhost`) n'affiche plus la page d'accueil de l'intranet. »

Objectif : `curl http://localhost` affiche « Bienvenue sur l'intranet » (site défini dans `/etc/nginx/sites-available/intranet`), et Nginx démarre au boot.