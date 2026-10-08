# Scénarios

Une fiche par scénario résolu (énoncé, cause, diagnostic, notions, solution).

Seuls les scénarios que j'ai résolus apparaissent ici : la fiche est écrite après la résolution.

## Dépannage

| Difficulté | Scénario | Notions |
|---|---|---|
| facile | [Alice ne peut plus se connecter](user-locked-1.md) | `passwd -S`, `passwd -u`, `/etc/shadow` |
| facile | [Alice ne peut plus se connecter](user-locked-2.md) | `ls -l`, `chown`, propriétaire d'un dossier |
| facile | [Le disque est plein](disk-full-log-1.md) | `df`, `du`, `lsof +L1`, `truncate`, fichier supprimé mais ouvert |
| facile | [Le site web est en panne](nginx-down-1.md) | `nginx -t`, `error.log`, erreur 403, `chmod 644`, utilisateur `www-data` |
| moyen | [La boutique conteneurisée est injoignable](docker-port-1.md) | `docker ps`, `docker port`, `-p`, `0.0.0.0` vs `127.0.0.1` |
