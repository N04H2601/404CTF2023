# Le Rouge et le vert, avec un soupçon de bleu

**Catégorie** : Moyen | **Points** : 961 | **Solves** : 78

## Description

*Ce qui semble être un brouillon a été laissé sur une table en hâte par un jeune homme. Vous vous rapprochez pour le lui rendre, mais il a déjà disparu. Vous décidez de lire ce bout de papier pour déterminer la personnalité de son auteur. Le début ressemble à un poème. La fin quant à elle a l'air assez spéciale...*

*Toutes les informations nécessaires à la résolution de ce challenge sont présentes dans l'énoncé ci-dessus. Déchiffrez la fin du poème.*

<p align="center">
  <img src="Rouge_Vert_Bleu.jpg" alt="rouge vert bleu" width="600">
</p>

## Solution

A première vue, on ne discerne pas vraiment ce qu'il faut faire pour ce challenge. Cependant, j'ai remarqué que les espaces ne concordaient pas parfaitement dans les deux textes. Je les ai donc visualisé avec un [outil](https://vii5ard.github.io/whitespace/) en ligne pour surligner les espaces :

On peut remarquer que le pattern n'est pas similaire pour certains mots dans les deux blocs de texte, notamment : Paris, Marseille, Allemagne... J'ai donc relevé les mots qui avaient le même pattern dans le bloc de gauche (un espace à gauche du mot et deux après).

## Flag

<details>
<summary>🚩</summary>

```
404CTF{paris_finlande_15_6_avion}
```