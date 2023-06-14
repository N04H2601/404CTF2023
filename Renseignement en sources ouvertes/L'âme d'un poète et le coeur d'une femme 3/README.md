# L'âme d'un poète et le coeur d'une femme 3/4

**Catégorie** : Facile | **Points** : 903 | **Solves** : 123

## Description

*« C'est exactement ça ! 'Le salon littéraire de Louise Colet'. Pensez vous pouvoir me trouver une invitation ? »*

*Trouvez une invitation pour rejoindre le salon*

## Solution

Pour résoudre ce challenge, c'est un peu différent des deux précédents. Après avoir fait le tour des réseaux sociaux (Facebook, Instagram, Twitter, ...), j'ai donc pensé à la suite logique : on cherche un lien d'invitation à un serveur Discord et ce n'est pas forcément le genre de choses que l'on trouverait sur Instagram ou Facebook.

Je suis donc allé chercher du côté GitHub, typique de l'OSINT. J'ai cherché un éventuel compte à l'aide du pseudo donné dans le profil de son compte Instagram : Louise_Colet. En tapant ce pseudo dans la barre de recherche, on tombe pile sur ce qui nous intéresse comme premier [résultat](https://github.com/LouiseRevoil/Salon-litteraire-de-Louise-Colet), un repository nommé *Salon-litteraire-de-Louise-Colet*, d'une certaine LouiseRevoil (Louise Révoil étant le nom de naissance de Louise Colet). On descend tout en bas du README et on trouve le flag en plus d'un [lien](https://discord.gg/NeCgh9ZZqD) d'invitation Discord.

## Flag

<details>
<summary>🚩</summary>

```
404CTF{B13nv3nue_d4ns_le_s4lon_l1tter4ir3_de_lou1se_C0l3t}
```