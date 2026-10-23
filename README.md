# ⚫⚪ Othello : Joueur vs IA

**Affrontez une intelligence artificielle à Othello, directement dans votre terminal.**

Un jeu d'Othello (Reversi) 100 % Python, jouable contre une IA qui réfléchit plusieurs coups à l'avance, adapte sa stratégie selon l'avancement de la partie… et ne vous fera pas de cadeau. 😈

---

## ✨ Ce que vous allez trouver

- 🎮 **Une partie complète** : humain contre IA, vous choisissez qui commence
- 🔴 **Coups valides en surbrillance** : plus besoin de deviner où jouer
- 🧠 **Une IA qui s'adapte** : prudente à l'ouverture, stratégique en milieu de partie, impitoyable en fin de partie
- ⏱️ **Chronomètre intégré** : comparez votre temps de réflexion à celui de l'IA
- 🔁 **Règles respectées** : retournement des pions, passage de tour, détection de fin de partie

## 🚀 Lancer une partie

Ouvrez `Othello.ipynb` dans Jupyter, exécutez toutes les cellules, et c'est parti !

## 🕹️ Comment jouer

Les coups se saisissent sous la forme **ligne + colonne** : `3C`, `6E`, `4D`…

```
     A   B   C   D   E   F   G   H

1 |   |   |   |   |   |   |   |   |
2 |   |   |   |   |   |   |   |   |
3 |   |   |   | + |   |   |   |   |
4 |   |   | + | ○ | ● |   |   |   |
5 |   |   |   | ● | ○ | + |   |   |
6 |   |   |   |   | + |   |   |   |
7 |   |   |   |   |   |   |   |   |
8 |   |   |   |   |   |   |   |   |
```

Les `+` (affichés en noir ici) indiquent les coups que vous pouvez jouer. Le but : avoir **le plus de pions** à la fin de la partie.

## 🤖 Sous le capot : comment réfléchit l'IA

L'IA repose sur l'algorithme **Minimax avec élagage alpha-bêta**, qui explore l'arbre des coups possibles en écartant les branches inutiles.

Sa profondeur de recherche évolue au fil de la partie :

| Phase | Pions sur le plateau | Profondeur | Ce qui compte le plus |
|---|---|---|---|
| 🌱 Ouverture | < 16 | 2 | Position + stabilité |
| ⚔️ Milieu de partie | 16 – 47 | 4 | + **Mobilité** (garder des options ouvertes) |
| 🏁 Fin de partie | ≥ 48 | 8 | **Nombre de pions** |

🎯 Pourquoi une profondeur évolutive ?

L'objectif : **allier performance de jeu et temps de calcul maîtrisé**. Une profondeur fixe serait soit trop lente, soit trop faible. L'IA investit donc son calcul là où il compte vraiment :

- **Ouverture (profondeur 2)** : le nombre de coups possibles est énorme, chercher plus loin ferait exploser le temps de calcul pour un gain minime, car rien de décisif ne se joue encore.
- **Milieu de partie (profondeur 4)** : le champ des possibles se réduit, et c'est ici que la stratégie se met en place et que les écarts se créent. On augmente donc la profondeur.
- **Fin de partie (profondeur 8)** : il reste peu de coups, on peut se permettre une recherche maximale pour trouver le meilleur coup possible et finir avec le plus de pions.

**Cette spécificité a été déterminante : grâce à elle, notre IA a battu celles de tous les autres binômes de la promo lors d'un tournoi, ce qui a valu au projet la note de 20/20 et la place de major de promo du module Data Science & IA.** 🏅

Pour évaluer un plateau, l'heuristique combine :

- **Le poids des cases** : les coins valent de l'or, les cases qui les entourent sont dangereuses
- **La mobilité** : avoir plus de coups possibles que l'adversaire
- **La stabilité** : les pions qui ne pourront plus être retournés

> 💡 Petit conseil : en fin de partie (profondeur 8), l'IA peut prendre un peu plus de temps à jouer. C'est normal, elle calcule !

## 🛠️ Technologies

- Python 3
- Jupyter Notebook

---

Bonne partie, et que le meilleur gagne ! 🏆
