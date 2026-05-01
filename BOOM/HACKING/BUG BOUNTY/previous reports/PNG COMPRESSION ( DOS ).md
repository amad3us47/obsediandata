

A PNG file is composed of multiple chunks. One of the optional ancillary chunks is called zTXT ([ztxt](http://www.libpng.org/pub/png/spec/1.1/PNG-Chunks.html#C.zTXt)). This chunk allows storage of compressed text data using the zlib library. From the zlib [tech](http://www.zlib.net/zlib_tech.html) details: "The test case was a 50MB file filled with zeros; it compressed to roughly 49 KB" I used this to store a huge amount of data in a small PNG (smaller than 1 MB). When sent to HackerOne the service timed out. I think it's because Paperclip tried to `identify` and `convert` my image again.


https://hackerone.com/reports/454 - <span style="color:rgb(0, 176, 80)">28 May 2015</span> 