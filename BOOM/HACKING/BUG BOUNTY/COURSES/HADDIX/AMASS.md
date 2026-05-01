### API Setup :-
```
amass enum -list
```



### Commands


Simple command : -
```
amass enum -d example.com
```

Recursive enum :-
2 is depth 
```
amass enum -brute -min-for-recursive 2 -d example.com
```

Search for org :-
```
amass intel -org 'Example Ltd'
```

By asn :-
```
amass intel -active -asn 222222 -ip
```

Passive search with sources :-
```
amass enum -passive -d owasp.org -src
```

Dns brute forces :-
```
amass enum -active -d owasp.org -public-dns -brute -w /root/dns_lists/deepmagic.com-top50k
```

Search by asn :-
```
amass intel -asn 16839 -dir amass -config recon/config.yaml
```

Active/Passive search :-
```
amass enum -active -d example.com -dir amass -config recon/config.yaml
```

