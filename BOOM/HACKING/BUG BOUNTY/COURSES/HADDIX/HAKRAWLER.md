
Installation :-
```
go install github.com/hakluke/hakrawler@latest
```




Basic usage :-
```
echo https://google.com | hakrawler
```


Multiple urls :-
```
cat urls.txt | hakrawler
```

Give some timeouts :-
```
cat urls.txt | hakrawler -timeout 5
```

Send to proxy :-
```
cat urls.txt | hakrawler -proxy http://localhost:8080
```

Include subdomains :-
```
echo https://google.com | hakrawler -subs
```

Chain other tools :-
```
echo google.com | haktrails subdomains | httpx | hakrawler
```


