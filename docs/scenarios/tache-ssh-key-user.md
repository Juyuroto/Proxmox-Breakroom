# Accès SSH par clé

**Type :** Tâche · **Difficulté :** moyen · **Dossier :** `scenarios/tache-ssh-key-user/`

## Énoncé

Une paire de clés a été générée : `/root/ops_key` (privée) et `/root/ops_key.pub` (publique).

Objectif : crée l'utilisateur `ops` et autorise-le à se connecter en SSH avec cette clé. Test : `ssh -i /root/ops_key ops@localhost`