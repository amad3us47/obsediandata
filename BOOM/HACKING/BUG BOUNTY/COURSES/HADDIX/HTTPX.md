

Basic usage :-
```
httpx -l hosts.txt
```


Combining tools :-
```
cat hosts.txt | grep example.com | httpx
```

More tool chain :-
```
subfinder -d example.com -silent | httpx -title -tech-detect -status-code
```


Specific status code :-
```
cat hosts.txt | httpx -mc 200,302
```

Match response with regex :-
```
cat hosts.txt | httpx -mr 'admin*'
```

Save output to a file :-
```
httpx -l urls.txt -o httpx.log
```

Use config file :-
```
httpx -config httpx-config.yaml
```




Config file :-
```
status-code: true  
content-length: true  
content-type: true  
location: true  
line-count: true  
word-count: true  
title: true  
body-preview: true  
web-server: true  
tech-detect: true  
ip: true  
cname: true  
filter-code: 302,401,403  
filter-error-page: true  
threads: 10  
rate-limit: 20  
update: false  
disable-update-check: true  
store-response: true  
store-response-dir: httpx-responses  
json: true  
include-response-header: true  
include-response: true  
random-agent: true  
#header: Custom Global Headers  
follow-redirects: false  
follow-host-redirects: false  
tls-impersonate: true  
version: false  
stats: true  
silent: true  
stats-interval: 5  
max-host-error: 3  
retries: 0  
timeout: 5
```

