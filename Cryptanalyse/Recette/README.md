# Recette

**Catégorie** : Introduction | **Points** : 100 | **Solves** : 597

## Description

*Le Commissaire Maigret, café à la main, vous raconte une de ses dernières enquêtes. Il vous explique que sur une scène de crime il a retrouvé un papier faisant office de message codé. Il le sort de sa poche pour vous le montrer :*

*Convertir depuis l'hexadécimal*
*Développer de sorte à ne plus voir de chiffres*
*Décoder le DeadFish*
*Convertir depuis la Base 85*

```
Suivi de la séquence : 32 69 31 73 34 69 31 73 31 35 64 31 6f 34 39 69 31 6f 34 64 31 6f 33 69 31 6f 31 35 64 31 6f 32 32 64 31 6f 32 30 64 31 6f 31 39 69 31 6f 37 64 31 6f 35 64 31 6f 32 69 31 6f 35 35 69 31 6f 31 64 31 6f 31 39 64 31 6f 31 37 64 31 6f 31 38 64 31 6f 32 39 69 31 6f 31 32 69 31 6f 32 36 69 31 6f 38 64 31 6f 35 39 64 31 6f 32 37 69 31 6f 36 64 31 6f 31 37 69 31 6f 31 32 64 31 6f 37 64 31 6f 35 69 31 6f 31 64 31 6f 32 64 31 6f 31 32 69 31 6f 39 64 31 6f 32 36 64 31 6f
```

## Solution

A première vue, on ne discerne pas vraiment ce qu'il faut faire pour ce challenge. Cependant, j'ai remarqué que les espaces ne concordaient pas parfaitement dans les deux textes. Je les ai donc visualisé avec un [outil](https://vii5ard.github.io/whitespace/) en ligne pour surligner les espaces :


On peut remarquer que le pattern n'est pas similaire pour certains mots dans les deux blocs de texte, notamment : Paris, Marseille, Allemagne... J'ai donc relevé les mots qui avaient le même pattern dans le bloc de gauche (un espace à gauche du mot et deux après).

## Flag

<details>
<summary>🚩</summary>

```
404CTF{paris_finlande_15_6_avion}
```