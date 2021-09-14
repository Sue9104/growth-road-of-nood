# pandas

## IO

### Excel

```text
# output to excel with specified datetime format
excel_writer = pd.ExcelWriter(filename, datetime_format = 'YYYY-MM-DD')
data.to_excel(excel_writer, sheetname)
excel_writer.close()
```

## Function

### pipe

### apply

