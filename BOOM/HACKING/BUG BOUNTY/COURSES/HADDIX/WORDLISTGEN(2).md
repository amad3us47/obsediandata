

$ cat file.txt
https://google.com/home/?q=2&d=asd
http://my.site
/api/v2/auth/me?id=123

```
cat hosts.txt | wordlistgen
```


```
$ wordlistgen -h
Usage of wordlistgen:

  -fq If enabled, filter out query strings (e.g. if enabled /?q=123 - q would NOT be included in results
  -qv
    	If enabled, include query string values (e.g. if enabled /?q=123 - 123 would be included in results
    	
```


Chaining with waybackurls :- 
```
cat hosts.txt | waybackurls | wordlistgen
```