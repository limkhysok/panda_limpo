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
