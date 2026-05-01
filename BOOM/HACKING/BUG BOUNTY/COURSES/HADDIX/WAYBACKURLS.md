

```
echo example.com | waybackurls
```


https://medium.com/@cuncis/waybackurls-a-powerful-tool-for-cybersecurity-professionals-to-enhance-reconnaissance-and-identify-6a25031f4a1c


```
echo "geeksforgeeks.org" | waybackurls -dates
```





This command retrieves all the URLs of the  Wayback Machine archive for the specified domain or target, and tests them for X-Frame-Options and Content-Security-Policy headers.

```
waybackurls <target> | xargs -I{} curl -s -L -I -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:58.0) Gecko/20100101 Firefox/58.0" {} | grep -iE "x-frame-options|content-security-policy"
```


This command retrieves all the URLs of the Wayback Machine archive for the specified domain or target that return a 200 status code.

```
waybackurls <target> -filter "status_code:200"|sort -u
```

