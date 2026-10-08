# Scénarios

Une fiche par scénario résolu (énoncé, cause, diagnostic, notions, solution).

Seuls les scénarios que j'ai résolus apparaissent ici : la fiche est écrite après la résolution.

## Dépannage

| Difficulté | Scénario | Variante | Notions |
|---|---|---|---|
| facile | [404 sur toutes les pages](nginx-404.md) | — | `root`, `error.log`, 404 contre 403, `nginx -t`, `reload` |
| facile | [Alice ne peut plus se connecter](user-locked-1.md) | 1/4 | `passwd -S`, `passwd -u`, `/etc/shadow` |
| facile | [Alice ne peut plus se connecter](user-locked-2.md) | 4/4 | `ls -l`, `chown`, propriétaire d'un dossier |
| facile | [Le disque est plein](disk-full-log.md) | — | `df`, `du`, `lsof +L1`, `truncate`, fichier supprimé mais ouvert |
| facile | [Le site web est en panne](nginx-down-1.md) | 3/3 | `nginx -t`, `error.log`, erreur 403, `chmod 644`, utilisateur `www-data` |
| moyen | [La boutique conteneurisée est injoignable](docker-port-1.md) | 4/4 | `docker ps`, `docker port`, `-p`, `0.0.0.0` vs `127.0.0.1` |
disk-full-log-1