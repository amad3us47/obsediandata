
Basic command :-
```
ffuf -u http://testphp.vulnweb.com/FUZZ/ -w
```

Multiple wordlist :-
```
ffuf -u https://ignitetechnologies.in/W2/W1/
-w dict.txt:W1 -w dns_dict.txt:W2
```

Filter specific file :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/
-w dict.txt -e .php
```

Match code :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/
-w dict.txt -mc 200
```

Color status code :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/ -w
dict.txt -c
```

Delay in request :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/ -w
dict.txt -p 1
```

Request rate :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/ -w
dict.txt -rate 50
```

Output in html file :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/ -w
dict.txt -o file.html -of html
```

Recursion :-
```
ffuf -u https://google.com -w dns_dict.txt
-recursion
```

Replay proxy :-
```
ffuf -u http://192.168.1.12/dvwa/FUZZ/ -w
dict.txt -replay-proxy http://127.0.0.1:8080
-v -mc 200
```

Post data :-
```
ffuf.exe -request  .\main.txt -w C:\Users\check.txt
```

