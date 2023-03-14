---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="9xZnRXM7x0Cv">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## Coffee chain dataset background

**Description**:

Dataset describing the information of different species of beans and
leaves. Coffee are made from beans and tea are made from leaves. This
dataset give some information about the coffee chain sales.

**Github**:
<https://github.com/prasertcbs/basic-dataset/blob/071c42dfb3554c58d0d60d9087fc0917df9067c1/coffee_chain.xlsx>

**Sample size**: 4248

**Feature documentation**:

| NO. | Column         | Non-Null Count | Dtype   |
|:----|:---------------|:---------------|:--------|
| 0   | ProductId      | 4248 non-null  | int64   |
| 1   | Area Code      | 4248 non-null  | int64   |
| 2   | Date           | 4248 non-null  | object  |
| 3   | Budget COGS    | 4248 non-null  | int64   |
| 4   | Budget Margin  | 4248 non-null  | int64   |
| 5   | Budget Profit  | 4248 non-null  | int64   |
| 6   | Budget Sales   | 4248 non-null  | object  |
| 7   | COGS           | 4248 non-null  | int64   |
| 8   | Inventory      | 4248 non-null  | object  |
| 9   | Margin         | 4248 non-null  | int64   |
| 10  | Marketing      | 4248 non-null  | int64   |
| 11  | Profit         | 4248 non-null  | int64   |
| 12  | Sales          | 4248 non-null  | int64   |
| 13  | Total Expenses | 4248 non-null  | int64   |
| 14  | Product Name   | 4248 non-null  | object  |
| 15  | Product Line   | 4248 non-null  | object  |
| 16  | Product Type   | 4248 non-null  | object  |
| 17  | Type           | 4248 non-null  | object  |
| 18  | Market Size    | 4248 non-null  | object  |
| 19  | Market         | 4248 non-null  | object  |
| 20  | State          | 4248 non-null  | object  |
| 21  | Unnamed: 21    | 0 non-null     | float64 |
| 22  | Unnamed: 22    | 0 non-null     | float64 |
| 23  | Unnamed: 23    | 0 non-null     | float64 |

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   Nowadays, A lot of people would like to choose either tea or
        coffee to drink. I love drinking coffee and tea. But I found out
        that not everyone loves drinking these both. I want to know
        which one is more popular based on their sales. That is the
        reason why I would like to pursue this topic. Also, my idea is
        to find out whether they are both popular or only one of these
        is more popular.
-   What two groups you are comparing:
    -   **G1**: beans; **G2**:leaves
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `sales`
-   Is your response variable quantitative rather than categorical?
    -   `sales` is quantitative data. Therefore, I would compare these
        data with its own value.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   I would expect that **G2** \> **G1** since [Tea Drinkers vs.
        Coffee Drinkers: 30 Statistics to Know in
        2023](https://coffeeaffection.com/tea-drinkers-vs-coffee-drinkers-statistics/).
-   Talk about how you will gather your data
    -   From Github link:
        <https://github.com/prasertcbs/basic-dataset/blob/071c42dfb3554c58d0d60d9087fc0917df9067c1/coffee_chain.xlsx>
        -And change it to csv file via Github
        link:<https://raw.githubusercontent.com/IIreneee01/STAT1013/main/coffee_chain.csv?token=GHSAT0AAAAAAB7DMLJZG7A56QYMJVAJJT6AY76FEOQ>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) Test:let people choose a drink they want to drink to see
        if they would choose coffee, tea or other beverage;

    \(ii\) Questionnaire:give online questionnaires to investigate
    customers what they prefer; (iii):Investigation:go to each coffee
    store to inquire which product line has the better sales

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:383}"
id="mUxJb4hxvpHQ" outputId="c05ffdce-48cb-4317-be9e-6811959904c9">

``` python
## load dataset from github

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/IIreneee01/STAT1013/main/coffee_chain.csv?token=GHSAT0AAAAAAB7DMLJZG7A56QYMJVAJJT6AY76FEOQ')
df.head(5)
```

<div class="output execute_result" execution_count="2">

       ProductId  Area Code      Date  Budget COGS  Budget Margin  Budget Profit  \
    0          1        719  1/1/2012           90            130            100   
    1          2        970  1/1/2012           80            110             80   
    2          3        970  1/1/2012          100            140            110   
    3         13        303  1/1/2012           30             50             30   
    4          5        303  1/1/2012           60             90             70   

      Budget Sales  COGS Inventory  Margin  ...       Product Name  Product Line  \
    0          220    89       777     130  ...           Amaretto         Beans   
    1          190    83       623     107  ...          Columbian         Beans   
    2          240    95       821     139  ...  Decaf Irish Cream         Beans   
    3           80    44       623      56  ...          Green Tea        Leaves   
    4          150    54       456      80  ...        Caffe Mocha         Beans   

       Product Type     Type   Market Size   Market     State Unnamed: 21  \
    0        Coffee  Regular  Major Market  Central  Colorado         NaN   
    1        Coffee  Regular  Major Market  Central  Colorado         NaN   
    2        Coffee    Decaf  Major Market  Central  Colorado         NaN   
    3           Tea  Regular  Major Market  Central  Colorado         NaN   
    4      Espresso  Regular  Major Market  Central  Colorado         NaN   

      Unnamed: 22 Unnamed: 23  
    0         NaN         NaN  
    1         NaN         NaN  
    2         NaN         NaN  
    3         NaN         NaN  
    4         NaN         NaN  

    [5 rows x 24 columns]

</div>

</div>

<div class="cell markdown" id="55xAIxVa3hpQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (Sales\|Product Line = Beans) vs. **G2** (Sales\|Product
        Line = Leaves)

</div>

<div class="cell markdown" id="13PdL3ht3902">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="UNL0WXav3hLj" outputId="97acd58d-0634-4fec-e7ec-36014b591425">

``` python
## First 5 records of G1 (beans)
(df[df['Product Line'] == 'Beans']['Sales']).head(5)
```

<div class="output execute_result" execution_count="27">

    0    219
    1    190
    2    234
    4    134
    5    180
    Name: Sales, dtype: int64

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="dhe52HVB4T1O" outputId="01b2375f-53df-4ce1-8077-2aafe2a6f878">

``` python
## First 5 records of G2 (Leaves)
(df[df['Product Line'] == 'Leaves']['Sales']).head(5)
```

<div class="output execute_result" execution_count="26">

    3    100
    6    341
    7    150
    8    140
    9    130
    Name: Sales, dtype: int64

</div>

</div>

<div class="cell code" id="zEgfWXaKGvNC">

``` python
## Any other data description and visualization you want to add.

## Open question, be flexible and no example can be provided.
```

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="aUYa12YnsAQE" outputId="e66fe3d4-ff8b-4ed8-c702-db276dce6d92">

``` python
##basic info
df.info()
```

<div class="output stream stdout">

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4248 entries, 0 to 4247
    Data columns (total 24 columns):
     #   Column          Non-Null Count  Dtype  
    ---  ------          --------------  -----  
     0   ProductId       4248 non-null   int64  
     1   Area Code       4248 non-null   int64  
     2   Date            4248 non-null   object 
     3   Budget COGS     4248 non-null   int64  
     4   Budget Margin   4248 non-null   int64  
     5   Budget Profit   4248 non-null   int64  
     6   Budget Sales    4248 non-null   object 
     7   COGS            4248 non-null   int64  
     8   Inventory       4248 non-null   object 
     9   Margin          4248 non-null   int64  
     10  Marketing       4248 non-null   int64  
     11  Profit          4248 non-null   int64  
     12  Sales           4248 non-null   int64  
     13  Total Expenses  4248 non-null   int64  
     14  Product Name    4248 non-null   object 
     15  Product Line    4248 non-null   object 
     16  Product Type    4248 non-null   object 
     17  Type            4248 non-null   object 
     18  Market Size     4248 non-null   object 
     19  Market          4248 non-null   object 
     20  State           4248 non-null   object 
     21  Unnamed: 21     0 non-null      float64
     22  Unnamed: 22     0 non-null      float64
     23  Unnamed: 23     0 non-null      float64
    dtypes: float64(3), int64(11), object(10)
    memory usage: 796.6+ KB

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:522}"
id="_v2SdLtqsDkw" outputId="e947e189-d183-4b50-cc12-70cbaf4a7a31">

``` python
##basic description of the data
df.describe(include='all')
```

<div class="output execute_result" execution_count="15">

              ProductId    Area Code      Date  Budget COGS  Budget Margin  \
    count   4248.000000  4248.000000      4248  4248.000000    4248.000000   
    unique          NaN          NaN        24          NaN            NaN   
    top             NaN          NaN  1/1/2012          NaN            NaN   
    freq            NaN          NaN       177          NaN            NaN   
    mean       6.887006   582.278013       NaN    74.830508     100.819209   
    std        3.664072   221.140310       NaN    66.238145      92.602725   
    min        1.000000   203.000000       NaN     0.000000    -210.000000   
    25%        4.000000   417.000000       NaN    30.000000      50.000000   
    50%        6.000000   573.000000       NaN    50.000000      70.000000   
    75%       10.000000   772.000000       NaN    90.000000     130.000000   
    max       13.000000   985.000000       NaN   450.000000     690.000000   

            Budget Profit Budget Sales         COGS Inventory       Margin  ...  \
    count     4248.000000         4248  4248.000000      4248  4248.000000  ...   
    unique            NaN           89          NaN       610          NaN  ...   
    top               NaN          100          NaN       777          NaN  ...   
    freq              NaN          282          NaN        54          NaN  ...   
    mean        60.913371          NaN    84.433145       NaN   104.293315  ...   
    std         79.546123          NaN    67.249769       NaN    94.342522  ...   
    min       -320.000000          NaN     0.000000       NaN  -302.000000  ...   
    25%         20.000000          NaN    43.000000       NaN    52.750000  ...   
    50%         40.000000          NaN    60.000000       NaN    76.000000  ...   
    75%         80.000000          NaN   100.000000       NaN   132.000000  ...   
    max        560.000000          NaN   364.000000       NaN   613.000000  ...   

            Product Name  Product Line  Product Type     Type   Market Size  \
    count           4248          4248          4248     4248          4248   
    unique            13             2             4        2             2   
    top        Columbian         Beans      Espresso  Regular  Small Market   
    freq             480          2232          1176     2400          2544   
    mean             NaN           NaN           NaN      NaN           NaN   
    std              NaN           NaN           NaN      NaN           NaN   
    min              NaN           NaN           NaN      NaN           NaN   
    25%              NaN           NaN           NaN      NaN           NaN   
    50%              NaN           NaN           NaN      NaN           NaN   
    75%              NaN           NaN           NaN      NaN           NaN   
    max              NaN           NaN           NaN      NaN           NaN   

             Market State Unnamed: 21 Unnamed: 22 Unnamed: 23  
    count      4248  4248         0.0         0.0         0.0  
    unique        4    20         NaN         NaN         NaN  
    top     Central  Utah         NaN         NaN         NaN  
    freq       1344   288         NaN         NaN         NaN  
    mean        NaN   NaN         NaN         NaN         NaN  
    std         NaN   NaN         NaN         NaN         NaN  
    min         NaN   NaN         NaN         NaN         NaN  
    25%         NaN   NaN         NaN         NaN         NaN  
    50%         NaN   NaN         NaN         NaN         NaN  
    75%         NaN   NaN         NaN         NaN         NaN  
    max         NaN   NaN         NaN         NaN         NaN  

    [11 rows x 24 columns]

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:983}"
id="OL_GPz8PtgEh" outputId="7f0fac13-52ac-4e59-c46e-2cbabd8df85b">

``` python
## grapgh
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.set()
sns.histplot(data=df, x='Sales', hue='Product Line')
plt.show()

sns.histplot(data=df, x='Sales', y='Product Line')
plt.show()

sns.violinplot(data=df, x="Sales", y="Product Line")
plt.show()
```

<div class="output display_data">

![](9b4996ccbb44700229db3bfd1081e4ca0b69b908.png)

</div>

<div class="output display_data">

![](5ad1342bdc69f71c4373f8a49afb1fd9a3fa9920.png)

</div>

<div class="output display_data">

![](2490291eb005b2afd294238df6daa29c06e305d3.png)

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="3dEicSAXx3-v" outputId="b3a34d67-18e6-4a9b-ee5c-94c70af3a2f7">

``` python
##mean, std, median, min and max values for Beans and Leaves
print('condition STAT of Beans')
a=(df[df['Product Line'] == 'Beans']['Sales'])
print(a.agg(['min','max','mean','std','median']))

print('---')

print('condition STAT of Leaves')
b=(df[df['Product Line'] == 'Leaves']['Sales'])
print(b.agg(['min', 'max','mean','std','median']))
```

<div class="output stream stdout">

    condition STAT of Beans
    min        23.000000
    max       912.000000
    mean      197.053763
    std       158.886262
    median    139.000000
    Name: Sales, dtype: float64
    ---
    condition STAT of Leaves
    min        17.000000
    max       796.000000
    mean      188.485615
    std       141.960152
    median    137.000000
    Name: Sales, dtype: float64

</div>

</div>
