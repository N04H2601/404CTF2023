# Les Félicitations

**Catégorie** : Facile | **Points** : 921 | **Solves** : 110

## Description

*Au café littéraire, le serveur vous parle alors qu'il vous porte votre café bien noir afin de rester alerte : « Vous avez osé braver cette tempête ? Toutes mes félicitations ! Et en parlant de félicitation, trouvez celles cachées dans ce texte. »*

```
Tous étaient réunis dans la salle,

Criblant leur feuille de mots et posant leurs esprits sur papier.

Très encouragés par le déroulement des opérations,

Il suffisait simplement de les regarder pour voir leur dévotion

.-.. . -.-. --- -.. . -- --- .-. ... . -.-. . ... - ... -.-- -- .--. .-

Beaucoup d'entre eux étaient fiers de leur oeuvre

Cillant à peine quand dehors, un monstre jappait

Fierté mène cependant à orgueil

Et n'oubliez pas qu'orgueil mène à perte.

-- .- .. ... .-.. .- -.-. .- ... . .-. - .- .-. .. . -. .... .- .... .-

Juste au moment où leurs travaux allaient finir,

Hors du laboratoire, un cri retentissant fut émis

Peu d'humains avaient entendu ce genre de cris.

Exténués par cette énième attaque, les scientifiques se remirent au travail.
```

## Solution

Pour résoudre ce challenge, la première étape était évidemment de déchiffrer le morse :

- Le premier message décodé donne : LECODEMORSECESTSYMPA
- Le second message décodé donne : MAISLACASERTARIENHAHA

Cette piste est donc écarté et on en déduit que le morse sert simplement de séparateur pour le texte.
Après beaucoup de recherches et de tentatives, j'ai fini par trouver comment extraire les mots du texte. Il faut prendre le premier caractère de la première ligne, puis le deuxième de la deuxième ligne, et pareil pour la troisième ligne. On repart ensuite du premier caractère de la première ligne pour le paragraphe suivant (délimité par le morse et obtient finalement trois mots : Très, Bien, Joué.

## Flag

<details>
<summary>🚩</summary>

```
404CTF{TrèsBienJoué}
```