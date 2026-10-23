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

```bash
pip install colorama
```

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

Les `+` (affichés en rouge) indiquent les coups que vous pouvez jouer. Le but : avoir **le plus de pions** à la fin de la partie.

## 🤖 Sous le capot : comment réfléchit l'IA

L'IA repose sur l'algorithme **Minimax avec élagage alpha-bêta**, qui explore l'arbre des coups possibles en écartant les branches inutiles.

Sa profondeur de recherche évolue au fil de la partie :

| Phase | Pions sur le plateau | Profondeur | Ce qui compte le plus |
|---|---|---|---|
| 🌱 Ouverture | < 16 | 2 | Position + stabilité |
| ⚔️ Milieu de partie | 16 – 47 | 4 | + **Mobilité** (garder des options ouvertes) |
| 🏁 Fin de partie | ≥ 48 | 8 | **Nombre de pions** |

Pour évaluer un plateau, l'heuristique combine :

- **Le poids des cases** : les coins valent de l'or, les cases qui les entourent sont dangereuses
- **La mobilité** : avoir plus de coups possibles que l'adversaire
- **La stabilité** : les pions qui ne pourront plus être retournés

> 💡 Petit conseil : en fin de partie (profondeur 8), l'IA peut prendre un peu plus de temps à jouer. C'est normal, elle calcule !

## 🛠️ Technologies

- Python 3
- [`colorama`](https://pypi.org/project/colorama/) pour les couleurs dans le terminal
- Jupyter Notebook

## 🔮 Idées d'amélioration

- Choix du niveau de difficulté
- Interface graphique (Pygame, Tkinter…)
- Mode IA contre IA

---

Bonne partie, et que le meilleur gagne ! 🏆
