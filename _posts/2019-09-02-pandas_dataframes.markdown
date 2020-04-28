---
layout: post
title:      "Pandas | Dataframes"
date:       2019-09-02 22:07:24 -0400
permalink:  pandas_dataframes
---

> Published on Medium | [Article](https://medium.com/@spettiett/pandas-dataframe-for-beginners-cec24dc3d1ca)

```
Pandas - DataFrames
Pandas is one of the most popular Python libraries for Data Science and Analytics.

Why? Because pandas helps you to manage two-dimensional data tables in Python. In this pandas tutorial series about dataframes, I’ll show you the some important things that you have to know as a Data Scientist.

We will start from the basics!

Import Libraries
# Import Pandas Library
import pandas as pd

# Import Other Libraries
import numpy as np
import matplotlib as plt
%matplotlib inline
How to open data files in pandas
You might have your data in .csv files, excel files, from a URL or SQL tables. In all cases, if you want to analyze that data using pandas, the first step will be to read it into a data structure that’s compatible with pandas like dataframe.

Read in data from .csv file into Dataframe Structure

# EXAMPLE_
# df = pd.read_csv("./filename.csv")
Read in data from URL into Dataframe Structure

data_url = 'http://bit.ly/2cLzoxH'
df = pd.read_csv(data_url)   # Read data contained in URL into dataframe (df)
Preview Data in the dataframe.
Sometimes, it makes sense not to print the whole dataframe and flood your screen with lots of data. When a few lines is enough, you can print only the first 5 rows or last 5 rows – by typing the following:

df.head() # Preview the first (5) rows in the dataframe = default
country	year	pop	continent	lifeExp	gdpPercap
0	Afghanistan	1952	8425333.0	Asia	28.801	779.445314
1	Afghanistan	1957	9240934.0	Asia	30.332	820.853030
2	Afghanistan	1962	10267083.0	Asia	31.997	853.100710
3	Afghanistan	1967	11537966.0	Asia	34.020	836.197138
4	Afghanistan	1972	13079460.0	Asia	36.088	739.981106
df.tail() # Preview the last (5) rows in the dataframe = default
country	year	pop	continent	lifeExp	gdpPercap
1699	Zimbabwe	1987	9216418.0	Africa	62.351	706.157306
1700	Zimbabwe	1992	10704340.0	Africa	60.377	693.420786
1701	Zimbabwe	1997	11404948.0	Africa	46.809	792.449960
1702	Zimbabwe	2002	11926563.0	Africa	39.989	672.038623
1703	Zimbabwe	2007	12311143.0	Africa	43.487	469.709298
df.head(10) # Preview the first (10 or specify any #) rows in the dataframe
country	year	pop	continent	lifeExp	gdpPercap
0	Afghanistan	1952	8425333.0	Asia	28.801	779.445314
1	Afghanistan	1957	9240934.0	Asia	30.332	820.853030
2	Afghanistan	1962	10267083.0	Asia	31.997	853.100710
3	Afghanistan	1967	11537966.0	Asia	34.020	836.197138
4	Afghanistan	1972	13079460.0	Asia	36.088	739.981106
5	Afghanistan	1977	14880372.0	Asia	38.438	786.113360
6	Afghanistan	1982	12881816.0	Asia	39.854	978.011439
7	Afghanistan	1987	13867957.0	Asia	40.822	852.395945
8	Afghanistan	1992	16317921.0	Asia	41.674	649.341395
9	Afghanistan	1997	22227415.0	Asia	41.763	635.341351
What is the shape of the data in the dataframe. (Number of Rows? Number of Columns?)

df.shape  # 1704 -rows and 6-columns
(1704, 6)
Select specific columns of your dataframe
Let’s say you want to print the "country", "year", and "pop" columns only. You should use this syntax:

df[["country", "year", "pop"]].head(10)
country	year	pop
0	Afghanistan	1952	8425333.0
1	Afghanistan	1957	9240934.0
2	Afghanistan	1962	10267083.0
3	Afghanistan	1967	11537966.0
4	Afghanistan	1972	13079460.0
5	Afghanistan	1977	14880372.0
6	Afghanistan	1982	12881816.0
7	Afghanistan	1987	13867957.0
8	Afghanistan	1992	16317921.0
9	Afghanistan	1997	22227415.0
NOTE: Any guesses why we have to use double bracket frames? It seems a bit over-complicated, I admit, but maybe this will help you remember: the outer bracket frames tell pandas that you want to select columns, and the inner brackets are for the list (remember? Python lists go between bracket frames) of the column names.

You can get a Series (Column) using this syntax (and selecting only one column):
df["country"].head(25)
0     Afghanistan
1     Afghanistan
2     Afghanistan
3     Afghanistan
4     Afghanistan
5     Afghanistan
6     Afghanistan
7     Afghanistan
8     Afghanistan
9     Afghanistan
10    Afghanistan
11    Afghanistan
12        Albania
13        Albania
14        Albania
15        Albania
16        Albania
17        Albania
18        Albania
19        Albania
20        Albania
21        Albania
22        Albania
23        Albania
24        Algeria
Name: country, dtype: object
# View unique values for Series (Column) values:
df["country"].unique()
array(['Afghanistan', 'Albania', 'Algeria', 'Angola', 'Argentina',
       'Australia', 'Austria', 'Bahrain', 'Bangladesh', 'Belgium',
       'Benin', 'Bolivia', 'Bosnia and Herzegovina', 'Botswana', 'Brazil',
       'Bulgaria', 'Burkina Faso', 'Burundi', 'Cambodia', 'Cameroon',
       'Canada', 'Central African Republic', 'Chad', 'Chile', 'China',
       'Colombia', 'Comoros', 'Congo Dem. Rep.', 'Congo Rep.',
       'Costa Rica', "Cote d'Ivoire", 'Croatia', 'Cuba', 'Czech Republic',
       'Denmark', 'Djibouti', 'Dominican Republic', 'Ecuador', 'Egypt',
       'El Salvador', 'Equatorial Guinea', 'Eritrea', 'Ethiopia',
       'Finland', 'France', 'Gabon', 'Gambia', 'Germany', 'Ghana',
       'Greece', 'Guatemala', 'Guinea', 'Guinea-Bissau', 'Haiti',
       'Honduras', 'Hong Kong China', 'Hungary', 'Iceland', 'India',
       'Indonesia', 'Iran', 'Iraq', 'Ireland', 'Israel', 'Italy',
       'Jamaica', 'Japan', 'Jordan', 'Kenya', 'Korea Dem. Rep.',
       'Korea Rep.', 'Kuwait', 'Lebanon', 'Lesotho', 'Liberia', 'Libya',
       'Madagascar', 'Malawi', 'Malaysia', 'Mali', 'Mauritania',
       'Mauritius', 'Mexico', 'Mongolia', 'Montenegro', 'Morocco',
       'Mozambique', 'Myanmar', 'Namibia', 'Nepal', 'Netherlands',
       'New Zealand', 'Nicaragua', 'Niger', 'Nigeria', 'Norway', 'Oman',
       'Pakistan', 'Panama', 'Paraguay', 'Peru', 'Philippines', 'Poland',
       'Portugal', 'Puerto Rico', 'Reunion', 'Romania', 'Rwanda',
       'Sao Tome and Principe', 'Saudi Arabia', 'Senegal', 'Serbia',
       'Sierra Leone', 'Singapore', 'Slovak Republic', 'Slovenia',
       'Somalia', 'South Africa', 'Spain', 'Sri Lanka', 'Sudan',
       'Swaziland', 'Sweden', 'Switzerland', 'Syria', 'Taiwan',
       'Tanzania', 'Thailand', 'Togo', 'Trinidad and Tobago', 'Tunisia',
       'Turkey', 'Uganda', 'United Kingdom', 'United States', 'Uruguay',
       'Venezuela', 'Vietnam', 'West Bank and Gaza', 'Yemen Rep.',
       'Zambia', 'Zimbabwe'], dtype=object)
Filter for specific values in your dataframe
Let’s say, you want to see a list of only the users who came from the ‘United Kingdom’. In this case you have to filter for the ‘United Kingdom’ value in the ‘country’ column:

df_uk_rows = df[df["country"]=="United Kingdom"]
df_uk_rows
country	year	pop	continent	lifeExp	gdpPercap
1596	United Kingdom	1952	50430000.0	Europe	69.180	9979.508487
1597	United Kingdom	1957	51430000.0	Europe	70.420	11283.177950
1598	United Kingdom	1962	53292000.0	Europe	70.760	12477.177070
1599	United Kingdom	1967	54959000.0	Europe	71.360	14142.850890
1600	United Kingdom	1972	56079000.0	Europe	72.010	15895.116410
1601	United Kingdom	1977	56179000.0	Europe	72.760	17428.748460
1602	United Kingdom	1982	56339704.0	Europe	74.040	18232.424520
1603	United Kingdom	1987	56981620.0	Europe	75.007	21664.787670
1604	United Kingdom	1992	57866349.0	Europe	76.420	22705.092540
1605	United Kingdom	1997	58808266.0	Europe	77.218	26074.531360
1606	United Kingdom	2002	59912431.0	Europe	78.471	29478.999190
1607	United Kingdom	2007	60776238.0	Europe	79.425	33203.261280
Functions can be used after each other
It’s very important to understand that pandas’s logic is very linear. So if you apply a function, you can always apply another one on it. In this case, the input of the latter function will always be the output of the previous function.

df.count().head()
country      1704
year         1704
pop          1704
continent    1704
lifeExp      1704
dtype: int64
df.mean().head()
year         1.979500e+03
pop          2.960121e+07
lifeExp      5.947444e+01
gdpPercap    7.215327e+03
dtype: float64
df["pop"].max()
1318683096.0
df["pop"].count()
1704
df[["lifeExp", "pop", "gdpPercap"]].max()
lifeExp      8.260300e+01
pop          1.318683e+09
gdpPercap    1.135231e+05
dtype: float64
df[["country","lifeExp", "pop", "gdpPercap"]].head()
country	lifeExp	pop	gdpPercap
0	Afghanistan	28.801	8425333.0	779.445314
1	Afghanistan	30.332	9240934.0	820.853030
2	Afghanistan	31.997	10267083.0	853.100710
3	Afghanistan	34.020	11537966.0	836.197138
4	Afghanistan	36.088	13079460.0	739.981106
Grouping in pandas
# Pandas .groupby in action
df.groupby("country").mean()
year	pop	lifeExp	gdpPercap
country				
Afghanistan	1979.5	1.582372e+07	37.478833	802.674598
Albania	1979.5	2.580249e+06	68.432917	3255.366633
Algeria	1979.5	1.987541e+07	59.030167	4426.025973
Angola	1979.5	7.309390e+06	37.883500	3607.100529
Argentina	1979.5	2.860224e+07	69.060417	8955.553783
Australia	1979.5	1.464931e+07	74.662917	19980.595634
Austria	1979.5	7.583298e+06	73.103250	20411.916279
Bahrain	1979.5	3.739132e+05	65.605667	18077.663945
Bangladesh	1979.5	9.075540e+07	49.834083	817.558818
Belgium	1979.5	9.725119e+06	73.641750	19900.758072
Benin	1979.5	4.017497e+06	48.779917	1155.395107
Bolivia	1979.5	5.610395e+06	52.504583	2961.228754
Bosnia and Herzegovina	1979.5	3.816525e+06	67.707833	3484.779069
Botswana	1979.5	9.711862e+05	54.597500	5031.503557
Brazil	1979.5	1.223121e+08	62.239500	5829.316653
Bulgaria	1979.5	8.182985e+06	69.743750	6384.055172
Burkina Faso	1979.5	7.548677e+06	44.694000	843.990665
Burundi	1979.5	4.651608e+06	44.817333	471.662990
Cambodia	1979.5	8.510431e+06	47.902750	675.367824
Cameroon	1979.5	9.816648e+06	48.128500	1774.634222
Canada	1979.5	2.446297e+07	74.902750	22410.746340
Central African Republic	1979.5	2.560963e+06	43.866917	958.784697
Chad	1979.5	5.329256e+06	46.773583	1165.453674
Chile	1979.5	1.120573e+07	67.430917	6703.289147
China	1979.5	9.581601e+08	61.785140	1488.307694
Colombia	1979.5	2.725610e+07	63.897750	4195.342920
Comoros	1979.5	3.616839e+05	52.381750	1314.380339
Congo Dem. Rep.	1979.5	3.268166e+07	44.543750	648.342646
Congo Rep.	1979.5	1.923209e+06	52.501917	3312.788215
Costa Rica	1979.5	2.400008e+06	70.181417	5448.610779
...	...	...	...	...
Sierra Leone	1979.5	3.605425e+06	36.769167	1072.819493
Singapore	1979.5	2.667817e+06	71.220250	17425.382267
Slovak Republic	1979.5	4.774507e+06	70.696083	10415.530689
Slovenia	1979.5	1.794381e+06	71.600750	14074.582109
Somalia	1979.5	5.197198e+06	40.988667	1140.793252
South Africa	1979.5	2.992835e+07	53.993167	7247.431074
Spain	1979.5	3.585180e+07	74.203417	14029.826479
Sri Lanka	1979.5	1.454583e+07	66.526083	1854.731119
Sudan	1979.5	2.156033e+07	48.400500	1835.010430
Swaziland	1979.5	6.790520e+05	49.002417	3163.352358
Sweden	1979.5	8.220029e+06	76.177000	19943.126104
Switzerland	1979.5	6.384293e+06	75.565083	27074.334405
Syria	1979.5	9.865379e+06	61.346167	3009.287981
Taiwan	1979.5	1.687472e+07	70.336667	10224.807181
Tanzania	1979.5	2.049950e+07	47.912333	849.281271
Thailand	1979.5	4.496163e+07	62.200250	3045.966474
Togo	1979.5	2.895964e+06	51.498750	1153.820116
Trinidad and Tobago	1979.5	1.006470e+06	66.828000	7866.871946
Tunisia	1979.5	6.686770e+06	60.721000	3477.210351
Turkey	1979.5	4.590901e+07	59.696417	4469.453380
Uganda	1979.5	1.436105e+07	47.618833	810.383788
United Kingdom	1979.5	5.608780e+07	73.922583	19380.472986
United States	1979.5	2.282112e+08	73.478500	26261.151347
Uruguay	1979.5	2.912487e+06	70.781583	7100.133176
Venezuela	1979.5	1.512980e+07	66.580667	10088.516252
Vietnam	1979.5	5.456857e+07	57.479500	1017.712615
West Bank and Gaza	1979.5	1.848606e+06	60.328667	3759.996781
Yemen Rep.	1979.5	1.084319e+07	46.780417	1569.274672
Zambia	1979.5	6.353805e+06	45.996333	1358.199409
Zimbabwe	1979.5	7.641966e+06	52.663167	635.858042
142 rows × 4 columns

df_uk_rows.groupby("country").mean()
year	pop	lifeExp	gdpPercap
country				
United Kingdom	1979.5	5.608780e+07	73.922583	19380.472986
Note: You can either ignore the year column, or you can remove it afterwards by using this syntax:

df_uk_rows.groupby("country").mean()[["pop","lifeExp","gdpPercap"]]
pop	lifeExp	gdpPercap
country			
United Kingdom	5.608780e+07	73.922583	19380.472986
df.groupby("continent").count()
country	year	pop	lifeExp	gdpPercap
continent					
Africa	624	624	624	624	624
Americas	300	300	300	300	300
Asia	396	396	396	396	396
Europe	360	360	360	360	360
Oceania	24	24	24	24	24
df[df["continent"] == "Oceania"].groupby("country").mean()
year	pop	lifeExp	gdpPercap
country				
Australia	1979.5	1.464931e+07	74.662917	19980.595634
New Zealand	1979.5	3.100032e+06	73.989500	17262.622813
 
```
