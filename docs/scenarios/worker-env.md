# Le worker redémarre en boucle

**Type :** Panne · **Difficulté :** difficile · **Dossier :** `scenarios/worker-env/`

## Énoncé

Ticket : « Depuis la dernière mise en production, le service `worker` ne démarre plus. Il doit répondre sur le port 9000. »

Objectif : `curl http://127.0.0.1:9000` répond « worker ok », le service tourne en tant qu'utilisateur `worker` et démarre au boot.