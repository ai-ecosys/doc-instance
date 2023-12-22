# 文字和语音（ChatGPT4 版本）

## 介绍
"照片扮演角色(X-me)" 是一项创新服务，允许用户的照片在指定视频中扮演角色。这种技术通过处理用户提供的照片和视频文件，创造出一种新颖的视觉体验，让照片在视频中“活”起来。

## 示例

## API 使用说明

### 1.视频生成接口

#### 请求方式
- **方法**: POST
- **URL**: https://obai.ipolloverse.cn/iPollo/chatGPT/txt2voice

#### 请求参数
请求需要包含以下JSON格式的参数：
```json
{
  "txt": "",          #需要生成语音的文字
  "voice": "",        #使用的声音（alloy、echo、fable、onyx、nova、shimmer）
  "btc_address": ""   #BTC地址
}
```
- txt: 需要生成语音的文字
- voice: 使用的声音（alloy、echo、fable、onyx、nova、shimmer）
- btc_address: 用户的比特币地址

#### 响应格式
请求成功后，将返回包含以下信息的JSON格式数据：
```
{
  "result_code": 200,
  "msg": "https://obai.ipolloverse.cn:8090/20231218211952000.mp3"
}
```

##### 状态码说明
- 200: 请求参数错误或不完整。
- 202: 音频或视频文件的云地址无效或缺失。
- 203: 内部服务器错误，例如视频转换失败或存储失败。
