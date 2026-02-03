# PANDAS CHEAT SHEET

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
   bins = np.linspace(min(df['column_name']), max(df['column_name']), 4)
   group_names = ['Low', 'Medium', 'High']
   df['column_name-binned'] = pd.cut(df['column_name'], bins, labels=group_names, include_lowest=True)
   
```