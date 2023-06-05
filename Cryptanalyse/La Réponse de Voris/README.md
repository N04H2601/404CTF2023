# La Réponse de Voris

**Catégorie** : Moyen | **Points** : 960 | **Solves** : 80

## Description

*Vous rencontrez Mme de Beauvoir qui vous explique vouloir surprendre son mari Jean Sol Partre. Ce dernier est en train d'écrire un livre et a demandé à son ami Voris un titre approprié. Elle a réussi à se procurer un étrange message, qu'elle pense avoir été chiffré par Voris afin de limiter les fuites d'information. Ne sachant quoi faire avec ceci, elle s'est décidée à aller à la séance de spiritualisme du samedi au café littéraire, où elle vous a rencontré aujourd'hui. Par chance, vous connaissez une oracle pouvant peut être vous aider à déchiffrer ce message. Mais, malchance, cette dernière n'est qu'en mesure de chiffrer un message... Dommage, il va falloir réfléchir pour trouver le titre que Voris a proposé à Jean Sol !*

*message chiffré : **pvfdhtuwgbpxfhocidqcznupamzsezp***

## Solution

Pour résoudre ce challenge, il faut s'appuyer sur la méthode que l'on a appliqué pour le challenge [Le Jour de l'espace](../Le%20Jour%20de%20l'espace/README.md). En effet, nous nous étions intéressés au chiffre de Hill de la forme ``Y = AX``. Cette fois-ci, il s'agit d'un chiffre affine mais sous forme matricielle, à savoir ``Y = AX + B``. Il faut de nouveau trouver la matrice ``A``, mais également le vecteur ``B``.

Petit changement, nous n'envoyons plus les messages en clair 5 lettres par 5 lettres, mais directement en entier (31 caractères, comme le message chiffré de l'énoncé). On commence donc par envoyer ``aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`` pour envoyer le vecteur nul, ce qui nous donne dans l'équation : ``Y = A * 0 + B = B``. Donc, ``Y = B``. On récupère donc directement les valeurs du vecteur ``B``.

Pour la suite on va faire exactement comme pour [Le Jour de l'espace](../Le%20Jour%20de%20l'espace/README.md), à savoir envoyer ``baaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`` puis ``abaaaaaaaaaaaaaaaaaaaaaaaaaaaaa``, et ainsi de suite pour reformer la matrice identité. Seulement cette-fois il faudra juste traiter le résultat car on n'obtient pas directement une colonne de la matrice ``A``. Il faut d'abord l'isoler dans l'équation : ``Y - B = A * X``. On peut donc récupérer la colonne ``A`` en faisant ``Y - B``, avec ``Y`` le chiffré renvoyé par l'oracle et ``B`` le vecteur récupéré précédemment. On obtient donc la matrice ``A``.

Une fois que l'on a la matrice ``A`` et le vecteur ``B``, il suffit d'isoler le vecteur ``X`` dans l'équation ``Y = AX + B``. On obtient donc ``X = A ** -1 * (Y - B)``. On prend le message chiffré dans l'énoncé pour le vecteur ``Y`` et on obtient le message en clair.

```py
from pwn import *
import numpy as np
from Crypto.Util.number import inverse

r = remote("challenges.404ctf.fr", 31682)
print()
alpha = "abcdefghijklmnopqrstuvwxyz"
A = np.zeros((31, 31))
B = np.zeros((31, 1))

r.recvuntil(b"message en clair : ")
r.sendline(b"a" * 31)
values_string = r.recvline().decode('utf-8')[-32:-1]
values = list(values_string)
final = np.array([alpha.index(e) for e in values])

B[:, 0] = final
payload = "a" * 30

for i in range(31):
    r.recvuntil(b"message en clair : ")
    string = payload[:i] + "b" + payload[i:]
    r.sendline(string.encode())
    values_string = r.recvline().decode('utf-8')[-32:-1]
    values = list(values_string)
    final = np.array([alpha.index(e) for e in values])
    print(f"Row {i + 1}")
    A[:, i] = (final - B[:, 0]) % 26


def computeInversemod26(A):
    A = np.matrix(A)
    det = int(np.round(np.linalg.det(A)))
    det_inv = pow(det, -1, 26)
    A_inv = det_inv * np.round(det * A.I) % 26
    return A_inv


A_inv = computeInversemod26(A)
ciphertext = list("pvfdhtuwgbpxfhocidqcznupamzsezp")
cipher = np.array([alpha.index(e) for e in ciphertext])
plaintext_list = ((np.dot(A_inv, cipher - B[:, 0])) % 26).tolist()[0]
plaintext = list(map(int, plaintext_list))

print()
print("Flag:", "".join([alpha[i] for i in plaintext])) # Flag: lenclumedesjourneesensoleillees

print()
r.close()
```

## Flag

<details>
<summary>🚩</summary>

```
404CTF{l_enclume_des_journees_ensoleillees}
```