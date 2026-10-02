# Documentation

- [Scénarios](scenarios/README.md) : une fiche par scénario (énoncé, causes, pistes, notions, solution)
- [Template](template.md) : modèle vierge pour rédiger une nouvelle fiche

Chaque fiche est rédigée à la main, après avoir résolu le scénario.

## Ajouter une fiche

1. Copier le template :
```bash
   cp docs/template.md docs/scenarios/<nom>.md
```
2. Remplir chaque section à partir de ce que j'ai vécu pendant le scénario :
   - **Énoncé** : le ticket affiché sur le site
   - **Ce qui est cassé** : la cause que j'ai trouvée
   - **Pistes de diagnostic** : les commandes qui m'ont mis sur la piste
   - **Solution** : les commandes que j'ai utilisées pour réparer
   - **Notions travaillées** : ce que j'ai appris
3. Ajouter la ligne du scénario dans le tableau de [`scenarios/README.md`](scenarios/README.md).