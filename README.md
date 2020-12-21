reduce_mem_usageを早くしたい

##  2通りで速度の比較
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
https://user-images.githubusercontent.com/44664107/102814636-4737c400-440e-11eb-9873-c222d296f307.png
