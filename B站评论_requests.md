```python
import requests

def send_comment():
    url = "https://api.bilibili.com/x/v2/reply/add"
    headers = {
        "Accept": "application/json, text/javascript, */*; q=0.01",
        "Accept-Encoding": "gzip, deflate, br",
        "Accept-Language": "zh-CN,zh;q=0.9,en;q=0.8",
        "Connection": "keep-alive",
        "Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",
        "Cookie": "_uuid=A674206E-E048-2012-1032-BF0FD75BC70E99970infoc; buvid3=F4A09182-27A1-4DAD-8F93-C3164E9CAF9053914infoc; sid=6rxdamki; im_notify_type_478149120=0; CURRENT_FNVAL=16; LIVE_BUVID=AUTO4915829617489886; rpdid=|(J|YkRm|Ruk0J'ul)kmYu~l|; DedeUserID=478149120; DedeUserID__ckMd5=b117727f75a94a18; SESSDATA=50d5ba27%2C1601444487%2Cc9727*41; bili_jct=fda4acd2a3e2f0fa699ee9e33bbdc774; CURRENT_QUALITY=80; bp_t_offset_478149120=377922904044417661; PVID=1",
        "Host": "api.bilibili.com",
        "Origin": "https://www.bilibili.com",
        "Referer": "https://www.bilibili.com/video/BV1pV411Z7RC",
        "Sec-Fetch-Dest": "empty",
        "Sec-Fetch-Mode": "cors",
        "Sec-Fetch-Site": "same-site",
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.113 Safari/537.36",
    }
    form_data = {
        "oid": 412845071,
        "type": 1,
        "message": "你想回学校了吗？",
        "plat": 1,
        "jsonp": "jsonp",
        "csrf": "fda4acd2a3e2f0fa699ee9e33bbdc774"
    }

    response = requests.post(url=url,headers=headers,data=form_data)
    return response.json()

def parser(data):
    C = data["data"]
    print(C)
    a = C["success_toast"]
    print(a)
    
    
  
def run():
    data = send_comment()
    parser(data)

if __name__ == "__main__":
    run()
```