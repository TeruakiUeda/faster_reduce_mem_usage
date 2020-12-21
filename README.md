reduce_mem_usageを早くしたい

##  Comparison of the two methods
- base code (overwrite)
```
if c_min > np.iinfo(np.int8).min and c_max < np.iinfo(np.int8).max:
    df[col] = df[col].astype(np.int8)
```


- change (concat)
```
dfs = []
...
if c_min > np.iinfo(np.int8).min and c_max < np.iinfo(np.int8).max:
    dfs.append(df[col].astype(np.int8))
...
df_out = pd.concat(dfs, axis=1)
```

- result  
![exp result](https://user-images.githubusercontent.com/44664107/102815979-9979e480-4410-11eb-9094-ff6206ac93ad.png)
