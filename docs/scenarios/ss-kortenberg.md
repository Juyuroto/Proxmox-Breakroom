# Impossible de créer des fichiers dans un dossier

**Type :** Panne · **Difficulté :** facile · **Variante :** 3/3

## Énoncé

Ticket : « L'utilisateur `admin` ne peut plus rien créer dans son dossier de travail `/home/admin/projets` : ni fichier, ni dossier. Il jure que les droits sont bons. »

Objectif : `admin` peut créer des fichiers et des dossiers dans `/home/admin/projets`, et ça doit rester vrai après un redémarrage du serveur.

## Ce qui est cassé

Le dossier `projets` appartient à `root:root` : `admin` n'est plus propriétaire et les droits `755` ne lui donnent que la lecture.

## Diagnostic

```bash
sudo -u admin touch /home/admin/projets/test
# touch: cannot touch ...: Permission denied
ls -ld /home/admin/projets
# drwxr-xr-x root root ... /home/admin/projets
```

Les deux autres variantes se distinguent avec `lsattr -d` (attribut `i`) et `findmnt` (montage en lecture seule).

## Notions travaillées

- Reproduire l'erreur avec `sudo -u <user> touch` et lire le message exact
- Lire le propriétaire et les droits avec `ls -ld`
- Changer le propriétaire avec `chown`
- Trois causes possibles d'un refus d'écriture : droits/propriétaire, attribut immuable (`chattr`), montage en lecture seule (`fstab`)

## Solution

<details>
<summary>Afficher</summary>

```bash
chown admin: /home/admin/projets
```

</details>
