
Installation :-
```
git clone https://github.com/blechschmidt/massdns.git
cd massdns
make
sudo make install
```


Basic usage :-
```
puredns bruteforce <wordlist.txt> <domain.com> -r <resolvers.txt>
```

Chaining :-
```
cat <hosts.txt> | puredns resolve -r <resolvers.txt>
```

