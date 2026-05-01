
Usage :-
```
katana -u https://hackerone.com
```

Multiple targets :-
```
katana -u https://hackerone.com,https://geeksforgeeks.org
```

From a txt file :-
```
katana -list targets.txt
```

Crawl depth :-
```
katana -u https://tesla.com -d 5
```

Javascript endpoints :-
```
katana -u https://tesla.com -jc
```

Proxy server :-
```
katana scan -u target.com --proxy http://proxyserver:8080
```

Specific plugin search :-
```
katana scan -u target.com -p xss,sq
```


