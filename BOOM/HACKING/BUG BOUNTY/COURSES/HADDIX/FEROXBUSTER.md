For more info :-
https://www.hackingarticles.in/a-detailed-guide-on-feroxbuster

Basic :-
```
feroxbuster -u http://192.168.1.4
```


Remove unnecessary data :-
```
feroxbuster -u http://192.168.1.4 --silent
```


Follow redirects :-
```
feroxbuster -u http://192.168.1.4 -r
```


Specific extension :-
```
feroxbuster -u http://192.168.1.4 -x php,txt --silent
```


Storing output :-
```
feroxbuster -u http://192.168.1.4 --output results.txt
```


Using user agent :-
```
feroxbuster -u http://192.168.1.4 -a "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
```


Status code :-
```
feroxbuster -u http://192.168.1.4 -C 403,404
```


Threading to speed up :-
```
feroxbuster -u http://192.168.1.4 -t 20
```


Custom wordlist :-
```
feroxbuster -u http://192.168.1.4 -w /usr/share/wordlists/dirb/common.txt
```






