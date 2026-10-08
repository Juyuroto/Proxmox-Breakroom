# Analyser des logs

**Type :** Tâche · **Difficulté :** moyen

## Énoncé

Ticket : « Le fichier `/root/analyse/access.log` contient des logs Nginx d'une attaque supposée. »

Objectif : écrire dans `/root/reponse.txt`
- ligne 1 : l'adresse IP qui a fait le plus de requêtes ;
- ligne 2 : le nombre total de réponses avec le code HTTP 500.

## Démarche

D'abord comprendre le format : une ligne = une requête, les champs séparés par des espaces (Combined Log Format de Nginx).

```bash
head -1 /root/analyse/access.log
# 203.0.113.7 - - [30/Sep/2026:00:00:04 +0000] "GET /login HTTP/1.1" 200 4521 "-" "Mozilla/5.0"
#     $1                                        $6     $7            $9
```

L'IP est le **1er champ**, le code HTTP renvoyé est le **9e champ**.

**Ligne 1 — l'IP la plus active :**

Je l'ai extraite **par motif** plutôt que par position de colonne, avec une regex qui reconnaît une adresse IPv4 :

```bash
grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' analyse/access.log | sort | uniq -c | sort -nr | head -1
#        └─ un groupe « nombre + point » ×3, puis un dernier nombre
# 720 203.0.113.7     ← le compte, puis l'IP gagnante
```

- `-E` : regex étendue (pour `(...)` et `{3}`) ; `-o` : n'affiche **que** le texte qui correspond, pas la ligne entière.
- `([0-9]{1,3}\.){3}[0-9]{1,3}` : trois fois « 1 à 3 chiffres suivis d'un point », puis un dernier bloc de 1 à 3 chiffres.
- `uniq -c` ne compte que des lignes **voisines** identiques → d'où le `sort` **avant** ; `sort -nr` classe du plus grand au plus petit, `head -1` garde le gagnant.

**Ligne 2 — le nombre de réponses 500 :**

```bash
awk '$9 == 500' /root/analyse/access.log | wc -l
#   ← ne garde que les lignes dont le 9e champ vaut exactement 500
```

## Le piège

`grep 500 access.log | wc -l` donne un **mauvais** résultat : « 500 » apparaît aussi dans la taille des réponses (`4500`, `500`…), dans l'horodatage, dans une URL… `grep` compte alors bien plus de lignes que de vraies réponses 500. Il faut viser **la bonne colonne**, pas le texte brut — d'où `awk '$9 == 500'` (comparaison exacte sur le champ), et non une recherche de motif.

## Notions travaillées

- `grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}'` : extraire une IP **par motif** (`-E` regex étendue, `-o` n'affiche que ce qui correspond)
- Alternative par colonne : `awk '{print $N}'` extrait la Nᵉ colonne (séparateur = espaces)
- Format Nginx : IP en `$1`, code HTTP en `$9`
- Extraire par motif (grep) ou par colonne (awk) : deux façons valables ; le motif ne dépend pas de la position, la colonne est insensible au reste de la ligne
- L'idiome `sort | uniq -c | sort -rn` : compter et classer les occurrences
- `uniq -c` exige un `sort` juste avant (il ne regroupe que les lignes voisines)
- `awk '$9 == 500'` compare un **champ**, là où `grep 500` attraperait aussi tailles, dates et URL
- `wc -l` pour compter les lignes

## Solution

<details>
<summary>Afficher</summary>

```bash
L=/root/analyse/access.log
awk '{print $1}' "$L" | sort | uniq -c | sort -rn | awk 'NR==1 {print $2}' > /root/reponse.txt
awk '$9 == 500' "$L" | wc -l >> /root/reponse.txt
```

`NR==1 {print $2}` reprend juste l'IP (2e colonne de la sortie de `uniq -c`) de la ligne de tête. Le `>>` ajoute le compte des 500 en deuxième ligne.

</details>