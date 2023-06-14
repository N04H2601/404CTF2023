# La Quête du sens 2/3

**Catégorie** : Moyen | **Points** : 977 | **Solves** : 61

## Description

*Vous vous rappelez de son nom maintenant. Marceline Desbordes-Valmore, passionnée d'écriture et de musique ! Elle est connue au salon pour ses inventions aussi imprévisibles qu'éphémères. Elle se penche soudainement d'un air enjoué vers vous. Vous n'avez pas le temps d'essayer d'esquiver le long monologue qui s'annonce qu'elle est déjà lancée sur sa dernière idée : publier un journal dont les auteurs seraient des écrivains romantiques ! Vous lui faites remarquer que ce concept n'est peut-être pas si original que cela. Vexée, elle pianote furieusement sur son téléphone, bien décidée à vous montrer que vous avez tort. Elle tombe alors sur un étrange échange de message dans un forum obscur :*

*Sainte-Marie : Je crois que notre journal n'a pas beaucoup de succès.*

*Auverney : Pourtant, qui n'a pas besoin d'un peu de romantisme dans sa vie ?*

*Sainte-Marie : il faut se rendre à l'évidence, nous allons devoir arrêter cette activité.*

*Auverney : ... il est dur de se faire une raison, mais j'accepte. On en parle aux autres d'abord ? @Frères ?*

*Marceline, embêtée de ne pas avoir eu l'idée en premier, veut à tout prix retrouver le nom de ce journal impopulaire. Saurez-vous le lui fournir ?*


## Solution

Avant de commencer ce genre de challenge, le tout est de bien lire l'énoncé car c'est notre seul indice. On relève donc les informations importantes: nous devons trouver un journal dont les auteurs sont des écrivains romantiques, avec comme informations notables son nom (Marceline Desbordes-Valmore), ainsi que la mention de '@Frères', probablement un indice pour trouver le nom du journal.

Je fais donc une recherche filtrée à l'aide d'une dork Google : ``"romantique" "journal" "marceline" "desbordes" "valmore" "frères"``. Dans les premiers résultats je tombe sur ce [site](https://www.mediaclasse.fr/lectures/456). Je fais un ``CTRL+F`` pour trouver le mot ``journal``. Une seule correspondance : *Démis de ses fonctions, il fonde son journal Le Conservateur en 1818. À ce moment, Victor Hugo n’a que 17 ans, mais il veut déjà devenir « Chateaubriand ou rien » : il fonde Le Conservateur littéraire en 1819.* Curieux, je me renseigne sur ce journal et tombe sur la [page](https://fr.wikipedia.org/wiki/Le_Conservateur_litt%C3%A9raire) Wikipédia : *Le Conservateur littéraire est une revue littéraire fondée en 1819 par les frères Abel, Eugène et Victor Hugo, elle exprime le point de vue de l'aile ultra-royaliste des écrivains romantiques (Hugo, Lamartine, Alfred de Vigny, Alexandre Soumet...).* On tient notre journal !

## Flag

<details>
<summary>🚩</summary>

```
404CTF{le_conservateur_litteraire}
```