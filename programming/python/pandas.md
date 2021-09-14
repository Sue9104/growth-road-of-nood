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

apply function to whole dataframe， and unit is **dataframe**

```text
fun_c(func_b( func_a(df, args_a), args_b ), args_c )
# equivalence
df.pip(func_a, args_a).pip(func_b, args_b).pip(func_c, args_b)
```

### apply

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">function</th>
      <th style="text-align:left">Unit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">apply</td>
      <td style="text-align:left">apply a function along an axis</td>
      <td style="text-align:left">function(including <b>aggregated func</b>)</td>
      <td style="text-align:left">
        <ul>
          <li>single column: <em><b>element</b></em>
          </li>
          <li>row or column axis: <em><b>series</b></em>
          </li>
          <li>groupby object: <em><b>dataframe</b></em>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">transform</td>
      <td style="text-align:left">
        <p>call a function on self</p>
        <p></p>
        <p>return a dataframe with transformed values</p>
      </td>
      <td style="text-align:left">
        <ul>
          <li>function (not aggregate func)</li>
          <li><b>a list</b>
          </li>
          <li><b>a dict</b>
          </li>
        </ul>
      </td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>single column: <em><b>element</b></em>
          </li>
          <li>row or column axis: <em><b>series</b></em>
          </li>
          <li>groupby object: <b>only works with a series</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">applymap</td>
      <td style="text-align:left">
        <p></p>
        <p>apply a function to a dataframe elementwise</p>
      </td>
      <td style="text-align:left">function</td>
      <td style="text-align:left"><b>element</b>
      </td>
    </tr>
  </tbody>
</table>

```text
# function type
## transform() can take a function, string, list, and a dict. 
## apply() is only allowed a function
df.transform('sqrt')
df.transform( [np.sqrt, np.exp] )
df.transform({'A': np.sqrt, 'B': np.exp})

# groupby
## apply() works with multiple Series at a time, but transform() is allowed with one. 
## apply() can produce aggregated results.
df.groupby('key').apply(lambda x: x['A'] - x['B'])
df.apply(lambda x: x.sum())
```

