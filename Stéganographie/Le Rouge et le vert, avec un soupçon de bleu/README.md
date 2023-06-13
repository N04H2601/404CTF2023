# Le Rouge et le vert, avec un soupçon de bleu

**Catégorie** : Difficile | **Points** : 927 | **Solves** : 107

## Description

*Ce qui semble être un brouillon a été laissé sur une table en hâte par un jeune homme. Vous vous rapprochez pour le lui rendre, mais il a déjà disparu. Vous décidez de lire ce bout de papier pour déterminer la personnalité de son auteur. Le début ressemble à un poème. La fin quant à elle a l'air assez spéciale...*

*Toutes les informations nécessaires à la résolution de ce challenge sont présentes dans l'énoncé ci-dessus. Déchiffrez la fin du poème.*

<p align="center">
  <img src="Rouge_Vert_Bleu.jpg" alt="rouge vert bleu" width="600">
</p>

## Solution

A la fin de l'image on peut voir clairement le message codé mais avec des morceaux manquants. Les morceaux manquants sont des bandes de couleur (rouge, bleu, vet et blanc). Il faut donc déterminer les 3 chiffres cachés derrière chaque bande de couleur pour reconstituer le message :

Ci-après le message avec WWW pour white, RRR pour red, GGG pour green et BBB pour blue :


```
76WWW321021089710332WWW115116581089795118RRRWWW95WWW1109599BBBGGG108WWWGGG114115125
```

Afin de reconstituer le message j'ai commencé par déchiffrer ce qui nous était connu :

Pour le début en déchiffrant de décimal vers ASCII on obtient :

```
L* flag
```
On en déduit très simplement que WWW sera égal à ``e`` en décimal (101). On peut donc déchiffrer un peu plus de texte :

```
76101321021089710332101115116581089795118RRR101951011109599BBBGGG108101GGG114115125
```

On déchiffre et on détermine la valeur de RRR :

```
Le flag est:la_v*e_en_c
```

On identifie aisément que RRR correspond à la lettre ``i`` en décimal (105). On répète les mêmes opérations pour les valeurs de GGG et BBB et on obtient finalement :

```
Le flag est:la_vie_en_couleurs
```

## Flag

<details>
<summary>🚩</summary>

```
404CTF{la_vie_en_couleurs}
```