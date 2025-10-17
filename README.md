# operations-on-diamond-dataset

AIM:
    To perform the following operations on diamond dataset in 'https://raw.githubusercontent.com/mwaskom/seaborn-data/master/diamonds.csv'

    
S.No  |  Operation Description                                                          
------+---------------------------------------------------------------------------------
1     |  Read CSV and print first 5 rows                                                
2     |  Modify default column values and print first 6 rows                            
3     |  Select a Series from the DataFrame                                             
4     |  Create a new 'Quality‑color' Series                                            
5     |  Count rows, columns, and data types                                            
6     |  Summarize only 'object' columns                                                
7     |  Rename two of the columns                                                      
8     |  Rename all columns                                                             
9     |  Remove the second column                                                       
10    |  Remove multiple columns at once                                                
11    |  Remove multiple rows at once                                                   
12    |  Sort the 'cut' Series in ascending order                                       
13    |  Sort the 'price' Series in descending order                                    
14    |  Sort entire DataFrame by 'carat' (ascending and descending)                    
15    |  Filter rows where carat weight ≥ 0.3                                           
16    |  Convert Python list to Pandas Series                                           
17    |  Find diamonds where x > 5, y > 5, z > 5                                        
18    |  Find diamonds that are either Premium or Ideal                                 
19    |  Find diamonds that are Fair, Good, or Premium                                  
20    |  Display all column labels                                                      
21    |  Read only a subset of 3 rows                                                   
22    |  Iterate through the DataFrame                                                  
23    |  Drop all non‑numeric columns                                                   
24    |  Include only numeric columns                                                   
25    |  Describe only certain data types                                               
26    |  Calculate mean of each numeric column                                          
27    |  Calculate mean of each row                                                     
28    |  Calculate mean price for each cut                                              
29    |  Calculate count, minimum, and maximum price for each cut                       
30    |  Create a side‑by‑side bar plot                                                 
31    |  Count occurrences in 'cut' Series                                              
32    |  Display percentages for each 'cut' value                                       
33    |  Display unique values in 'cut' Series                                          
34    |  Count number of unique 'cut' values                                            
35    |  Compute cross‑tabulation of two Series                                         
36    |  Calculate summary statistics of 'cut' Series                                   
37    |  Create a histogram of 'carat' Series                                           
38    |  Create a bar plot of 'value_counts' for 'cut' Series                           
39    |  Create a boolean DataFrame indicating missing values                           
40    |  Count missing values in each Series                                            
41    |  Drop rows with any missing values and check shape                              
42    |  Drop rows if any/all missing in two specific columns                           
43    |  Set an existing column as index                                                
44    |  Set column as index and restore the index name                                 
45    |  Access a specified Series index and values                                     
46    |  Sort a Series by values and index                                              
47    |  Calculate product of x, y, and z for each diamond                              
48    |  Concatenate DataFrame with 'color' Series                                      
49    |  Read specified rows and all columns                                            
50    |  Read rows 0, 5, 7 and all columns                                              
51    |  Read rows 2 through 5 and all columns                                          
52    |  Read rows 0 through 2, columns 'color' and 'price'                             
53    |  Read rows 0 through 2, columns 'color' through 'price' (inclusive)             
54    |  Read rows where 'cut' is 'Premium', column 'color'                             
55    |  Read rows in positions 0 and 1, columns in positions 0 and 3                   
56    |  Read rows in positions 0 through 4, columns in positions 1 through 4           
57    |  Read rows in positions 0 through 4 (exclusive) and all columns                 
58    |  Read rows 2 through 5 (inclusive), columns in positions 0 through 2 (exclusive)
59    |  Print concise summary of DataFrame                                             
60    |  Get true memory usage of DataFrame                                             
61    |  Calculate memory usage for each Series                                         
62    |  Randomly sample rows from DataFrame                                            
63    |  Sample 75% of rows without replacement and store 25% separately                
64    |  Detect duplicate 'color' entries                                               
65    |  Count duplicate rows in DataFrame   
-----------------------------------------------------------------------------------------

PROGRAM:
```
import pandas as pd

# Load the Diamonds dataset
print("Loading Diamonds dataset...")
diamonds = pd.read_csv('https://raw.githubusercontent.com/mwaskom/seaborn-data/master/diamonds.csv')

print("\n1. Read CSV and Print First 5 Rows")
print(diamonds.head())

print("\n2. Modify Default Column Values and Print First 6 Rows")
diamonds2 = diamonds.rename(columns={col: col.upper() for col in diamonds.columns})
print(diamonds2.head(6))

print("\n3. Select a Series from Diamonds DataFrame")
print(diamonds['price'])

print("\n4. Create a New 'Quality -color' Series")
diamonds['Quality -color'] = diamonds['cut'] + '-' + diamonds['color']
print(diamonds['Quality -color'].head())

print("\n5. Count Rows, Columns, and Data Types")
print("Shape:", diamonds.shape)
print("Dtypes:\n", diamonds.dtypes)

print("\n6. Summarize Only 'Object' Columns")
print(diamonds.select_dtypes(include='object').describe())

print("\n7. Rename Two Columns")
print(diamonds.rename(columns={'cut': 'diamond_cut', 'color': 'diamond_color'}).head())

print("\n8. Rename All Columns")
print(diamonds.rename(columns={col: col+'_feature' for col in diamonds.columns}).head())

print("\n9. Remove the Second Column")
print(diamonds.drop(columns=[diamonds.columns[1]]).head())

print("\n10. Remove Multiple Columns at Once")
print(diamonds.drop(columns=['cut', 'color', 'clarity']).head())

print("\n11. Remove Multiple Rows at Once")
print(diamonds.drop([0,2,4], axis=0).head())

print("\n12. Sort the 'cut' Series in Ascending Order")
print(diamonds['cut'].sort_values().head())

print("\n13. Sort the 'price' Series in Descending Order")
print(diamonds['price'].sort_values(ascending=False).head())

print("\n14. Sort Entire DataFrame by 'carat' (ascending and descending)")
print("Ascending:\n", diamonds.sort_values('carat').head())
print("Descending:\n", diamonds.sort_values('carat', ascending=False).head())

print("\n15. Filter Rows with Carat Weight at Least 0.3")
print(diamonds[diamonds['carat'] >= 0.3].head())

print("\n16. Convert Python List to Pandas Series")
py_list = [1, 2, 3, 4, 5]
print(pd.Series(py_list))

print("\n17. Diamonds Where x > 5, y > 5, z > 5")
print(diamonds[(diamonds['x'] > 5) & (diamonds['y'] > 5) & (diamonds['z'] > 5)].head())

print("\n18. Diamonds that are either Premium or Ideal")
print(diamonds[diamonds['cut'].isin(['Premium','Ideal'])].head())

print("\n19. Diamonds with Fair, Good, or Premium Cut")
print(diamonds[diamonds['cut'].isin(['Fair','Good','Premium'])].head())

print("\n20. Display All Column Labels")
print(diamonds.columns)

print("\n21. Read Only a Subset of 3 Rows")
print(diamonds.head(3))

print("\n22. Iterate Through Diamonds DataFrame")
for index, row in diamonds.iterrows():
    print(index, row['price'])
    if index>=4: break

print("\n23. Drop All Non-Numeric Columns")
print(diamonds.select_dtypes(exclude='object').head())

print("\n24. Include Only Numeric Columns")
print(diamonds.select_dtypes(include='number').head())

print("\n25. Describe Only Certain Data Types")
print("Numeric:\n", diamonds.describe(include=['number']))
print("Object:\n", diamonds.describe(include=['object']))

print("\n26. Calculate Mean of Each Numeric Column")
print(diamonds.select_dtypes(include='number').mean())

print("\n27. Calculate Mean of Each Row")
print(diamonds.select_dtypes(include='number').mean(axis=1).head())

print("\n28. Calculate Mean of Price for Each Cut")
print(diamonds.groupby('cut')['price'].mean())

print("\n29. Calculate Count, Min, Max Price for Each Cut")
print(diamonds.groupby('cut')['price'].agg(['count','min','max']))

print("\n30. Create Side-by-Side Bar Plot (code only)")
print("diamonds.groupby('cut')[['price','carat']].mean().plot.bar()")

print("\n31. Count Occurrences in 'cut' Series")
print(diamonds['cut'].value_counts())

print("\n32. Display Percentages for 'cut' Series Values")
print(diamonds['cut'].value_counts(normalize=True)*100)

print("\n33. Display Unique Values in 'cut' Series")
print(diamonds['cut'].unique())

print("\n34. Count Number of Unique Values in 'cut' Series")
print(diamonds['cut'].nunique())

print("\n35. Compute Cross-Tabulation of Two Series")
print(pd.crosstab(diamonds['cut'], diamonds['color']))

print("\n36. Calculate Summary Statistics of 'cut' Series")
print(diamonds['cut'].describe())

print("\n37. Create a Histogram of the 'carat' Series (code only)")
print("diamonds['carat'].hist()")

print("\n38. Create a Bar Plot of 'value_counts' for 'cut' Series (code only)")
print("diamonds['cut'].value_counts().plot.bar()")

print("\n39. Boolean DataFrame Indicating Missing Values")
print(diamonds.isnull().head())

print("\n40. Count Missing Values in Each Series")
print(diamonds.isnull().sum())

print("\n41. Drop Rows with Any Missing Values and Check Shape")
print(diamonds.dropna().shape)

print("\n42. Drop Row if Any or All Values Missing in Two Specific Columns")
print("Drop rows with any missing in 'cut' or 'color':", diamonds.dropna(subset=['cut','color']).shape)
print("Drop rows with all missing in 'cut' or 'color':", diamonds.dropna(subset=['cut','color'], how='all').shape)

print("\n43. Set an Existing Column as the Index")
print(diamonds.set_index('cut').head())

print("\n44. Set Column as Index and Restore the Index Name")
df_indexed = diamonds.set_index('color')
print(df_indexed.reset_index().head())

print("\n45. Access a Specified Series Index and Values")
ser = diamonds['color']
print("Index:", ser.index, "Values:", ser.values[:5])

print("\n46. Sort a Series by Its Values and Index")
print("Sorted by values:\n", diamonds['price'].sort_values().head())
print("Sorted by index:\n", diamonds['price'].sort_index().head())

print("\n47. Product of x, y, and z for Each Diamond")
diamonds['xyz_prod'] = diamonds['x']*diamonds['y']*diamonds['z']
print(diamonds['xyz_prod'].head())

print("\n48. Concatenate Diamonds DataFrame with the 'color' Series")
print(pd.concat([diamonds, diamonds['color']], axis=1).head())

print("\n49. Read Specified Rows and All Columns")
print(diamonds.loc[[1,2]].head())

print("\n50. Read Rows 0, 5, 7 and All Columns")
print(diamonds.loc[[0,5,7]].head())

print("\n51. Read Rows 2 Through 5 and All Columns")
print(diamonds.loc[2:5])

print("\n52. Read Rows 0 Through 2, Columns 'color' and 'price'")
print(diamonds.loc[0:2, ['color', 'price']])

print("\n53. Read Rows 0-2, Columns 'color' Through 'price' (inclusive)")
cols_order = list(diamonds.columns)
print(diamonds.loc[0:2, cols_order[cols_order.index('color'):cols_order.index('price')+1]])

print("\n54. Rows Where 'cut' is 'Premium', Column 'color'")
print(diamonds.loc[diamonds['cut']=='Premium','color'].head())

print("\n55. Rows 0,1, Columns 0,3")
print(diamonds.iloc[[0,1],[0,3]])

print("\n56. Rows 0-4 (inclusive), Columns 1-4")
print(diamonds.iloc[0:5, 1:5])

print("\n57. Rows 0-4 (exclusive) and All Columns")
print(diamonds.iloc[0:4,:])

print("\n58. Rows 2-5 (inclusive), Columns 0-2 (exclusive)")
print(diamonds.iloc[2:6,0:2])

print("\n59. Print Concise Summary")
diamonds.info()

print("\n60. Get True Memory Usage of Diamonds DataFrame")
print(diamonds.memory_usage(deep=True).sum())

print("\n61. Calculate Memory Usage for Each Series in Diamonds DataFrame")
print(diamonds.memory_usage(deep=True))

print("\n62. Randomly Sample Rows from Diamonds DataFrame")
print(diamonds.sample(3))

print("\n63. Sample 75% of Rows Without Replacement and Store 25% Separately")
sampled = diamonds.sample(frac=0.75, random_state=42, replace=False)
not_sampled = diamonds.drop(sampled.index)
print("Sampled shape:", sampled.shape, "Remaining shape:", not_sampled.shape)

print("\n64. Detect Duplicate 'color'")
print(diamonds['color'].duplicated().head())

print("\n65. Count Duplicate Rows in Diamonds DataFrame")
print(diamonds.duplicated().sum())

```

OUTPUT:
```

Loading Diamonds dataset...

1. Read CSV and Print First 5 Rows
   carat      cut color clarity  depth  table  price     x     y     z
0   0.23    Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31
3   0.29  Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63
4   0.31     Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75

2. Modify Default Column Values and Print First 6 Rows
   CARAT        CUT COLOR CLARITY  DEPTH  TABLE  PRICE     X     Y     Z
0   0.23      Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43
1   0.21    Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31
2   0.23       Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31
3   0.29    Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63
4   0.31       Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75
5   0.24  Very Good     J    VVS2   62.8   57.0    336  3.94  3.96  2.48

3. Select a Series from Diamonds DataFrame
0         326
1         326
2         327
3         334
4         335
         ... 
53935    2757
53936    2757
53937    2757
53938    2757
53939    2757
Name: price, Length: 53940, dtype: int64

4. Create a New 'Quality -color' Series
0      Ideal-E
1    Premium-E
2       Good-E
3    Premium-I
4       Good-J
Name: Quality -color, dtype: object

5. Count Rows, Columns, and Data Types
Shape: (53940, 11)
Dtypes:
 carat             float64
cut                object
color              object
clarity            object
depth             float64
table             float64
price               int64
x                 float64
y                 float64
z                 float64
Quality -color     object
dtype: object

6. Summarize Only 'Object' Columns
          cut  color clarity Quality -color
count   53940  53940   53940          53940
unique      5      7       8             35
top     Ideal      G     SI1        Ideal-G
freq    21551  11292   13065           4884

7. Rename Two Columns
   carat diamond_cut diamond_color clarity  depth  table  price     x     y  \
0   0.23       Ideal             E     SI2   61.5   55.0    326  3.95  3.98   
1   0.21     Premium             E     SI1   59.8   61.0    326  3.89  3.84   
2   0.23        Good             E     VS1   56.9   65.0    327  4.05  4.07   
3   0.29     Premium             I     VS2   62.4   58.0    334  4.20  4.23   
4   0.31        Good             J     SI2   63.3   58.0    335  4.34  4.35   

      z Quality -color  
0  2.43        Ideal-E  
1  2.31      Premium-E  
2  2.31         Good-E  
3  2.63      Premium-I  
4  2.75         Good-J  

8. Rename All Columns
   carat_feature cut_feature color_feature clarity_feature  depth_feature  \
0           0.23       Ideal             E             SI2           61.5   
1           0.21     Premium             E             SI1           59.8   
2           0.23        Good             E             VS1           56.9   
3           0.29     Premium             I             VS2           62.4   
4           0.31        Good             J             SI2           63.3   

   table_feature  price_feature  x_feature  y_feature  z_feature  \
0           55.0            326       3.95       3.98       2.43   
1           61.0            326       3.89       3.84       2.31   
2           65.0            327       4.05       4.07       2.31   
3           58.0            334       4.20       4.23       2.63   
4           58.0            335       4.34       4.35       2.75   

  Quality -color_feature  
0                Ideal-E  
1              Premium-E  
2                 Good-E  
3              Premium-I  
4                 Good-J  

9. Remove the Second Column
   carat color clarity  depth  table  price     x     y     z Quality -color
0   0.23     E     SI2   61.5   55.0    326  3.95  3.98  2.43        Ideal-E
1   0.21     E     SI1   59.8   61.0    326  3.89  3.84  2.31      Premium-E
2   0.23     E     VS1   56.9   65.0    327  4.05  4.07  2.31         Good-E
3   0.29     I     VS2   62.4   58.0    334  4.20  4.23  2.63      Premium-I
4   0.31     J     SI2   63.3   58.0    335  4.34  4.35  2.75         Good-J

10. Remove Multiple Columns at Once
   carat  depth  table  price     x     y     z Quality -color
0   0.23   61.5   55.0    326  3.95  3.98  2.43        Ideal-E
1   0.21   59.8   61.0    326  3.89  3.84  2.31      Premium-E
2   0.23   56.9   65.0    327  4.05  4.07  2.31         Good-E
3   0.29   62.4   58.0    334  4.20  4.23  2.63      Premium-I
4   0.31   63.3   58.0    335  4.34  4.35  2.75         Good-J

11. Remove Multiple Rows at Once
   carat        cut color clarity  depth  table  price     x     y     z  \
1   0.21    Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
3   0.29    Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
5   0.24  Very Good     J    VVS2   62.8   57.0    336  3.94  3.96  2.48   
6   0.24  Very Good     I    VVS1   62.3   57.0    336  3.95  3.98  2.47   
7   0.26  Very Good     H     SI1   61.9   55.0    337  4.07  4.11  2.53   

  Quality -color  
1      Premium-E  
3      Premium-I  
5    Very Good-J  
6    Very Good-I  
7    Very Good-H  

12. Sort the 'cut' Series in Ascending Order
3850     Fair
51464    Fair
51466    Fair
10237    Fair
10760    Fair
Name: cut, dtype: object

13. Sort the 'price' Series in Descending Order
27749    18823
27748    18818
27747    18806
27746    18804
27745    18803
Name: price, dtype: int64

14. Sort Entire DataFrame by 'carat' (ascending and descending)
Ascending:
        carat      cut color clarity  depth  table  price     x     y     z  \
14       0.2  Premium     E     SI2   60.2   62.0    345  3.79  3.75  2.27   
31597    0.2    Ideal     D     VS2   61.5   57.0    367  3.81  3.77  2.33   
31596    0.2  Premium     F     VS2   62.6   59.0    367  3.73  3.71  2.33   
31595    0.2    Ideal     E     VS2   59.7   55.0    367  3.86  3.84  2.30   
31594    0.2  Premium     E     VS2   59.7   62.0    367  3.84  3.80  2.28   

      Quality -color  
14         Premium-E  
31597        Ideal-D  
31596      Premium-F  
31595        Ideal-E  
31594      Premium-E  
Descending:
        carat      cut color clarity  depth  table  price      x      y     z  \
27415   5.01     Fair     J      I1   65.5   59.0  18018  10.74  10.54  6.98   
27630   4.50     Fair     J      I1   65.8   58.0  18531  10.23  10.16  6.72   
27130   4.13     Fair     H      I1   64.8   61.0  17329  10.00   9.85  6.43   
25999   4.01  Premium     J      I1   62.5   62.0  15223  10.02   9.94  6.24   
25998   4.01  Premium     I      I1   61.0   61.0  15223  10.14  10.10  6.17   

      Quality -color  
27415         Fair-J  
27630         Fair-J  
27130         Fair-H  
25999      Premium-J  
25998      Premium-I  

15. Filter Rows with Carat Weight at Least 0.3
    carat      cut color clarity  depth  table  price     x     y     z  \
4    0.31     Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75   
10   0.30     Good     J     SI1   64.0   55.0    339  4.25  4.28  2.73   
13   0.31    Ideal     J     SI2   62.2   54.0    344  4.35  4.37  2.71   
15   0.32  Premium     E      I1   60.9   58.0    345  4.38  4.42  2.68   
16   0.30    Ideal     I     SI2   62.0   54.0    348  4.31  4.34  2.68   

   Quality -color  
4          Good-J  
10         Good-J  
13        Ideal-J  
15      Premium-E  
16        Ideal-I  

16. Convert Python List to Pandas Series
0    1
1    2
2    3
3    4
4    5
dtype: int64

17. Diamonds Where x > 5, y > 5, z > 5
       carat   cut color clarity  depth  table  price     x     y     z  \
11778   1.83  Fair     J      I1   70.0   58.0   5083  7.34  7.28  5.12   
13002   2.14  Fair     J      I1   69.4   57.0   5405  7.74  7.70  5.36   
13118   2.15  Fair     J      I1   65.5   57.0   5430  8.01  7.95  5.23   
13562   1.96  Fair     F      I1   66.6   60.0   5554  7.59  7.56  5.04   
13757   2.22  Fair     J      I1   66.7   56.0   5607  8.04  8.02  5.36   

      Quality -color  
11778         Fair-J  
13002         Fair-J  
13118         Fair-J  
13562         Fair-F  
13757         Fair-J  

18. Diamonds that are either Premium or Ideal
    carat      cut color clarity  depth  table  price     x     y     z  \
0    0.23    Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
1    0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
3    0.29  Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
11   0.23    Ideal     J     VS1   62.8   56.0    340  3.93  3.90  2.46   
12   0.22  Premium     F     SI1   60.4   61.0    342  3.88  3.84  2.33   

   Quality -color  
0         Ideal-E  
1       Premium-E  
3       Premium-I  
11        Ideal-J  
12      Premium-F  

19. Diamonds with Fair, Good, or Premium Cut
   carat      cut color clarity  depth  table  price     x     y     z  \
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   
3   0.29  Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
4   0.31     Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75   
8   0.22     Fair     E     VS2   65.1   61.0    337  3.87  3.78  2.49   

  Quality -color  
1      Premium-E  
2         Good-E  
3      Premium-I  
4         Good-J  
8         Fair-E  

20. Display All Column Labels
Index(['carat', 'cut', 'color', 'clarity', 'depth', 'table', 'price', 'x', 'y',
       'z', 'Quality -color'],
      dtype='object')

21. Read Only a Subset of 3 Rows
   carat      cut color clarity  depth  table  price     x     y     z  \
0   0.23    Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   

  Quality -color  
0        Ideal-E  
1      Premium-E  
2         Good-E  

22. Iterate Through Diamonds DataFrame
0 326
1 326
2 327
3 334
4 335

23. Drop All Non-Numeric Columns
   carat  depth  table  price     x     y     z
0   0.23   61.5   55.0    326  3.95  3.98  2.43
1   0.21   59.8   61.0    326  3.89  3.84  2.31
2   0.23   56.9   65.0    327  4.05  4.07  2.31
3   0.29   62.4   58.0    334  4.20  4.23  2.63
4   0.31   63.3   58.0    335  4.34  4.35  2.75

24. Include Only Numeric Columns
   carat  depth  table  price     x     y     z
0   0.23   61.5   55.0    326  3.95  3.98  2.43
1   0.21   59.8   61.0    326  3.89  3.84  2.31
2   0.23   56.9   65.0    327  4.05  4.07  2.31
3   0.29   62.4   58.0    334  4.20  4.23  2.63
4   0.31   63.3   58.0    335  4.34  4.35  2.75

25. Describe Only Certain Data Types
Numeric:
               carat         depth         table         price             x  \
count  53940.000000  53940.000000  53940.000000  53940.000000  53940.000000   
mean       0.797940     61.749405     57.457184   3932.799722      5.731157   
std        0.474011      1.432621      2.234491   3989.439738      1.121761   
min        0.200000     43.000000     43.000000    326.000000      0.000000   
25%        0.400000     61.000000     56.000000    950.000000      4.710000   
50%        0.700000     61.800000     57.000000   2401.000000      5.700000   
75%        1.040000     62.500000     59.000000   5324.250000      6.540000   
max        5.010000     79.000000     95.000000  18823.000000     10.740000   

                  y             z  
count  53940.000000  53940.000000  
mean       5.734526      3.538734  
std        1.142135      0.705699  
min        0.000000      0.000000  
25%        4.720000      2.910000  
50%        5.710000      3.530000  
75%        6.540000      4.040000  
max       58.900000     31.800000  
Object:
           cut  color clarity Quality -color
count   53940  53940   53940          53940
unique      5      7       8             35
top     Ideal      G     SI1        Ideal-G
freq    21551  11292   13065           4884

26. Calculate Mean of Each Numeric Column
carat       0.797940
depth      61.749405
table      57.457184
price    3932.799722
x           5.731157
y           5.734526
z           3.538734
dtype: float64

27. Calculate Mean of Each Row
0    64.727143
1    65.292857
2    65.651429
3    66.535714
4    66.864286
dtype: float64

28. Calculate Mean of Price for Each Cut
cut
Fair         4358.757764
Good         3928.864452
Ideal        3457.541970
Premium      4584.257704
Very Good    3981.759891
Name: price, dtype: float64

29. Calculate Count, Min, Max Price for Each Cut
           count  min    max
cut                         
Fair        1610  337  18574
Good        4906  327  18788
Ideal      21551  326  18806
Premium    13791  326  18823
Very Good  12082  336  18818

30. Create Side-by-Side Bar Plot (code only)
diamonds.groupby('cut')[['price','carat']].mean().plot.bar()

31. Count Occurrences in 'cut' Series
cut
Ideal        21551
Premium      13791
Very Good    12082
Good          4906
Fair          1610
Name: count, dtype: int64

32. Display Percentages for 'cut' Series Values
cut
Ideal        39.953652
Premium      25.567297
Very Good    22.398962
Good          9.095291
Fair          2.984798
Name: proportion, dtype: float64

33. Display Unique Values in 'cut' Series
['Ideal' 'Premium' 'Good' 'Very Good' 'Fair']

34. Count Number of Unique Values in 'cut' Series
5

35. Compute Cross-Tabulation of Two Series
color         D     E     F     G     H     I    J
cut                                               
Fair        163   224   312   314   303   175  119
Good        662   933   909   871   702   522  307
Ideal      2834  3903  3826  4884  3115  2093  896
Premium    1603  2337  2331  2924  2360  1428  808
Very Good  1513  2400  2164  2299  1824  1204  678

36. Calculate Summary Statistics of 'cut' Series
count     53940
unique        5
top       Ideal
freq      21551
Name: cut, dtype: object

37. Create a Histogram of the 'carat' Series (code only)
diamonds['carat'].hist()

38. Create a Bar Plot of 'value_counts' for 'cut' Series (code only)
diamonds['cut'].value_counts().plot.bar()

39. Boolean DataFrame Indicating Missing Values
   carat    cut  color  clarity  depth  table  price      x      y      z  \
0  False  False  False    False  False  False  False  False  False  False   
1  False  False  False    False  False  False  False  False  False  False   
2  False  False  False    False  False  False  False  False  False  False   
3  False  False  False    False  False  False  False  False  False  False   
4  False  False  False    False  False  False  False  False  False  False   

   Quality -color  
0           False  
1           False  
2           False  
3           False  
4           False  

40. Count Missing Values in Each Series
carat             0
cut               0
color             0
clarity           0
depth             0
table             0
price             0
x                 0
y                 0
z                 0
Quality -color    0
dtype: int64

41. Drop Rows with Any Missing Values and Check Shape
(53940, 11)

42. Drop Row if Any or All Values Missing in Two Specific Columns
Drop rows with any missing in 'cut' or 'color': (53940, 11)
Drop rows with all missing in 'cut' or 'color': (53940, 11)

43. Set an Existing Column as the Index
         carat color clarity  depth  table  price     x     y     z  \
cut                                                                   
Ideal     0.23     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
Premium   0.21     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
Good      0.23     E     VS1   56.9   65.0    327  4.05  4.07  2.31   
Premium   0.29     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
Good      0.31     J     SI2   63.3   58.0    335  4.34  4.35  2.75   

        Quality -color  
cut                     
Ideal          Ideal-E  
Premium      Premium-E  
Good            Good-E  
Premium      Premium-I  
Good            Good-J  

44. Set Column as Index and Restore the Index Name
  color  carat      cut clarity  depth  table  price     x     y     z  \
0     E   0.23    Ideal     SI2   61.5   55.0    326  3.95  3.98  2.43   
1     E   0.21  Premium     SI1   59.8   61.0    326  3.89  3.84  2.31   
2     E   0.23     Good     VS1   56.9   65.0    327  4.05  4.07  2.31   
3     I   0.29  Premium     VS2   62.4   58.0    334  4.20  4.23  2.63   
4     J   0.31     Good     SI2   63.3   58.0    335  4.34  4.35  2.75   

  Quality -color  
0        Ideal-E  
1      Premium-E  
2         Good-E  
3      Premium-I  
4         Good-J  

45. Access a Specified Series Index and Values
Index: RangeIndex(start=0, stop=53940, step=1) Values: ['E' 'E' 'E' 'I' 'J']

46. Sort a Series by Its Values and Index
Sorted by values:
 0    326
1    326
2    327
3    334
4    335
Name: price, dtype: int64
Sorted by index:
 0    326
1    326
2    327
3    334
4    335
Name: price, dtype: int64

47. Product of x, y, and z for Each Diamond
0    38.202030
1    34.505856
2    38.076885
3    46.724580
4    51.917250
Name: xyz_prod, dtype: float64

48. Concatenate Diamonds DataFrame with the 'color' Series
   carat      cut color clarity  depth  table  price     x     y     z  \
0   0.23    Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   
3   0.29  Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
4   0.31     Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75   

  Quality -color   xyz_prod color  
0        Ideal-E  38.202030     E  
1      Premium-E  34.505856     E  
2         Good-E  38.076885     E  
3      Premium-I  46.724580     I  
4         Good-J  51.917250     J  

49. Read Specified Rows and All Columns
   carat      cut color clarity  depth  table  price     x     y     z  \
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   

  Quality -color   xyz_prod  
1      Premium-E  34.505856  
2         Good-E  38.076885  

50. Read Rows 0, 5, 7 and All Columns
   carat        cut color clarity  depth  table  price     x     y     z  \
0   0.23      Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
5   0.24  Very Good     J    VVS2   62.8   57.0    336  3.94  3.96  2.48   
7   0.26  Very Good     H     SI1   61.9   55.0    337  4.07  4.11  2.53   

  Quality -color   xyz_prod  
0        Ideal-E  38.202030  
5    Very Good-J  38.693952  
7    Very Good-H  42.321081  

51. Read Rows 2 Through 5 and All Columns
   carat        cut color clarity  depth  table  price     x     y     z  \
2   0.23       Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   
3   0.29    Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   
4   0.31       Good     J     SI2   63.3   58.0    335  4.34  4.35  2.75   
5   0.24  Very Good     J    VVS2   62.8   57.0    336  3.94  3.96  2.48   

  Quality -color   xyz_prod  
2         Good-E  38.076885  
3      Premium-I  46.724580  
4         Good-J  51.917250  
5    Very Good-J  38.693952  

52. Read Rows 0 Through 2, Columns 'color' and 'price'
  color  price
0     E    326
1     E    326
2     E    327

53. Read Rows 0-2, Columns 'color' Through 'price' (inclusive)
  color clarity  depth  table  price
0     E     SI2   61.5   55.0    326
1     E     SI1   59.8   61.0    326
2     E     VS1   56.9   65.0    327

54. Rows Where 'cut' is 'Premium', Column 'color'
1     E
3     I
12    F
14    E
15    E
Name: color, dtype: object

55. Rows 0,1, Columns 0,3
   carat clarity
0   0.23     SI2
1   0.21     SI1

56. Rows 0-4 (inclusive), Columns 1-4
       cut color clarity  depth
0    Ideal     E     SI2   61.5
1  Premium     E     SI1   59.8
2     Good     E     VS1   56.9
3  Premium     I     VS2   62.4
4     Good     J     SI2   63.3

57. Rows 0-4 (exclusive) and All Columns
   carat      cut color clarity  depth  table  price     x     y     z  \
0   0.23    Ideal     E     SI2   61.5   55.0    326  3.95  3.98  2.43   
1   0.21  Premium     E     SI1   59.8   61.0    326  3.89  3.84  2.31   
2   0.23     Good     E     VS1   56.9   65.0    327  4.05  4.07  2.31   
3   0.29  Premium     I     VS2   62.4   58.0    334  4.20  4.23  2.63   

  Quality -color   xyz_prod  
0        Ideal-E  38.202030  
1      Premium-E  34.505856  
2         Good-E  38.076885  
3      Premium-I  46.724580  

58. Rows 2-5 (inclusive), Columns 0-2 (exclusive)
   carat        cut
2   0.23       Good
3   0.29    Premium
4   0.31       Good
5   0.24  Very Good

59. Print Concise Summary
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 53940 entries, 0 to 53939
Data columns (total 12 columns):
 #   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
 0   carat           53940 non-null  float64
 1   cut             53940 non-null  object 
 2   color           53940 non-null  object 
 3   clarity         53940 non-null  object 
 4   depth           53940 non-null  float64
 5   table           53940 non-null  float64
 6   price           53940 non-null  int64  
 7   x               53940 non-null  float64
 8   y               53940 non-null  float64
 9   z               53940 non-null  float64
 10  Quality -color  53940 non-null  object 
 11  xyz_prod        53940 non-null  float64
dtypes: float64(7), int64(1), object(4)
memory usage: 4.9+ MB

60. Get True Memory Usage of Diamonds DataFrame
15032550

61. Calculate Memory Usage for Each Series in Diamonds DataFrame
Index                 132
carat              431520
cut               2982154
color             2697000
clarity           2811070
depth              431520
table              431520
price              431520
x                  431520
y                  431520
z                  431520
Quality -color    3090034
xyz_prod           431520
dtype: int64

62. Randomly Sample Rows from Diamonds DataFrame
       carat        cut color clarity  depth  table  price     x     y     z  \
9919    1.13  Very Good     H     SI1   63.3   56.0   4689  6.65  6.62  4.20   
22528   1.21      Ideal     G    VVS2   61.3   57.0  10568  6.83  6.85  4.19   
47605   0.51      Ideal     H      IF   62.0   54.0   1879  5.14  5.18  3.20   

      Quality -color    xyz_prod  
9919     Very Good-H  184.896600  
22528        Ideal-G  196.031245  
47605        Ideal-H   85.200640  

63. Sample 75% of Rows Without Replacement and Store 25% Separately
Sampled shape: (40455, 12) Remaining shape: (13485, 12)

64. Detect Duplicate 'color'
0    False
1     True
2     True
3    False
4    False
Name: color, dtype: bool

65. Count Duplicate Rows in Diamonds DataFrame
146

```
