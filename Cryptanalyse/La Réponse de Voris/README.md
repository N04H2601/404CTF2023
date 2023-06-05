# La Réponse de Voris

**Catégorie** : Moyen | **Points** : 960 | **Solves** : 80

## Description

*Vous rencontrez Mme de Beauvoir qui vous explique vouloir surprendre son mari Jean Sol Partre. Ce dernier est en train d'écrire un livre et a demandé à son ami Voris un titre approprié. Elle a réussi à se procurer un étrange message, qu'elle pense avoir été chiffré par Voris afin de limiter les fuites d'information. Ne sachant quoi faire avec ceci, elle s'est décidée à aller à la séance de spiritualisme du samedi au café littéraire, où elle vous a rencontré aujourd'hui. Par chance, vous connaissez une oracle pouvant peut être vous aider à déchiffrer ce message. Mais, malchance, cette dernière n'est qu'en mesure de chiffrer un message... Dommage, il va falloir réfléchir pour trouver le titre que Voris a proposé à Jean Sol !

| message chiffré : pvfdhtuwgbpxfhocidqcznupamzsezp

## Solution

Pour résoudre ce challenge, la seule difficulté était de trouver le bon [tool](https://pypi.org/project/ascon/) à utiliser. On pouvait ensuite réaliser un simple script pour déchiffrer le message car nous avions toutes les informations nécessaires.

```py
import ascon


key = bytes.fromhex("00456c6c616e61206427416c2d466172")
nonce = bytes.fromhex("00000000000000000000000000000000")
data = bytes.fromhex("80400c0600000000")
cipher = bytes.fromhex(
    "ac6679386ffcc3f82d6fec9556202a1be26b8af8eecab98783d08235bfca263793b61997244e785f5cf96e419a23f9b29137d820aab766ce986092180f1f5a690dc7767ef1df76e13315a5c8b04fb782")

print(f"Key: {key}")
print(f"Nonce: {nonce}")
print(f"Ciphertext: {cipher}")
print(f"Data: {data}")

plaintext = ascon.decrypt(key, nonce, data, cipher, variant="Ascon-128")
print(f"Plaintext: {plaintext}")
```

## Flag

<details>
<summary>🚩</summary>

```
404CTF{V3r5_l4_lum1èr3.}
```