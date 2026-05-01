

```
cat .audible.com.br.txt | C:\Users\marku\OneDrive\Desktop\Games\pendrive\tools\httpx.exe | ForEach-Object { $_ -replace '^https://', '' } > live.audible.com.br.txt
```


Sort unique

``` 
| Sort-Object -Unique
```