# Too many open files

**Type :** Panne · **Difficulté :** difficile · **Dossier :** `scenarios/fd-limit/`

## Énoncé

Ticket : « Le service `fdapp` plante au démarrage avec "Too many open files". Il doit répondre sur le port 9100. »

Objectif : `curl http://127.0.0.1:9100` répond « fd ok », et le service démarre au boot.