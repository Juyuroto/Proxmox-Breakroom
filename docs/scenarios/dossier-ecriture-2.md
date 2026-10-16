# Impossible de créer des fichiers dans un dossier

**Type :** Panne · **Difficulté :** facile · **Variante :** 1/3

## Énoncé

Ticket : « L'utilisateur `admin` ne peut plus rien créer dans son dossier de travail `/home/admin/projets` : ni fichier, ni dossier. Il jure que les droits sont bons. »

Objectif : `admin` peut créer des fichiers et des dossiers dans `/home/admin/projets`, et ça doit rester vrai après un redémarrage du serveur.

## Ce qui est cassé

Le dossier `projets` porte l'attribut **immuable** (`i`). Le propriétaire et les droits sont corrects (`admin`, `rwx`), mais le noyau refuse toute création, modification ou suppression dans un dossier immuable, même pour root. C'est pour ça que « les droits sont bons » et que ça échoue quand même.

## Diagnostic

```bash
sudo -u admin touch /home/admin/projets/test

ls -la /home/
# drwxr-xr-x admin admin ... projets
lsattr -d /home/admin/projets
# ----i---------e------- /home/admin/projets → le « i » = immuable
```

Le message « Operation not permitted » (et non « Permission denied ») est l'indice qui oriente vers un attribut plutôt que vers les droits classiques.

## Notions travaillées

- Lire le message d'erreur exact : `Permission denied` (droits ou propriétaire) contre `Operation not permitted` (attribut) contre `Read-only file system` (montage)
- `ls -ld` : écarter d'abord le propriétaire et les droits
- `lsattr -d` : lire les attributs d'un dossier (`-d` pour le dossier lui-même, pas son contenu)
- `chattr -i` / `chattr +i` : retirer / poser l'attribut immuable
- Les trois causes possibles d'un refus d'écriture : droits/propriétaire, attribut immuable, montage en lecture seule

## Solution

<details>
<summary>Afficher</summary>

```bash
chattr -i /home/admin/projets
```

L'attribut est stocké dans le système de fichiers : la correction survit au redémarrage. Vérification : `lsattr -d /home/admin/projets` ne montre plus le `i`, puis `sudo -u admin touch /home/admin/projets/test`.

</details>
