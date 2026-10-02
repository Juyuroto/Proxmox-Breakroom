# Alice ne peut plus se connecter

**Type :** Panne · **Difficulté :** facile

## Énoncé

Le dossier `/home/alice` appartient à root (droits `700`) : alice ne peut plus y entrer.

## Ce qui est cassé

Alice ne peut pas accéder à son répertoire personnel

## Diagnostic

```bash
ls -ld /home/alice
# drwx------ root root ... /home/alice
```

## Notions travaillées

- Lire les droits et le propriétaire d'un fichier avec `ls -l` (`drwx------ root root`)
- Changer le propriétaire avec `chown -R utilisateur:groupe`
- Un utilisateur doit être propriétaire de son dossier personnel pour pouvoir s'y connecter

## Solution

<details>
<summary>Afficher</summary>

```bash
chown -R alice:alice /home/alice
```

</details>