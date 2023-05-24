# Libraries

Libraries are collections of functions called modules that can be imported and used in your script. Let's use the `math` library to grab constants:

```py
import math
math.e
```

```
2.718281828459045
```

Now how about functions:

```py
math.log2(25)
```

```
4.643856189774724
```
We want to point out that here we call the value `e` after `math`. This is called a **member value**. On the contrary we see that `.log2()` comes after `math`. The parentheses make this a **method** or function in a given package. 

!!! tip
    If you ever need assistance with a library, try using the `help()` function to grab more information (e.g. `help(math)`).
    
## Importing Parts of Libraries & Using Aliases

Sometimes you'll only need a few things from a library. To grab just those few things use the following approach:

```py
from math import log2, e
math.log2(25)
```

```
4.643856189774724
```

Now sometimes the name of a library is just too long to continuously type out. For this we can use an **alias**

```py
from math import log2 as l2
math.l2(25)
```

```
4.643856189774724
```

Here we abbreviate `log2` from the `math` package to `l2`.

## Importing and Inspecting Data Frames 

In data analysis we often work with tabular data, or two dimensional data with columns and rows. Columns will typically contain the same type of data and rows will be one sample with different observations. We commonly read in tabular data using the `pandas` module:

```py
import pandas as pd
import csv
df = pd.read_csv('/cluster/tufts/bio/tools/training/intro-to-r/metadata.tsv' , sep = '/t', engine = 'python')
print(df)
```

```
    SampleID AntibioticUsage DaySinceExperimentStart Genotype                 Description OtuCount
1   WT.unt.1            None                    DAY0       WT   16S_WT_unt_1_SRR2627457_1     1174
2   WT.unt.2            None                    DAY0       WT   16S_WT_unt_2_SRR2627461_1     1474
3   WT.unt.3            None                    DAY0       WT   16S_WT_unt_3_SRR2627463_1     1492
4   WT.unt.7            None                    DAY0       WT   16S_WT_unt_7_SRR2627465_1     1451
5 WT.day3.11    Streptomycin                    DAY3       WT 16S_WT_day3_11_SRR2628505_1      314
6 WT.day3.13    Streptomycin                    DAY3       WT 16S_WT_day3_13_SRR2628506_1      189
7 WT.day3.15    Streptomycin                    DAY3       WT 16S_WT_day3_15_SRR2628507_1      279
8 WT.day3.14    Streptomycin                    DAY3       WT 16S_WT_day3_14_SRR2627471_1      175
9  WT.day3.9    Streptomycin                    DAY3       WT  16S_WT_day3_9_SRR2628504_1      452
```

If we want to inspect this data frame we can use a few useful commands. To get a quick summary of the data frame we can use:

```py
df.info() # reveals that we have 6 columns, 9 rows, uses 504.0+ bytes of memory, and has one integer column
```

```
<class 'pandas.core.frame.DataFrame'>
Int64Index: 9 entries, 1 to 9
Data columns (total 6 columns):
 #   Column                   Non-Null Count  Dtype 
---  ------                   --------------  ----- 
 0   SampleID                 9 non-null      object
 1   AntibioticUsage          9 non-null      object
 2   DaySinceExperimentStart  9 non-null      object
 3   Genotype                 9 non-null      object
 4   Description              9 non-null      object
 5   OtuCount                 9 non-null      int64 
dtypes: int64(1), object(5)
memory usage: 504.0+ bytes
```

To get column names:

```py
df.columns
```

```
Index(['SampleID', 'AntibioticUsage', 'DaySinceExperimentStart', 'Genotype',
       'Description', 'OtuCount'],
      dtype='object')
```

To get row names:

```py
df.index
```

```
Int64Index([1, 2, 3, 4, 5, 6, 7, 8, 9], dtype='int64')
```

To transpose (flip the columns and rows) the data frame:

```py
df.T
```

```
                                                 1                          2  
SampleID                                  WT.unt.1                   WT.unt.2   
AntibioticUsage                               None                       None   
DaySinceExperimentStart                       DAY0                       DAY0   
Genotype                                        WT                         WT   
Description              16S_WT_unt_1_SRR2627457_1  16S_WT_unt_2_SRR2627461_1   
OtuCount                                      1174                       1474   
```

If we wanted a numeric summary we can use:

```py
df.describe()
```

```
          OtuCount
count     9.000000
mean    777.777778
std     600.526806
min     175.000000
25%     279.000000
50%     452.000000
75%    1451.000000
max    1492.000000
```

!!! note
    the `.describe()` method will only summarizes numeric data. So here we only have one column of numeric data that get's summarized.

## Data Manipulation

Say you want to grab certain values in a data frame using the number location. So the value in the second row and third column:

```py
df.iloc[2,3]
```

```
'WT'
```
Here we see that the formula to grab values is `[row, column]`. If we wanted to use row/column names to specify the value:

```py
df.loc[1,"OtuCount"]
```

```
1174
```

To grab all values in a row or column we use `:` to specify every value:

```py
df.loc[:,"OtuCount"]
```

```
1    1174
2    1474
3    1492
4    1451
5     314
6     189
7     279
8     175
9     452
Name: OtuCount, dtype: int64
```

We can also subset our data with a few operators:

| Operator | Description |
:-------|:-----|
| > | greater than | 
| >= | greater than or equal |
| < | less than |
| <= | less than or equal |
| == | equals | 
| != | not equal |
| & | and |
| \| | or|

Let's go through a few of these:

```py
df[df["AntibioticUsage"] == "None"]    # select samples with no antibiotic useage
```

```
SampleID	AntibioticUsage	DaySinceExperimentStart	Genotype	Description	OtuCount
1	WT.unt.1	None	DAY0	WT	16S_WT_unt_1_SRR2627457_1	1174
2	WT.unt.2	None	DAY0	WT	16S_WT_unt_2_SRR2627461_1	1474
3	WT.unt.3	None	DAY0	WT	16S_WT_unt_3_SRR2627463_1	1492
4	WT.unt.7	None	DAY0	WT	16S_WT_unt_7_SRR2627465_1	1451
```

```py
df[df["OtuCount"] > 400]   # select samples with an otu count over 400
```

```
SampleID	AntibioticUsage	DaySinceExperimentStart	Genotype	Description	OtuCount
1	WT.unt.1	None	DAY0	WT	16S_WT_unt_1_SRR2627457_1	1174
2	WT.unt.2	None	DAY0	WT	16S_WT_unt_2_SRR2627461_1	1474
3	WT.unt.3	None	DAY0	WT	16S_WT_unt_3_SRR2627463_1	1492
4	WT.unt.7	None	DAY0	WT	16S_WT_unt_7_SRR2627465_1	1451
9	WT.day3.9	Streptomycin	DAY3	WT	16S_WT_day3_9_SRR2628504_1	452
```
