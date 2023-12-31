# 咨询（ChatGPT4 版本、支持60句话内的上下文）

## 介绍
"照片扮演角色(X-me)" 是一项创新服务，允许用户的照片在指定视频中扮演角色。这种技术通过处理用户提供的照片和视频文件，创造出一种新颖的视觉体验，让照片在视频中“活”起来。

## 示例

## API 使用说明

### 1.视频生成接口

#### 请求方式
- **方法**: POST
- **URL**: https://obai.ipolloverse.cn/iPollo/chatGPT/chat

#### 请求参数
请求需要包含以下JSON格式的参数：
```json
{
  "question": "",     #咨询内容
  "btc_address": ""   #BTC地址
}
```
- question: 咨询内容
- btc_address: 用户的比特币地址

#### 响应格式
请求成功后，将返回包含以下信息的JSON格式数据：
```
{
  "result_code": 200,
  "msg": `三亚和海口位于中国海南省，都是非常受欢迎的旅游目的地，各自具有独特的特色。      三亚：     海滨风光：三亚以其美丽的海滩和清澈的海水而著称，度假圣地。著名的景点有亚龙湾、天涯海角、大东海等。     自然景观：热带雨林、山脉等，如南山、热带天堂森林公园等。     文化遗址：诸如南繁儿童旅游区、椰梦长廊等。     氛围：三亚崇尚“度假”的轻松氛围以及多姿多彩的夜生活。          海口：     历史文化名城：海口拥有丰富的历史底蕴，如五公祠、文化公园等。     自然风光：以火山口、红树林等为特色，如火山口地质公园、东寨港红树林等。     "遇见海口"城市建筑风貌活动。     怡然自得的都市度假生活：城市中有许多美食、酒吧、购物广场等，都市功能发展齐全。          不同的游客可以根据自己的兴趣选择。如果你更喜欢热带海滨度假，以沙滩、阳光、冲浪为主题，那么三亚会是更好的选择。如果你对历史文化感兴趣，同时想体验都市度假的生活，那么海口将是不错的选择。当然，如果时间充裕，可以考虑游览这两个城市，体会南海风情的多样美。`
}
```

##### 状态码说明
- 200: 请求参数错误或不完整。
- 202: 音频或视频文件的云地址无效或缺失。
- 203: 内部服务器错误，例如视频转换失败或存储失败。
