# Encode and Decode TinyURL  

[Question Link](https://leetcode.com/problems/encode-and-decode-tinyurl/)  

TinyURL is a URL shortening service where you enter a URL such as https://leetcode.com/problems/design-tinyurl and it returns a short URL such as http://tinyurl.com/4e9iAk.  

Design the encode and decode methods for the TinyURL service. There is no restriction on how your encode/decode algorithm should work. You just need to ensure that a URL can be encoded to a tiny URL and the tiny URL can be decoded to the original URL.  

### Explanation:
TLDR: Use the Python built-in hash functin to encode and decode the URLs

## Solution:
```Python
class Codec:
    urls = {}
    def encode(self, longUrl):
        genUrl = hash(longUrl)
        self.urls[genUrl]=longUrl
        return 'http://tinyurl.com/'+str(genUrl)
        """Encodes a URL to a shortened URL.
        
        :type longUrl: str
        :rtype: str
        """
        

    def decode(self, shortUrl):
        genUrl = long(shortUrl.split('/')[-1])
        return self.urls[genUrl]
```
