# Mann-Whitney Web App

-- Update 2/27/2019

The Mann-Whitney U test is a non-parametric test for testing whether two independent data samples come from the same distribution.

This is a web application for Mann-Whitney U test made with Python and Flask. Add solution to test for small sample size (n < 20).


## Demo
https://mannwhitney.herokuapp.com/


![demo](https://github.com/Hatchin/Mann-Whitney-Extension/blob/master/demo.png)

## Guide

### Data Summary

Information summary for two groups of data, including sample size (number of data samples), mean, standard deviation and median for each group.    

### Test Result

`Sig Diff`: whether or not the two sample data are from different distribution at the custom significant level

`Sample Size`: if n <= 20, then small sample size; else large sample size

`U-critical` or `P Value`: when small sample size, return the U critical value at the significant level; when large sample size, return the P Value computed from U stat

`Sample Stat`: U stat computed from the data samples

`Effect Size`:  a value to measure how large the difference is between the two data groups. 

Formula:

<a href="https://www.codecogs.com/eqnedit.php?latex=\fn_phv&space;EffectSize&space;=&space;1&space;-&space;\frac{2\times&space;U_{stat}}{n1\times&space;n2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\fn_phv&space;EffectSize&space;=&space;1&space;-&space;\frac{2\times&space;U_{stat}}{n1\times&space;n2}" title="EffectSize = 1 - \frac{2\times U_{stat}}{n1\times n2}" /></a>

`Larger Group`: indicates which group has a higher value

### Interpretation
1. Determine whether or not `Sample Size` is small
   1. if n <20 ,then `Small` size, continue to step 2;
   2. else, then `Large` size, continue to step 3
2. Determine whether or not there is significant difference
   1. If sample size is `Small`, compare `U-critical` and `Sample Stat` : 
      1. if `U-critical` < `Sample Stat`, then there is significant difference (`Sig Diff` = `Yes`), continue to step 4;
      2. else, there is no signifcant difference (`Sig Diff` = `Yes`), end
3. If sample size is `Large`, compare `P value` and <a href="https://www.codecogs.com/eqnedit.php?latex=\alpha" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" /></a> : 
   1. if `P value` < <a href="https://www.codecogs.com/eqnedit.php?latex=\alpha" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" /></a>, then there is significant difference (`Sig Diff` = `Yes`), continue to step 4;
   2. else, there is no signifcant difference (`Sig Diff` = `Yes`), end


## Requirements
Flask==0.12.2

Pandas>=0.21.1

Numpy>=1.14.3

Scipy>=1.1.0

Request>=2.7.0

## Installation
Change to app directory, use `virtualenv` create and activate virtual enviroment.  
Then use `pip` to install requirements：  
```
pip install -r requirements.txt
```
Run:  
```
python app.py runserver
```

Go to http://127.0.0.1:5000/



