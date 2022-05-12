This is the subset of the Reuters-21578 benchmark for (plain) text classification.

It contains only the documents with a single category label and only the categories that have at least 1 document in both the training and testing sets, same as the filtering scheme by Debole and Sebastiani, 2005. It's suitable for text classification, especially using the models with their own tokenizers such as BERT, which shows good performance on the plain text.

On the internet, there are [R52 datasets after pre-processing](https://ana.cachopo.org/datasets-for-single-label-text-categorization), provided by Ana Cardoso-Cachopo. But I couldn't find the raw R52 dataset without pre-processing, so I built one.

## Making a subset

I used dataset provided with NLTK Python library as a base. The only change in the text is that escaped 'less than' sign (\&lt;) is restored to <.

I tried my best to follow the given directions, but **there are inconsistencies with the R52 dataset online**. The total number of documents in other pre-processed R52 dataset is 9,100, whereas mine is 9,130. I'm not sure where this inconsistency come from. Maybe NLTK version of Reuters-21578 has some duplicated documents over different categories. (c.f. Debole and Sebastiani mentioned that their dataset consists of 9,052 documents) So, **please use with caution**.

## Distribution

There are 52 classes and 9,130 documents.

```
class            train  test
acq               1596   696
alum                31    19
bop                 22     9
carcass              6     5
cocoa               46    15
coffee              90    22
copper              31    13
cotton              15     9
cpi                 54    17
cpu                  3     1
crude              253   121
dlr                  3     3
earn              2840  1083
fuel                 4     7
gas                 10     8
gnp                 59    15
gold                70    20
grain               41    10
heat                 6     4
housing             15     2
income               7     4
instal-debt          5     1
interest           191    81
ipi                 34    11
iron-steel          26    12
jet                  2     1
jobs                37    12
lead                 4     4
lei                 11     3
livestock           16     6
lumber              10     4
meal-feed           10     1
money-fx           222    87
money-supply       123    28
nat-gas             24    12
nickel               3     1
orange              13     9
pet-chem            13     6
platinum             1     2
potato               2     3
reserves            37    12
retail              19     1
rubber              31     9
ship               108    36
strategic-metal      9     6
sugar               97    25
tea                  2     3
tin                 17    10
trade              250    76
veg-oil             19    11
wpi                 14     9
zinc                 8     5
TOTAL             6560  2570
```

## Format

File encoding is UTF-8. There is no header.

There are 4 columns, each are file id, category id, name of the category, and the raw text.

Columns are distinguished with tabs (\t).

The category id is given in the alphabetical order.

The raw text (most of them) contains New-line character (\n), so its quoted with quote sign. (")

## Notes

I do not own any copyright of this dataset.

If you're using Pandas, you can load the file by

```
pandas.read_csv('r52-raw.txt', header=None, sep='\t')
```
