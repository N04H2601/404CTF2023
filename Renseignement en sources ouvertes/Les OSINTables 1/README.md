# Les OSINTables 1/3

**Catégorie** : Facile | **Points** : 200 | **Solves** : 478

## Description

*En pleine discussion au Procope, Cosette vous raconte autour d'une part de fraisier la première fois qu'elle a essayé d'envoyer une lettre à son bienfaiteur : Jean Valjean.*

*Débutante dans la démarche postale, elle s'est trompée sur les informations nécessaires, elle en a même oublié l'adresse du destinataire, n'écrivant que la sienne. Elle vous montre la photo ci-jointe et vous met au défi de trouver d'où elle l'a écrite.*

*Trouvez l'adresse d'envoi de la lettre (celle de Cosette).*

<p align="center">
  <img src="photo.jpg" alt="enonce" width="600">
</p>

## Solution

Pour résoudre ce challenge, j'ai d'abord identifié le numéro 83, écrit en chiffres romains, ainsi que la Rue Victor Hugo. N'ayant pas saisi les autres indices présents sur la lettre, je décide de rentrer l'adresse sur Google Maps : 83 Rue Victor Hugo Ve... (je laisse le moteur de recherche me proposer des résultats). Je tombe alors sur la ville de Vergèze comme premier résultat. Et parce que l'OSINT c'est parfois un peu de guessing aussi, il s'avère que c'était la bonne réponse.

En y ayant repensé après avoir résolu le challenge, il me semble que l'adresse a tout simplement dû apparaître dans les premiers résultats grâce aux recherches des autres participants, alors merci à eux !

## Flag

<details>
<summary>🚩</summary>

```
404CTF{83_rue_victor_hugo_vergeze}
```