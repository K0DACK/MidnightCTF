
Voici un challenge de stéganographie permettant de comprendre le fonctionnement des chunks et de l'importance de leur ordre mais également que nous pouvons nous faire avoir par la commande "file".

## Nom du challenge : crash picture 737

#Plusieurs kilomètres après la dernière trace du vol, des valises ont été retrouvée. Un ordinateur a pu etre trouvé. Après une analyse, nous remarquons qu'une image à été envoyé quelques minutes avant la perte de la communication. Les analystes pensent que cette image n'est pas valide.
Prouvez leur le contraire.

***format du flag : MCTF{...}***

## STEP 1
Alors pour commencer si nous faisons la commande file sur l'image : 

```  file  image.png```

Nous obtiendrons ce résultat :

![App Screenshot](https://imgur.com/Ww3ffzl.png)


cependant ce n'est pas une  image JPEG, nous pouvons le vérifier,  nous remarquons des chunks d'image PNG.

## STEP 2

si nous regardons l'hexa de l'image nous remarquons un structure d'une image png mais le header d'une JPEG.

il suffit de changer le header de JPEG avec le header des PNG 

la photo pourra s'ouvrir mais sera totalement noire.



 | image initiale :                                     | image après les modifications :                                                |
| :----------------------------------------------- | ------------------------------------------------------------ |
| `FF D8 FF E0 00 10 4A 46 49 46`| `89 50 4E 47 0D 0A 1A 0A 00 00`                                           |
| ![App Screenshot](https://imgur.com/WNLqAd2.png)|    ![App Screenshot](https://imgur.com/wmDQlm2.png)                                                                                    |                                                               |

voici un screen de votre image :  🛠
![App Screenshot](https://imgur.com/LrOIOtX.png)


## STEP 3 

Une fois que nous obtenons l'image il faut checker les chunks
![App Screenshot](https://imgur.com/RnjFVsJ.png)



Quand une image est noire et que les chunk de bases sont correctes c'est que les chunk  des data ne sont pas bon, dans le mauvais sens. pour limiter les tests  ouvrez d'autre image pour comprendre le sens. Dans la majorité des cas les tailles  des chunks; le chunk le plus petit en taille est le dernier dans l'ordre.

donc voici les différents sens plausible : 

donc le fait de savoir la taille vous permettez d'enlever des possibilités inutiles.


| les différente possibilités| les resultats|
| :----------------------------------------------- |------------------|
|![App Screenshot](https://imgur.com/ZoflDbS.png)  | l'odre de base donnée|
|![App Screenshot](https://imgur.com/TwHe5nE.png) |ecran noir|
| ![App Screenshot](https://imgur.com/srY4bgl.png) |ecran   brouiller|
| ![App Screenshot](https://imgur.com/ndtQIwk.png) |ecran noir|
| ![App Screenshot](https://imgur.com/77HjoVQ.png) |![App Screenshot](https://imgur.com/jT1T1Sh.png)|
|![App Screenshot](https://imgur.com/JL1vJce.png)  | ![App Screenshot](https://imgur.com/oHFsb1B.png)|

Nous pouvons lire le flag : ***MCTF{a3ro_chunk_n0p_f!l3}***
