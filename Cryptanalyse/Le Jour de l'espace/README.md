# Le Jour de l'espace

**Catégorie** : Facile | **Points** : 874 | **Solves** : 140

## Description

*Rimbaud vous propose une séance initiatique au Oui-ja dans l'aile mystique du café littéraire (oui, oui, ça existe), vous avez une vision ésotérique :*

*Alors que vous voyez le texte suivant **ueomaspblbppadgidtfn**, Rimbaud vous décrit voir un étrange cadre de 50cm de côté, avec des petits carrés de 10cm de côtés, numérotés de 0 à 24 et jetés pêle-mêle sur le sol. Rimbaud n'y comprends rien, mais vous restez obsédé par cette idée, et décidez de résoudre l'énigme.*

*Toutes les informations nécéssaires à la résolution de ce challenge sont présentes dans l'énoncé ci-dessus.*


## Solution

Dans l'énoncé on nous parle d'un cadre de 50cm avec des carrés de 10cm de côté. On peut donc identifier une grille de 5x5 dans lequel on peut placer les lettres de ``a`` à ``y`` avec ``a = 0`` et ``y = 24``. Ce chiffrement est appelé le [chiffre de Hill](https://fr.wikipedia.org/wiki/Chiffre_de_Hill) : ``Y = AX`` avec ``Y`` le vecteur chiffré, ``A`` la matrice de chiffrement et ``X`` le vecteur clair.

On peut également vérifier ça en envoyant des vecteurs en clair à l'oracle de chiffrement (5 lettres par 5 lettres car on a une matrice 5x5) : en envoyant ``aaaaa`` on obtient en sortie ``aaaaa``, ce qui est normal car on envoie en réalité le vecteur nul ``X = (0, 0, 0, 0, 0)`` en entrée comme ``a = 0`` donc on aura en sortie ``Y = A * 0 = 0`` d'où le fait que ``Y`` soit aussi égal à ``aaaaa``.

Maintenant que l'on a identifié le chiffrement et son fonctionnement, comme on connaît les valeurs de ``X`` (notre vecteur en clair que l'on envoit à l'oracle) et ``Y`` (le vecteur chiffré que l'on reçoit de l'oracle), le but est de trouver la matrice ``A`` pour pouvoir ensuite déchiffrer le message donné dans l'énoncé.En effet, une fois que l'on a identifié A, on peut calculer son inverse (modulo 25) ``A ** -1`` et donc déchiffrer le message en faisant ``X = A ** -1 * Y``.

Pour ce faire, j'ai simplement eu besoin de ressortir mes cours d'espaces vectoriels sur le calcul matriciel et réfléchir un petit peu. En effet, le but ici est de trouver la matrice ``A`` en sachant que l'on peut envoyer un vecteur ``X`` et recevoir son chiffré ``Y``. Je sais qu'une matrice multiplié par la matrice identité me donne cette même matrice (la matrice identité est constitué de 0 partout avec des 1 sur la diagonale principale). Sauf qu'ici, je ne peux envoyer que des vecteurs. Mais ça n'est pas un problème :)

En effet, je n'ai qu'à envoyer chaque colonne de ma matrice identité séparément.

Un petit exemple pour le premier vecteur de la matrice identité (``(1, 0, 0, 0, 0)``) : je l'envoie à l'oracle et je récupère le vecteur chiffré ``Y``. Je sais que ``Y = A * (1, 0, 0, 0, 0)``. Je peux donc en déduire la première colonne de ``A``. Je fais la même chose pour les 4 autres colonnes et j'obtiens la matrice ``A``.

En effet :

```
              [a11, a12, a13, a14, a15]   [1]       [a11]
              [a21, a22, a23, a24, a25]   [0]       [a21]
A * I[:, 0] = [a31, a32, a33, a34, a35] * [0] = Y = [a31]
              [a41, a42, a43, a44, a45]   [0]       [a41]
              [a51, a52, a53, a54, a55]   [0]       [a51]
```

Et voilà comment identifier la première colonne de A. On peut faire la même chose pour les 4 autres colonnes et on obtient la matrice ``A``.

Enfin, on calcule l'inverse de ``A`` modulo 25 et on déchiffre le message donné dans l'énoncé.

```py
import numpy as np

A = np.array([[9, 4, 18, 20, 8], [11, 0, 2, 1, 3], [5, 6, 7, 10, 12], [
             13, 14, 15, 16, 17], [19, 21, 22, 23, 24]])

# compute modular inverse of matrix A (mod 25)
def computeInversemod25(A):
    A = np.matrix(A)
    det = int(np.round(np.linalg.det(A)))
    det_inv = pow(det, -1, 25)
    A_inv = det_inv * np.round(det * A.I) % 25
    return A_inv

cipher = "ueoma"

b = np.array([ord(c) - 97 for c in cipher])
A_inv = computeInversemod25(A)
x = (np.dot(A_inv, b) % 25).tolist()
print("".join([chr(int(i) + 97) for i in x[0]])) # Output: barja
```
Le script python que j'ai réalisé déchiffre le message 5 lettres par 5 lettres (je l'ai fais rapidement pendant le CTF il est bien sûr optimisable).

On obtient donc en sortie : barjavelmaassassinea

Il faut simplement retirer le dernier ``a`` pour obtenir le flag (en effet, lorsque l'on envoie un message à l'oracle mais que la longueur du message n'est pas un multiple de 5, l'oracle complète le message avec des ``a``).

## Flag

<details>
<summary>🚩</summary>

```
404CTF{barjavelmaassassine}
```