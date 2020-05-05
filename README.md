# Hopp-Woods Hydrophilicity Prediction with Linear Variation Model

## Description

A numeric value is assigned to each amino acid, using the amino acid scale outlined in the paper:

*Prediction of protein antigenic determinants from amino acid sequences*, T Hopp, K Woods, PNAS 1981 [link](https://www.ncbi.nlm.nih.gov/pubmed/6167991)

User provides protein seq in single-letter amino acid code, specifies a window size (length of the peptide), and edge weight (default ![\alpha=1](https://render.githubusercontent.com/render/math?math=%5Calpha%3D1)). For each amino acid in the window, the program computes a weight using the linear variation model. It then applies the weight to the original score at amino acid level. The final hydrophilicity score for the peptide is calculated by dividing the sum of the corrected amino acid scores by the sum of the weights. The program repeats the process along the sequence of the protein.


## Mathematical principles

Given: 

<img src="https://github.com/xinyu-dev/hopp-woods/blob/master/images/eq1.png" width=50% height=50%>

Rank items in set S from high to low

where:

![\phi(n)](https://render.githubusercontent.com/render/math?math=%5Cphi(n)): ![w_{i}\neq1](https://render.githubusercontent.com/render/math?math=w_%7Bi%7D%5Cneq1) or non-weighted ![w_{i}=1](https://render.githubusercontent.com/render/math?math=w_%7Bi%7D%3D1) hydrophilicity scores

![N](https://render.githubusercontent.com/render/math?math=N): Number of amino acids in the protein

![n](https://render.githubusercontent.com/render/math?math=n): residue index position on the protein (starting from 0)

![\Delta](https://render.githubusercontent.com/render/math?math=%5CDelta): size of the peptide "window"

![X_{i}](https://render.githubusercontent.com/render/math?math=X_%7Bi%7D): Hopp-Woods hydrophilicity value of amino acid X at index position i

![w_{i}](https://render.githubusercontent.com/render/math?math=w_%7Bi%7D): weight used at each position. Weights are calculated using linear variation model (see below)


## Linear Variation Model for Calculation of Weights

1. When no weights are used:

   ![w_{i}=1](https://render.githubusercontent.com/render/math?math=w_%7Bi%7D%3D1)
   
2. When using weights from linear variation model, specify edge weight ![\alpha (\alpha\subset {(0, 1\]})](https://render.githubusercontent.com/render/math?math=%5Calpha%20(%5Calpha%5Csubset%20%7B(0%2C%201%5D%7D))


   **1) When the peptide window (![](https://latex.codecogs.com/gif.latex?%24%5CDelta%24)) is an odd number:**
   
   ![](https://latex.codecogs.com/gif.latex?%24%24w_%7Bi%7D%3D%20%5Cbegin%7Bcases%7D%20%5Calpha&plus;%5Cfrac%7B1-%5Calpha%7D%7B%5Clfloor%200.5%5CDelta%20%5Crfloor%7Dq%20%26%200%5Cle%20q%20%5Cle%20%5Clfloor%200.5%5CDelta%20%5Crfloor%5C%5C%201-%5Cfrac%7B1-%5Calpha%7D%7B%5Clfloor%200.5%5CDelta%20%5Crfloor%7D%28q-%5Clfloor%200.5%5CDelta%20%5Crfloor%29%20%26%20%5Clfloor%200.5%5CDelta%20%5Crfloor%5C%20%3C%20q%20%5Cle%20%5CDelta-1%20%5Cend%7Bcases%7D%24%24)
   
   For example, if window=7 (7-mer peptide), edge ![](https://latex.codecogs.com/gif.latex?%24%5Calpha%3D0.1%24), then the first and the last weights will be 0.1. The weight for each amino acid in the 7-mer is:
   
   [0.1, 0.4, 0.7, 1.0, 0.7, 0.4, 0.1]
   
   **2) When the peptide window (![](https://latex.codecogs.com/gif.latex?%24%5CDelta%24)) is an even number: (new feature not available in Expasy)**
   
   ![](https://latex.codecogs.com/gif.latex?%24%24w_%7Bi%7D%3D%20%5Cbegin%7Bcases%7D%20%5Calpha&plus;%5Cfrac%7B1-%5Calpha%7D%7B0.5%5CDelta-1%7Dq%20%26%200%5Cle%20q%20%3C%200.5%5CDelta%5C%5C%201-%5Cfrac%7B1-%5Calpha%7D%7B0.5%5CDelta-1%7D%28q-0.5%5CDelta%29%20%26%200.5%5CDelta%20%5Cle%20q%20%5Cle%20%5CDelta-1%20%5Cend%7Bcases%7D%20%24%24)
   
   For example, if window=10, edge ![](https://latex.codecogs.com/gif.latex?%24%5Calpha%3D0.1%24), then the first and the last weights will be 0.1.The weight for each amino acid in the 10-mer is:
   
   [0.1, 0.33, 0.55, 0.78, 1.0, 1.0, 0.78, 0.55, 0.32, 0.1]


![](https://github.com/xinyu-dev/hopp-woods/blob/master/images/Weights_by_Linear_Variation_Model.png)
## Examples of Usage

See jupyter notebook


## Validation against Expasy Query Results
Expasy results were obtained from [ProtScale](https://web.expasy.org/protscale/)

![](https://github.com/xinyu-dev/hopp-woods/blob/master/images/expassy_validate_noweights.png)
![](https://github.com/xinyu-dev/hopp-woods/blob/master/images/expassy_validate_weighted.png)




