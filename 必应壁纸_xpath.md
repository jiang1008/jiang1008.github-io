```python
import requests
from lxml import etree

url = "https://bing.ioliu.cn/?p=1"
headers = {
"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.149 Safari/537.36"
}  #构造请求头
response = requests.get("https://bing.ioliu.cn/?p=1",headers=headers)
html = response.text #以文本格式将内容打印下来
#print(response.request.headers)
#print(response.text)


"""解析网址"""
selector = etree.HTML(html)   #构造xpath解析参数
imgs = selector.xpath("//a[@class='ctrl download']/@href") #获取图片地址
for url in imgs:
    picture_url= url + imgs
    print(picture_url)
'''下载图片'''
for img in picture_url:  #下载图片
    img_name ="img".split("/")[-1]
    print(img_name)
    response = requests.get(img, headers=headers)
    with open(img_name, 'wb') as f:   #保存图片
       f.write(response.content)
```
