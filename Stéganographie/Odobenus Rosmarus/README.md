# Odobenus Rosmarus

**Catégorie** : Introduction | **Points** : 100 | **Solves** : 582

## Description
*« Bonjour à toi, et bienvenue au café littéraire ! »*

*Connais-tu la première règle de la lecture ? Ne pas s'attacher aux mots. Il faut les surpasser, chercher l'idée derrière. L'existence précède l'essence, ici nous cherchons l'essence des choses, et non pas leur existence ou leur forme.*

*Je te laisse un petit quelque chose. Prouve moi que tu peux lire entre les lignes.*

```
Ce soir je Célèbre Le Concert Electro Comme Louis Et Lou. Comme La nuit Commence Et Continue Clairement, Et Clignote Lascivement il Chasse sans Chausser En Clapant Encore Classiquement Les Cerclages du Clergé. Encore Car Encore, Louis Lou Entamant Longuement La Lullabile En Commençant Le Cercle Exhaltant de Club Comique Cannais Et Clermontois.
```

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