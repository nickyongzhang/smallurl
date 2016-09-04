<link rel="stylesheet" href="/Users/zhangyong/highlight/styles/default.css">
<script src="/Users/zhangyong/highlight/highlight.pack.js"></script>
<script>hljs.initHighlightingOnLoad();</script>


# Smallyurl
**The project is aimed at changing a long URL to a small url.** 
  
We usesually see some ugly and long urls in emails or    
somewhere else like   

*https://www.amazon.com/BLACK-DECKER-LCC140-Lithium-Trimmer/dp/B00JGUAP8W/ref=gbps_img_s-3_5402_77b2d6e0?smid=ATVPDKIKX0DER&pf_rd_p=2558495402&pf_rd_s=slot-3&pf_rd_t=701&pf_rd_i=gb_main&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=KZRQ9PST7PV2YR29SHFT*

It would be a nightmare if we want to cut such a url. How about changing the long url into a small url which directs to the same direction? That what this little project is doing.

Actually this project is using the service provided the website [smallurl.com](http://smallurl.com). The website can return a small url if the user input a long url. Our project provides a simple script to get access to the website's service without opening the browsers. It's easy and portable.

## Introduction
A function is defined to call the smallurl api and return the short url.

	def make_small(url):
		request_url = 'http://smallurl.com/api-create.php?' + \
	    				urlencode({'url':url})
		return 	requests.get(request_url).content.decode('utf-8')
		
In the above function, the input url is encoded and added to the end of small url api ("http://smallurl.com/api-creat,php?").

In order to make the function work. We need to import some libraries.

	try:
		from urllib.parse import urlencode
	except ImportError:
		from urllib import urlencode
	import requests

Yes, the code is just that simple!

## Installation

	$ pip install smallurl


## Usage

After install smallurl

	>> from smallURL import smallurl
	>> long_url = 'https://www.amazon.com/BLACK-DECKER-LCC140-Lithium-Trimmer/dp/B00JGUAP8W/ref=gbps_img_s-3_5402_77b2d6e0?smid=ATVPDKIKX0DER&pf_rd_p=2558495402&pf_rd_s=slot-3&pf_rd_t=701&pf_rd_i=gb_main&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=KZRQ9PST7PV2YR29SHFT'
	>> short_url = smallurl.make_small(long_url)
	>> short_url
	http://smallurl.com/zh5lncb

The user can also call the script in a shell (in the script directory)

	$ python smallurl.py long_url1

The user can even input a list of long urls

	$ python smallurl.py long_url1 long_url2 long_url3
	
## Requirements

- Python >=2.7 or >=3.3

## License

MIT licensed.






