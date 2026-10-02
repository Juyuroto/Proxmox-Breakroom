# Héberger deux sites

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-nginx-vhosts/`

## Énoncé

Objectif : Nginx héberge deux sites sur le port 80 :
- `site1.lab` affiche « site1 » (fichiers dans `/var/www/site1`) ;
- `site2.lab` affiche « site2 » (fichiers dans `/var/www/site2`).

Tout autre nom (ex. `localhost`) doit toujours afficher la page Nginx par défaut.