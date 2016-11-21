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

```python
	alphabet = [ 'F', '+' , '-']
``` 


 2. Décrire la figure *maison* sous la forme **F**(**l**, **a**, **m**) en précisant les valeurs de **l**, **a** et **m (on commencera
du point A).

 3. Ecrire une fonction **dessiner** qui :
- reçoit en entrée :
 - unite : un nombre représentant la longueur **l**
 - angle : un nombre représentant le pas de rotation **a**
 - motif : le motif **m** de la figure sous forme d’une chaîne de caractères
- affiche le dessin **F**(**l**, **a**, **m**) et retourne 0 si celui-ci a pu être réalisé intégralement et 1 sinon (par
exemple si un caractère non défini est présent dans le motif).

```python
# avec turtle
def dessiner(unite, angle, motif):
	for commande in motif:
		print(commande)
		if commande == "F":
			forward(unite)
		
		elif commande == "+":
			left(angle)
		
		elif commande == "-": 
			right(angle) 
		
		else:
			return 1

	return 0
```

```python
# avec mathplot
def dessiner(unite, angle, motif):
    xi = 0.0
    yi = 0.0
    X = [xi]
    Y = [yi]
    ai = angle
    
    for commande in motif:
        if commande == "F":
            xi = xi + unite * cos(radians(ai))
            yi = yi + unite * sin(radians(ai))
        
        elif commande == "+":
            ai = ai + angle
		
        elif commande == "-":
            ai = ai - angle
		
		else:
		    return 1
		
        X.append(xi)
        Y.append(yi)
            
    plot(X,Y,"k-")
    show()
    return 0
```

# 6 Démontrer qu'à l'étape n, la chaîne de caractères représentant le flcon contient 3*4^n caractères F et 4^(n+1) caractères de rotation (+ ou -)

à l'étape 0 : la chaîne est "F--F--F"
nombre de F : 3 = 3*4^0 
nombre de caractères de rotation : 4 = 4^(1) = 4^( 1 + 0)

en admettant qu'à l'étape n 3*4^n = nombre de F et  4^(n+1) = nombre de caractères de rotation
à l'étape n+1 chaque caractère F est remplacé par "F+F--F+F"
d'où : - nombre de caractères F à l'étape n+1 : 4*(3*4^n) = 4 * 3 * 4^n = 3*4^(n+1)
       - nombre de caractères de rotation : 4^(n+1) + 4 * 3*4^n = 4^(n+1) + 3 * 4 ^ (n+1) = (1 + 3)^4(n+1) = 4*4^(n+1) 4^(n+2)
par reéurrence nous démontrons que le nombre de caractères de rotation est égal à 4^(n+1)	   
 

  .../...
# PROBLEME 2
## Parie A
### 1.mots bianires de longueur 3:
000 ; 001 ; 010 ; 011 ; 100 ; 101 ; 110 ; 111

### 2.Ecrire un fonction motn(donnant les mots de M(n,k) pour k < 10:
```python
from itertools import product

def motn(n,k):
    resultat = []
    for mot in product(range(k), repeat = n):
        chaine = ""
        for caractere in mot:
            chaine += str(caractere)
        resultat.append(chaine)
    
    return resultat
```  

### 3. combien y a-t-il d'éléments dans M(n,k) (ensemble des mots de longueur n sur l'alphabet de [0,k-1])
nb = k^n

### 4.En supposant qu’une liste puisse contenir jusqu’à 500 000 000 éléments, quelle longueur maximale peut-on donner aux mots binaires pour que la fonction motn s’exécute sans erreur (c’est-`a-dire k = 2)? 
pour k = 2 le nombre d'élement dans la liste est 2^n : log2(500.000.000) **!!!???!!! a verifier**

## Partie B
### 1.Déterminer tous les représentants possibles du mot circulaire (1011).
(1011) = (0111) = (1110) = (1101) 

### 2.Déterminer le nombre maximal de représentant d'un mot circulaire de n lettres.
dans les représentations d'un mot circulaire de longueur n la lettre ai peut occuper les n potision 1 à n, il en découle que le mot circulaire de longueur n peut avoir au maximum n représentations.
les n représentations peuvent contenir des homographies ( doublons ) d'où la notion de nombre *maximal* de représentations

### 3. Déduire de la question précédente un minorant du nombre de mots circulaires différents obtenus à partir de M(n,k). La réponse devra être justifiée. 
???

 