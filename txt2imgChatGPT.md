# 文生图（ChatGPT4版本）

## 介绍
"照片扮演角色(X-me)" 是一项创新服务，允许用户的照片在指定视频中扮演角色。这种技术通过处理用户提供的照片和视频文件，创造出一种新颖的视觉体验，让照片在视频中“活”起来。

## 示例

## API 使用说明

### 1.视频生成接口

#### 请求方式
- **方法**: POST
- **URL**: https://obai.ipolloverse.cn/iPollo/chatGPT/txt2img

#### 请求参数
请求需要包含以下JSON格式的参数：
```json
{
  "prompt": "",       #描述词
  "size": "",         #生成图片的大小（256x256、512x512、1024x1024）
  "btc_address": ""   #BTC地址
}
```
- prompt: 文生图的描述词
- size: 生成图片的大小（256x256、512x512、1024x1024）
- btc_address: 用户的比特币地址

#### 响应格式
请求成功后，将返回包含以下信息的JSON格式数据：
```
{
  "result_code": 200,
  "msg": "https://oaidalleapiprodscus.blob.core.windows.net/private/org-Ya6gz0sKG8BaEMaY7FbjwTup/user-dra6PQrAlbmLSgpX2N5KbKyU/img-lMJ1HzfdzH6JBpX8e0dQv8tM.png?st=2023-12-18T02%3A53%3A57Z&se=2023-12-18T04%3A53%3A57Z&sp=r&sv=2021-08-06&sr=b&rscd=inline&rsct=image/png&skoid=6aaadede-4fb3-4698-a8f6-684d7786b067&sktid=a48cca56-e6da-484e-a814-9c849652bcb3&skt=2023-12-17T16%3A32%3A09Z&ske=2023-12-18T16%3A32%3A09Z&sks=b&skv=2021-08-06&sig=mpniycYi56ipNICEtJbnVpBKiRdG12Y/OI6HF3aGtGw%3D"
}
```

##### 状态码说明
- 200: 请求参数错误或不完整。
- 202: 音频或视频文件的云地址无效或缺失。
- 203: 内部服务器错误，例如视频转换失败或存储失败。
