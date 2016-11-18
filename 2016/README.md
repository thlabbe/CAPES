# CAPES 2016 Sujet Zéro

## Partie A : représentation des L-Systèmes
### Le module turtle

1. Ecrire un programme `Python` permettant de réaliser la figure *maison* ci-après avec le mode turtle, sachant que :
>  AB = BC = CD = DE = EA = 100, (AB) ⊥ (AE) et (AB) ⊥ (BC).

```python
from turtle import *
from math import sqrt

len = 100
forward (len)
left (90)
forward (len)
left (30)    
forward (len)
left (90 + 30)
forward (len)
left (30)    
forward (len)
```

###Un alphabet pour coder les figures
Comme on réalise régulièrement les mêmes instructions, on se propose de d'écrire les figures selon les règles suivantes : une figure **F** est d´efinie par la donnée d’un triplet contenant :
- une longueur **l**
- un pas de rotation **a**, donnée en degrés
- un mot, appelée motif, sur l’alphabet {**F**, **+**, **-**} avec comme convention :
 - **F** : avancer de **l**
 - **+** : tourner à gauche de l’angle défini par le pas de rotation
 - **-** : tourner à droite de l’angle défini par le pas de rotation.


2. Décrire la figure *maison* sous la forme **F**(**l**, **a**, **m**) en précisant les valeurs de **l**, **a** et **m (on commencera
du point A).

3. Ecrire une fonction **dessiner** qui :
- reçoit en entrée :
 - unite : un nombre représentant la longueur **l**
 - angle : un nombre représentant le pas de rotation **a**
 - motif : le motif **m** de la figure sous forme d’une chaîne de caractères
— affiche le dessin **F**(**l**, **a**, **m**) et retourne 0 si celui-ci a pu être réalisé intégralement et 1 sinon (par
exemple si un caractère non défini est présent dans le motif).
