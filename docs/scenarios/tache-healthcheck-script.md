# Script de supervision

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-healthcheck-script/`

## Énoncé

Objectif : écris le script exécutable `/usr/local/bin/healthcheck` qui :
- vérifie que le site répond en HTTP sur `http://localhost` ;
- vérifie que PostgreSQL accepte une requête ;
- affiche l'état de chacun et se termine avec le code **0** si tout va bien, **1** sinon.