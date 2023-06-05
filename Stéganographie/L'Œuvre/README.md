# L'Œuvre

**Catégorie** : Facile | **Points** : 200 | **Solves** : 783

## Description
*Dans un coin du Procope, vous remarquez Claude Lantier scrutant sans relâche un tableau, tasse à la main. Cette situation vous interpelle et vous lui demandez ses raisons. Il vous explique qu'avec son œil de peintre il remarque des **variations de couleurs** à la limite de l'imperceptible.*

*Trouvez un message secret dans la peinture ci-jointe.*

<p align="center">
  <img src="loeuvre.png" alt="l'oeuvre" width="600">
</p>

## Solution

Pour résoudre ce challenge, il fallait d'abord se renseigner sur la signification du titre. Odobenus Rosmarus est le nom scientifique du morse, un animal marin. On peut donc facilement en déduire que le challenge est en rapport avec le morse.
Le plus dur était de trouver où était le morse ici. Plusieurs idées me sont venus en tête, parfois même des idées trop farfelues. J'étais par exemple parti sur l'idée qu'une majuscule était un trait et une miniscule un point, et bien d'autres enccore.
Mais en voyant le nombre des résolutions, je me suis dit que ce n'était pas si compliqué. Je m'y suis donc remis à tête reposée et lorsque j'ai prêté plus attention aux majuscules, j'ai trouvé qu'elles se répétaient étrangement, car nous avions seulement les trois lettres suivantes : C, L et E. C'est alors que j'ai fais le lien avec le morse, à savoir : C pour court, L pour long et E pour espace. J'ai donc pu déchiffrer le message et obtenir le flag :

```py
import morse_talk as mtalk

message = "Ce soir je Célèbre Le Concert Electro Comme Louis Et Lou. Comme La nuit Commence Et Continue Clairement, Et Clignote Lascivement il Chasse sans Chausser En Clapant Encore Classiquement Les Cerclages du Clergé. Encore Car Encore, Louis Lou Entamant Longuement La Lullabile En Commençant Le Cercle Exhaltant de Club Comique Cannais Et Clermontois.".split(
    " ")

morse = "".join(["." if word.startswith("C") else "-" if word.startswith("L")
                 else " " if word.startswith("E") else "" for word in message])

print(f"404CTF{{{mtalk.decode(morse)}}}")
```

## Flag

<details>
<summary>🚩</summary>

```
404CTF{FACILELEMORSE}
```