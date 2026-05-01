
Basic usage :-
```
gobuster dir -u "http://v.com/" -w /usr/share/wordlists/dirb/small.txt -t 64
```

Dir mode :-
```
gobuster dir -u "http://www.example.thm" -w /path/to/wordlist
```


Redirects :-
```
gobuster dir -u "http://www.example.thm" -w /usr/directory-list-2.3-medium.txt -r
```


Dns mode :-
```
gobuster dns -d example.thm -w /usr/share/subdomains-top1million-5000.txt
```


Vhost mode :-
```
gobuster vhost -u "http://example.thm" -w /path/to/wordlist
```


