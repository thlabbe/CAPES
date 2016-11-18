# CAPES 2016 Sujet Zéro

## Partie A : repr´esentation des L-Systèmes

1. Ecrire un programme ´ Python permettant de r´ealiser la figure *maison* ci-après avec le mode turtle, sachant que :
AB = BC = CD = DE = EA = 100, (AB) ⊥ (AE) et (AB) ⊥ (BC).


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