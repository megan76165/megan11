import requests
import json

def translate_text(text, source_language, target_language):
    url = "https://translate.googleapis.com/translate_a/single?client=gtx&sl={}&tl={}&dt=t&q={}".format(source_language, target_language, text)
    response = requests.get(url)
    result = json.loads(response.content.decode('utf-8'))
    translated_text = result[0][0][0]
    return translated_text

print("欢迎使用翻译程序！")
print("请输入要翻译的文本：")
text = input()

print("请输入语言代码（例如：en表示英语）：")
source_language = input()

print("请输入目标语言代码（例如：zh-CN表示中文）：")
target_language = input()

translated_text = translate_text(text, source_language, target_language)
print("翻译结果：", translated_text)
