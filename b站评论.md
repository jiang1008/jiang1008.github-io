---
title: b站评论
date: 2020-04-22 14:54:50
tags:
---


```python
import urllib.request
import urllib.parse
import http.cookiejar
import gzip
import json


def crawler():
	url = "https://api.bilibili.com/x/v2/reply/add"
	headers = {
		"Accept": "application/json, text/javascript, */*; q=0.01",
		"Accept-Encoding": "gzip, deflate, br",
		"Accept-Language": "zh-CN,zh;q=0.9",
		"Connection": "keep-alive",
		"Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",
		"Cookie":"_uuid=3A62C7DD-0C12-989E-CAA5-17B7393AE33162211infoc; buvid3=4D285F1A-8B88-486B-BD80-5CA36BEB389F155816infoc; CURRENT_FNVAL=16; LIVE_BUVID=AUTO3815854678801605; rpdid=|(JRuY~))ml|0J'ul)lRY~))|; DedeUserID=404011834; DedeUserID__ckMd5=ed6ebd6762b9d1cb; SESSDATA=cc61f7fe%2C1601019895%2C5f81b*31; bili_jct=f125445153cdc153d8a4bbc7c4b25846; CURRENT_QUALITY=80; PVID=1; bsource=seo_bing; sid=cughrz8m",
		"Host": "api.bilibili.com",
		"Origin": "https://www.bilibili.com",
		"Referer": "https://www.bilibili.com/video/BV1KE411u74U",
		"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.163 Safari/537.36"
	}

	form_data = {
		"oid": 94775464,
		"type": 1,
		"message":"哈哈哈",
		"plat": 1,
		"jsonp": "jsonp",
		"csrf": "f125445153cdc153d8a4bbc7c4b25846"
	}

	data = bytes(urllib.parse.urlencode(form_data), encoding="utf-8")
	r = urllib.request.Request(url=url, data=data, headers=headers)   #构造请求对象
	cookie = http.cookiejar.CookieJar()
	handler = urllib.request.HTTPCookieProcessor(cookie)
	opener = urllib.request.build_opener(handler)
	urllib.request.install_opener(opener)
	response = opener.open(r)
	json.load()
	response = urllib.request.urlopen(r)
	resp = gzip.GzipFile(fileobj=response)     #对输入评论进行解压
	print(resp.read().decode("utf-8"))
if __name__ == "__main__":
	crawler()
```