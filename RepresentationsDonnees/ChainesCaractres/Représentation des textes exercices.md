# Représentation des textes: exercices. 



**Exercice 1 :** L'algorithme rot13 est un algorithme très simple de chiffrement qui consiste à décaler de 13 caractères chaque lettre d'un texte. Par exemple, le mot *python* est transformé en *clguba*.

Écrire, en Python, une fonction rot13(s) en supposant que la chaîne passée en argument ne contient que des caractères entre a et z (en minuscule) et éventuellement des espaces. Votre fonction ne doit décaler que les lettres de l'alphabet (elle ne touche donc pas aux espaces). Elle renvoie en sortie une chaîne de caractères. 



**Exercice 2 :** Sachant que le point  de code du symbole é est E9, donner la séquence de points de code du mot élégance, puis les octets en binaire correspondant à l'encodage UTF-8 de ce mot. 



**Exercice 3 :** Pour chacune des séquences d'octets suivantes, représentées en base 10, dire si elle représente une séquence UTF-8 valide et si oui, combien de caractères sont représentés. 

1. 126 64 100
2. 198 129 129
3. 227 180 140




**Exercice 4 :** Écrire une fonction Python longeur(b) qui parcourt la chaîne d'octets b, supposé représenter une chaîne encodée en UTF-8 et qui compte le nombre de caractères (il est interdit de convertir b en chaîne puis de calculer la longueur de cette dernière). 
