
1= 1x 1000

How to run: - python test.py

```python
import requests
import os
import wget
import urllib
import time
with open("all.txt", encoding="utf8") as file:
    words = file.read().split()  # Read all words and split by spaces

for line in words[1:40000]:
    try:
        url="https://amad3us47.github.io/data/"+line
        r=requests.get(url,allow_redirects=True)
        open(line,'wb').write(r.content)
        #print("using "+ line+" template")
        os.system("./nuclei -u app-updates.agilebits.com -o find.txt -silent   2>/dev/null -sresp -t "+line)
        directory=os.getcwd()
        line=line.rstrip('\n')
        os.remove(directory+"/"+line)
    except urllib.error.URLError:
        time.sleep(5)

    except Exception as e:
        print("failed at",line)
        print("Error:",e)
        sys.exit(1)
```

