

## Nom du challenge : petit cochon

Vous retrouvez cette derniere image d'un telephone d'un disparu.
prouvez qu'il cache quelque chose.

#lesinfos   
## STEP 1

après analyse de la photo, nous remarquons un fichier zip. 


![App Screenshot](https://imgur.com/eH2CsP7.png)

Il suffit de taper la commande : 
``` 
binwalk -e chall.jpg / binwalk -dd chall.jpg
```

nous faisons un extract de ce zip et obtenons une image

## STEP 2   


voici la photo extraite :

![App Screenshot](https://imgur.com/v2gAOZa.png)



comment savoir quelle couleur était. La voiture bleu était un indice pour  la couleur utiliser.

depuis stegsolve en `LSB RGB  B4` nous remarquons comme un binaire :  🛠
![App Screenshot](https://imgur.com/RPkrIQk.png)


## STEP 3 

après tentative avec du binaire qui ne donne rien nous remarquons depuis le site dcode qu'il s'agit du chiffrement bilitère de bacon 
![App Screenshot](https://imgur.com/srlQj8M.png)

nous pouvons lire le flag : ***MCTF{SHAKESPEARECYPHEREXAMINED}***
