# Hopp-Woods Hydrophilicity Prediction
## Adapted from publication:

*Prediction of protein antigenic determinants from amino
acid sequences*

by

THOMAS P. HOPP AND KENNETH R. WOODS

PNAS, 1981

## Mathematical principles

![](https://latex.codecogs.com/gif.latex?%24%24%20A%3D%5CBigg%5C%7B%5Cfrac%7B%5Csum%5Climits_%7Bi%3Dn%7D%5E%7Bn&plus;%5CDelta-1%7D%20X_%7Bi%7D%7D%7B%5CDelta%7D%20%5CBigg%7C%200%5Cle%20n%20%5Cle%20N-%5CDelta%5CBigg%5C%7D%20%24%24)

Rank items in set ![](https://latex.codecogs.com/gif.latex?A) from high to low (corresponding to the predicted hydrophilicity scores from high to low)

where:

![](https://latex.codecogs.com/gif.latex?N): amino acid length of the protein

![](https://latex.codecogs.com/gif.latex?n): residue index position on the protein (**starting from 0**)

![](https://latex.codecogs.com/gif.latex?%5CDelta): amino acid length of the peptide region of interest

![](https://latex.codecogs.com/gif.latex?%24X_%7Bi%7D%24): Hopp-Woods hydrophilicity value of amino acid ![](https://latex.codecogs.com/gif.latex?X) at index position ![](https://latex.codecogs.com/gif.latex?i)


## Examples of Usage
1. Try prediction different peptide length (original paper suggests 6 aa peptide appears to generate optimal results). 
2. Generate a list of all possible peptides of given length, ranked by their hydrophilicity score from highest > lowest
3. Change scores assigned to each residue


## Limitations
1. Predicted peptide has a buffer zone of 2 amino acids on each side
2. Best for predicting peptides of 5-7 in lengths
3. Does not predict secondary structures or non-linear epitopes
