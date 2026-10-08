# Le disque est plein

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le disque est plein, plus rien ne s'écrit sur le serveur. »

Objectif : `/` utilisé à moins de 70 %, **sans supprimer** `/var/log/app/app.log` ni arrêter le service `app-logger` (l'application doit continuer à écrire dans son journal).

## Ce qui est cassé

Le journal `/var/log/app/app.log` du service `app-logger` a grossi jusqu'à remplir tout le disque.

## Diagnostic

```bash
df -h /
# /dev/sda1   20G   20G   0   100% /        → disque plein

ls -lh /var/log/app/
# app.log pèse plusieurs Go
```

## Mon erreur : `rm` ne libère pas la place

J'ai supprimé le fichier avec `rm -rf /var/log/app/app.log`. Le disque est resté plein :

```bash
df -h /
# toujours 100 %
```

Le service `app-logger` avait le fichier ouvert. `rm` enlève le nom du fichier, mais Linux garde son contenu sur le disque tant qu'un programme le tient ouvert.

## Notions travaillées

- `df -h` donne le remplissage du disque, `du` trouve quel dossier prend la place
- Supprimer un fichier encore ouvert par un programme **ne libère pas l'espace**
- `truncate -s 0 <fichier>` vide un fichier sans le supprimer : la place est libérée tout de suite et le programme continue d'écrire dedans
- Redémarrer le service lui fait fermer l'ancien fichier (place libérée) et en recréer un nouveau
- Sur un vrai serveur, on vide un journal, on ne le supprime pas : on ne peut pas toujours redémarrer l'application

## Solution

<details>
<summary>Afficher</summary>

La bonne méthode, sans rien supprimer ni redémarrer :

```bash
truncate -s 0 /var/log/app/app.log
df -h /
```

</details>
