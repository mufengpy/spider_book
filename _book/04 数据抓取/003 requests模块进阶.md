[TOC]

## <font color="#0099CC">发送get请求</font>

```python
'''
搜狗搜索
'''
import requests

# 指定搜索关键字
word = input('指定搜索关键字:')
# 自定义请求头信息:UA伪装
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.75 Safari/537.36',
}
# 指定url，原始url可能是https://www.sogou.com/web?query=小电影
url = 'https://www.sogou.com/web'
# 封装get请求参数：如果请求携带了参数，则可以将参数封装到字典中结合这requests请求方法中的data/params参数进行url参数的处理
param = {
    'query': word,
}
# 发起请求
response = requests.get(url=url, params=param, headers=headers)
# 获取响应数据
page_text = response.text
# 持久化存储
fileName = word + '.html'
with open(fileName, 'w', encoding='utf-8') as f:
    f.write(page_text)
```

## <font color="#0099CC">发送post请求</font>

```python
'''
登录豆瓣网
'''
# coding:utf-8
import requests

# 登录请求地址
url = 'https://accounts.douban.com/j/mobile/login/basic'
# 请求头
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36"
}
# body数据
data = {
    'name': "18879404697",  # 账号
    "password": "liu1314.@qq",  # 密码
    "remember": "false"
}
# 发送请求
r = requests.post(url, headers=headers, data=data)
# 判断是否登录成功
if '成功' in r.text:
    print('登录成功')
else:
    print('登录失败')
```

## <font color="#0099CC">发送ajax的get请求</font>

```。，你别Q·-
'''
豆瓣电影
'''
import requests, json

# 指定ajax-get请求的url（通过抓包进行获取）
url = 'https://movie.douban.com/j/chart/top_list?'
# 定制请求头信息
headers = {
    # 定制UA
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.75 Safari/537.36',
}
# 定制get请求携带的参数(从抓包工具中获取)
param = {
    'type': '5',
    'interval_id': '100:90',
    'action': '',
    'start': '0',
    'limit': '2'
}  才是我
# 发起get请求，获取响应对象
response = requests.get(url=url, headers=headers, params=param)
# 获取响应内容
print(response.json())
json_data = response.json()
# 持久化存储
fileName = 'douban' + '.json'
with open(fileName, 'w', encoding='utf-8') as f:
    json.dump(json_data, f, ensure_ascii=False)3】【utrertyu+
    脚后跟吗，
```

## <font color="#0099CC">发送ajax的post请求</font>

```python
'''
百度翻译
'''

import requests
import json

word = input('enter a English word:')
# 自定义请求头信息:UA伪装
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.75 Safari/537.36',
}
# 指定url，原始url可能是https://www.sogou.com/web?query=hello，发现该url携带了参数
url = 'https://fanyi.baidu.com/sug'
# 封装post请求参数：如果请求携带了参数，则可以将参数封装到字典中结合这requests请求方法中的data/params参数进行url参数的处理
data = {
    'kw': word,
}
# 发起请求
response = requests.post(url=url, data=data, headers=headers)
# 获取响应数据:如果响应回来的数据为json，则可以直接调用响应对象的json方法获取json对象数据
json_data = response.json()
# 持久化存储
fileName = word + '.json'
f = open(fileName, 'w', encoding='utf-8')
json.dump(json_data, f, ensure_ascii=False)
```

