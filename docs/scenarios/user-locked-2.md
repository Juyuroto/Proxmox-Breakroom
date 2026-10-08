# Alice ne peut plus se connecter

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le compte de alice ne fonctionne plus depuis ce matin. »

Objectif: Le compte alice est de nouveau utilisable normalement.

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