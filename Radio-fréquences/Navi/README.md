# Navi

**Catégorie** : Introduction | **Points** : 100 | **Solves** : 319

## Description

*En vous installant à une table, sirotant tranquillement une boisson, vous entendez le bruit monter à l’intérieur du café littéraire.*

*C'est à ce moment qu'une femme vient s'assoir en face de vous. Elle se présente comme étant Simone DE BEAUVOIR. Vous vous étiez déjà rencontrés lors des comités de lecture des éditions Gallimard.*

*Pendant votre discussion absolument passionnante, la radio du café diffuse une lecture de La ruelle des lutins. C'est à ce moment que son auteur, Alexandre DUMAS, vient se joindre à votre compagnie.*

*Toutefois, vous remarquez que ce dernier semble intrigué par la narration, pensant qu'elle doit cacher quelque chose...*

## Solution

Pour résoudre ce challenge, j'ai tout d'abord importé le fichier .raw dans Audacity et j'ai écouté l'audio. J'ai remarqué qu'il fallait augmenter la vitesse de lecture par deux pour etendre une dame parler. Cependant, j'entendais également dans le fond une autre voix, mais je n'arrivais pas à la comprendre. J'ai donc appliqué un filtre passe-bas et joué avec les paramètres de tempo pour trouver la solution.

Cependant, il existait une solution beaucoup plus simple que j'ai découvert ensuite et que je préfère détailler par rapport à celle qui m'a permis de flag. En effet, au lieu d'importer le .raw en ``Mono`` dans Audacity, il suffisait de l'importer en ``Stereo``. Je pouvais alors isoler la voix que j'entendais dans le fond et en inversant le sens de l'audio puis en accélérant la vitesse de lecture par deux, j'ai pu entendre la voix qui me donnait le flag en hexadécimal :

```
34 30 34 43 54 46 7B 31 74 72 30 5F 34 55 78 5F 52 34 64 31 30 2D 66 52 33 71 55 33 4E 63 33 35 7D
```

## Flag

<details>
<summary>🚩</summary>

```
404CTF{1tr0_4Ux_R4d10-fR3qU3Nc35}
```