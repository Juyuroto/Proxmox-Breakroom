# Alice ne peut plus se connecter

**Type :** Panne · **Difficulté :** facile

## Énoncé

Ticket : « Le compte de alice ne fonctionne plus depuis ce matin. »

Objectif: Le compte alice est de nouveau utilisable normalement.

## Ce qui est cassé

Le mot de passe de alice est verrouillé.

## Diagnostic

```bash
passwd -S alice
# alice L ...   → L = verrouillé (P = normal)
```

## Notions travaillées

- `passwd -S` : lire l'état d'un compte (L, P, NP)
- `passwd -l` / `passwd -u` : verrouiller / déverrouiller un mot de passe
- `/etc/shadow` : un `!` devant le hash = mot de passe verrouillé

## Solution

<details>
<summary>Afficher</summary>

```bash
passwd -u alice
```

</details>