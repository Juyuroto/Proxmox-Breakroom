# Alice ne peut plus se connecter

**Type :** Panne · **Difficulté :** facile · **Variante :** 2/4

## Énoncé

Ticket : « Le compte de alice ne fonctionne plus depuis ce matin. »

Objectif : le compte alice est de nouveau utilisable normalement.

## Ce qui est cassé

Le compte de alice a expiré : sa date d'expiration est fixée au 1er janvier 1970 (jour 0 de l'époque Unix), donc déjà dépassée. Le mot de passe, le shell et le dossier personnel sont intacts, ce qui explique le « il marchait hier ».

## Diagnostic

```bash
passwd -S alice
# alice P ...   → le mot de passe n'est pas verrouillé, ce n'est pas la cause
chage -l alice
# Account expires : Jan 01, 1970   → expiré depuis longtemps
```

## Notions travaillées

- `passwd -S` : écarter un verrouillage du mot de passe (L) avant de chercher ailleurs
- `chage -l` : lire les dates d'un compte (dernier changement, expiration du mot de passe, **expiration du compte**)
- Ne pas confondre expiration du mot de passe (`Password expires`) et expiration du compte (`Account expires`)
- `chage -E` : fixer ou retirer la date d'expiration (`-1` = jamais)

## Solution

<details>
<summary>Afficher</summary>

```bash
chage -E -1 alice
```

Équivalent : `usermod -e "" alice`. Vérification : `chage -l alice` affiche `Account expires : never`.

</details>
