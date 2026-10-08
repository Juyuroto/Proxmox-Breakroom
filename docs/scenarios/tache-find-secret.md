# Retrouver un fichier égaré

**Type :** Tâche · **Difficulté :** facile

## Énoncé

Ticket : « Un fichier contenant le jeton de production (une ligne `API_TOKEN=prod-...`) a été égaré quelque part dans `/srv`, `/opt` ou `/var`. Attention, il existe des copies de test. »

Objectif : écrire le chemin complet du bon fichier dans `/root/reponse.txt`.

## Démarche

J'ai cherché le motif `API_TOKEN` récursivement :

```bash
grep -rl 'API_TOKEN=prod-' /srv /opt /var
# /srv/app/config/settings.bak
```

- `-r` : parcourt récursivement tous les fichiers du dossier.
- `-l` : n'affiche que le NOM du fichier (pas la ligne), et on filtre direct sur « prod- »
- La sortie est au format `chemin:ligne` : le fichier recherché est la partie **avant** le `:`.

Le repère décisif est le préfixe du jeton : **`prod-`** = le vrai, **`test-`** = les leurres. Comme plusieurs fichiers contiennent `API_TOKEN`, c'est la valeur `prod-...` qui tranche.

## Notions travaillées

- `grep -r` : recherche récursive dans une arborescence
- `grep -l` : affiche seulement le **nom des fichiers** qui correspondent
- Sortie `chemin:ligne` de `grep` : le chemin est avant le `:` (sinon `cut -d: -f1`)
- Distinguer le vrai du leurre par un motif précis (`prod-` vs `test-`) plutôt que par le seul nom `API_TOKEN`
- Chercher dans tous les emplacements possibles (`/srv /opt /var`) donnés par l'énoncé

## Solution

<details>
<summary>Afficher</summary>

```bash
grep -rl 'API_TOKEN=prod-' /srv /opt /var | head -1 > /root/reponse.txt
```

`-l` donne le chemin, le filtre `prod-` ignore les leurres, `head -1` garde le premier si jamais il y en avait plusieurs.

</details>
