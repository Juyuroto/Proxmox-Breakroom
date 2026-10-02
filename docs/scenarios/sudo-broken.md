# sudo ne marche plus pour deploy

**Type :** Panne · **Difficulté :** moyen · **Dossier :** `scenarios/sudo-broken/`

## Énoncé

Ticket : « Le compte `deploy` n'arrive plus à redémarrer Nginx avec sudo, le déploiement est bloqué. »

Objectif : `su - deploy -c "sudo -n systemctl restart nginx"` fonctionne, sans donner d'autres droits root à deploy.