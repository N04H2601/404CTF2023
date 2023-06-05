# Dessine-moi une courbe elliptique

**Catégorie** : Facile | **Points** : 796 | **Solves** : 177

## Description

**Au cours d'une de vos explorations dans le café, vous surprenez la conversation suivante :**

*Oh ! Ce jour, je m'en souviens parfaitement, comme si c'était hier. À cette époque, je passais mes journées à mon bureau chez moi, avec comme seule occupation de dessiner les illustrations qui m'étaient commandées par les journaux du coin. Je ne m'en rendais pas compte à ce moment, mais cela faisait bien 6 ans que je vivais cette vie monacale sans réelle interaction humaine. Le temps passe vite quand on n'a rien à faire de ses journées. Mais ce jour-là, c'était différent. Je m'apprêtais à commencer ma journée de travail, un peu stressé parce que j'avais des illustrations que je devais absolument finir aujourd'hui. Alors que je venais de m'installer devant ma planche à dessin, quelle ne fut pas ma surprise d'entendre une voix venir de derrière-moi :*
*« S'il-te plaît, dessine moi une courbe elliptique. »*
*Je me suis retourné immédiatement. Un petit bonhomme se tenait derrière moi, dans mon appartement, habillé de façon tout à fait incongrue. Il portait une sorte de tenue de mousquetaire céleste ? Même aujourd'hui je ne sais toujours pas comment la décrire.*

*« Quoi ?*

*— S'il-te plaît, dessine moi une courbe elliptique. »*

*Devant cette situation ubuesque, mon cerveau a lâché, a abandonné. Je ne cherchais plus à comprendre et je me contentais de répondre:*

*« Je ne sais pas ce que c'est.*

*— Ce n'est pas grave, je suis sûr que tu pourras en dessiner une belle! Répondit l'enfant en rigolant. »*

*Machinalement, je pris mon crayon, et je dessinai à main levée une courbe, sans réfléchir. Après quelques instants, je me suis retourné, et j'ai montré le résultat à l'enfant, qui secoua immédiatement la tête.*

*« Non, regarde: cette courbe à un déterminant nul, je ne veux pas d'une courbe malade ! »*

*À ce moment, je ne cherchais plus à comprendre ce qu'il se passait. J'ai donc fait la seule chose que je pouvais faire, j'en ai redessiné une. Cette fois, l'enfant était très heureux.*

*« Elle est magnifique ! Je suis sûr qu'elle sera très heureuse toute seule. »*

*Et là, sous mes yeux ébahis, la courbe pris vie depuis mon dessin, et s'envola dans la pièce. Elle se mit à tourner partout, avant de disparaître. J'étais bouche bée, enfin encore plus qu'avant.*

*« Ah, elle avait envie de bouger visiblement !*

*— Où est-elle partie ?*

*— Je ne sais pas. Mais c'est toi qui l'a dessinée ! Tu ne devrais pas avoir de mal à la retrouver. En plus je crois qu'elle t'a laissé un petit souvenir, dit-il en pointant le sol, où une série de chiffres étaient effectivement dessinés sur le parquet.*

*— Merci encore ! Sur ce, je dois partir. Au revoir ! »*

*Avant que je puisse ouvrir la bouche, il disparût.*
*Je ne sais toujours pas ce qu'il s'est passé ce jour-là, mais je retrouverais cette courbe un jour !*

*Peut-être pourriez-vous l'aider ?*

## Solution

En lisant le script Python associé au chall, on peut voir que l'on chiffre un message à l'aide de l'algorithme AES-CBC. On peut voir également que nous n'avons pas les valeurs de ``a`` et ``b``, cependant la somme de ces valeurs donnent la clé à utiliser pour l'AES. Il faut donc la déterminer, en sachant que l'on a également les coordonnées de deux point sur la courbe elliptique.

C'est alors que j'ai trouvé exactement ce que je cherchais sur un [forum de cryptographie](https://crypto.stackexchange.com/questions/97811/find-elliptic-curve-parameters-a-and-b-given-two-points-on-the-curve), à savoir comment déterminer les paramètres ``a`` et ``b`` d'une courbe elliptique à partir de des coordonnées de deux points sur la courbe : $$a = [(y_1^2 - y_2^2) - (x_1^3 - x_2^3)] (x_1 - x_2)^-1$$

## Flag

<details>
<summary>🚩</summary>

```
404CTF{}
```