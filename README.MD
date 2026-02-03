# PANDAS CHEAT SHEET
# Cleaning → Formatting → Normalization → Encoding


# Module 1



# Module 2


## 1. Reading Files | Import Files

```python
   pd.read_csv('file_name.csv')
   pd.read_excel('file_name.xlsx')
   pd.read_json('file_name.json')
   pd.read_html('file_name.html')
   pd.read_sql('file_name.sql')
   pd.read_parquet('file_name.parquet')
   pd.read_clipboard()
```

## 2. Writing Files | Export Files

```python
   df.to_csv('file_name.csv')
   df.to_excel('file_name.xlsx')
   df.to_json('file_name.json')
   df.to_html('file_name.html')
   df.to_sql('file_name.sql')
   df.to_parquet('file_name.parquet')
   df.to_clipboard()
```

## 3. Missing Values | Null | NaN | None

```python
   df.dropna(subnet=['column_name'], axis=0, inplace=True)
```

## 4. Replace Values

```python
   mean = df['column_name'].mean()
   df['column_name'].replace(np.nan, mean, inplace=True)
```

## 5 . Data Formatting | Data Type


## 6. Convert Data Values | Data Type Conversion

```python
   df['column_name'] = df['new_column_name']
   df.rename(columns={'old_column_name': 'new_column_name'}, inplace=True)

   Example : Converting mpg to LKm
             df['column_name'] = 235 / df['column_name']
             
```

```python 
   df.dtypes() # identify data types
   df.info()   # identify data properties
   df.astype() # convert data types
```

## 7. Incorrect Data 

```python
   df['price'].tail(5)
```

## 8. Data Normalization | Data Scaling

```python
   
   df['column_name'] = df['column_name'] / df['column_name'].max()
   Example : .max()
   | length | width | height |         | length | width | height |
   | 168.8  | 64.1  | 48.8   |  ===>>  | 0.81   | 64.1  | 48.8   |
   | 168.8  | 64.1  | 48.8   |  ===>>  | 0.81   | 64.1  | 48.8   |
   | 180.0  | 65.5  | 52.4   |         | 0.87   | 65.5  | 52.4   |

   df['length'] = (df['length'] - df['length'].min())/
   df['column_name'].max() - df['column_name'].min()
   Example : .min()
   | length | width | height |         | length | width | height |
   | 168.8  | 64.1  | 48.8   |  ===>>  | 0.41   | 64.1  | 48.8   |
   | 168.8  | 64.1  | 48.8   |  ===>>  | 0.41   | 64.1  | 48.8   |
   | 180.0  | 65.5  | 52.4   |         | 0.58   | 65.5  | 52.4   |

   df['length'] = (df.['length'] - df['length'].mean())/
   df['length'].std()
   Example : .mean() .std()
   | length | width | height |         | length | width | height |
   | 168.8  | 64.1  | 48.8   |  ===>>  | -0.034 | 64.1  | 48.8   |
   | 168.8  | 64.1  | 48.8   |  ===>>  | -0.034 | 64.1  | 48.8   |
   | 180.0  | 65.5  | 52.4   |         |  0.0   | 65.5  | 52.4   |

```

## 9. Binning | Grouping

```python
   |  price  |        |  price  |  price-binned  |
   |  13495  |        |  13495  |  Low           |
   |  16500  |        |  16500  |  Low           |
   |  18920  |   ==>  |  18920  |  Medium        |
   |  41315  |   ==>  |  41315  |  High          |
   |  5151   |        |  5151   |  Low           |
   |  5151   |        |  5151   |  Low           |
   |  6295   |        |  6295   |  Low           |
   bins = np.linspace(min(df['price']), max(df['price']), 4)
   group_names = ['Low', 'Medium', 'High']
   df['price-binned'] = pd.cut(df['price'], bins, labels=group_names, include_lowest=True)
   
```

## 10. Dummy Variables

```python
   |  car  | fuel   |       |  gas  | diesel |
   |  A    | diesel |       |  1    |  0     |
   |  A    | gas    |       |  1    |  0     |
   |  B    | diesel | ===>  |  1    |  0     |
   |  C    | gas    |       |  0    |  1     |
   |  C    | diesel |       |  0    |  1     |
   |  D    | gas    |       |  1    |  0     |
   |  D    | gas    |       |  1    |  0     |
   pd.get_dummies(df['fuel'])

```

# Module 3  

## 1. Destriptive Statistics

```python 
   df.describe()      # to Summarize statistics
   df.value_count()   # 
      ex : df['column_name'].value_counts()
      ex : df['column_name'].value_counts().to_frame()
      ex : df['column_name'].value_counts().to_frame().rename(columns={'column_name': 'value_counts'}, inplace=True)

   sns.boxplot(x=df['column_name'], y=df['column_name'], data = df)
    
    Scatterplot : Example
        y = df['column_name']
        x = df['column_name']
        plt.scatter(x, y)

        plt.title('Scatterplot of column_name vs column_name')
        plt.xlabel('column_name')
        plt.ylabel('column_name')
```

## 2. Groupby in Python

```python
    df.groupby(['column_name']).mean()
    df.groupby(['column_name'])['column_name'].mean()
    df.groupby(['column_name'])['column_name'].max()
    df.groupby(['column_name'])['column_name'].min()
    df.groupby(['column_name'])['column_name'].count()
    df.groupby(['column_name'])['column_name'].value_counts()
    df.groupby(['column_name'])['column_name'].std()
    df.groupby(['column_name'])['column_name'].var()
    df.groupby(['column_name'])['column_name'].median()

    * Example  
          df_test = df['drive-wheels', 'body-style', 'price']
          df_group_one = df_test.groupby(['drive-wheels', 'body-style'], as_index=False).mean()
          df_group_one
```

## 3. Correlation

```python
    * corretlation between two features

    * positive  linear relationship
        sns.regplot(x='column_name', y='column_name', data=df)
        plt.ylim(0,)

    * negative  linear relationship
        sns.regplot(x='column_name', y='column_name', data=df)
        plt.ylim(0,)

    * no linear relationship

    Example : Lung Caner -> Smoking
              Rain -> umbrella
```

## 4. Correlation - Statistics

```python
   * providing heatmap
   Example : pearon_coef, p_value = stats.pearsonr(df['house_power'], df['price'])
             Pearson correclation: 0.81
             P-value: 9.35 e-48

```