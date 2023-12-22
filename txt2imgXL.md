# 文生图（Stable Diffusion XL版本）

## 介绍
"照片扮演角色(X-me)" 是一项创新服务，允许用户的照片在指定视频中扮演角色。这种技术通过处理用户提供的照片和视频文件，创造出一种新颖的视觉体验，让照片在视频中“活”起来。

## 示例

## API 使用说明

### 1.视频生成接口

#### 请求方式
- **方法**: POST
- **URL**: https://obai.ipolloverse.cn/iPollo/stableDiffsionXL/txt2img

#### 请求参数
请求需要包含以下JSON格式的参数：
```json
{
  "prompt": "",       #文生图的描述词
  "btc_address": ""   #BTC地址
}
```
- prompt: 文生图的描述词
- btc_address: 用户的比特币地址

#### 响应格式
请求成功后，将返回包含以下信息的JSON格式数据：
```
{
  "result_code": 200,
  "msg": "success",
  "prompt": "a Chinese girl sitting in a garden, with sunshine and green trees, fine face，realistic",
  "key": {
    "ok": true,
    "result": [{
        "id": 321571788393808896,
        "workspace_id": "311367531866620928",
        "key": "ts-be5fb69e-31ef-43ea-bfb0-4a9192566140",
        "video_duration": 60,
        "total_duration": 60,
        "use_duration": 13,
        "start_time": "2023-12-05 16:51:26",
        "end_time": "2024-12-05 16:51:26",
        "bench_mark": "PGPU-3080-10G-CN",
        "note": "",
        "address": "0x6fd53365566d9f0E81204850182544C40F4f3d6F",
        "email": "9476588@qq.com",
        "discord_uid": "1148540162113011753",
        "tg_uid": ""
    }]
  },
  "image_base": {
    "parameters": {
      "enable_hr": false,
      "Prompt": "a Chinese girl sitting in a garden, with sunshine and green trees, fine face，realistic",
      "Seed": -1,
      "Batch_size": 1,
      "Width": 512,
      "Height": 512
    },
  "info": "{\"prompt\": \"a Chinese girl sitting in a garden, with sunshine and green trees, fine face\\uff0crealistic\", \"all_prompts\": [\"a Chinese girl sitting in a garden, with sunshine and green trees, fine face\\uff0crealistic\"], \"negative_prompt\": \"\", \"all_negative_prompts\": [\"\"], \"seed\": 1706924173, \"all_seeds\": [1706924173], \"subseed\": 359219742, \"all_subseeds\": [359219742], \"subseed_strength\": 0, \"width\": 512, \"height\": 512, \"sampler_name\": \"Euler\", \"cfg_scale\": 7.0, \"steps\": 50, \"batch_size\": 1, \"restore_faces\": false, \"face_restoration_model\": null, \"sd_model_name\": \"sd_xl_base_1.0_0.9vae\", \"sd_model_hash\": \"e6bb9ea85b\", \"sd_vae_name\": null, \"sd_vae_hash\": null, \"seed_resize_from_w\": -1, \"seed_resize_from_h\": -1, \"denoising_strength\": 0, \"extra_generation_params\": {}, \"index_of_first_image\": 0, \"infotexts\": [\"a Chinese girl sitting in a garden, with sunshine and green trees, fine face\\uff0crealistic\\nSteps: 50, Sampler: Euler, CFG scale: 7.0, Seed: 1706924173, Size: 512x512, Model hash: e6bb9ea85b, Model: sd_xl_base_1.0_0.9vae, Denoising strength: 0, Version: v1.6.0\"], \"styles\": [], \"job_timestamp\": \"20231205085216\", \"clip_skip\": 1, \"is_using_inpainting_conditioning\": false}",
  "imageUrl": "https://dispense.ipolloverse.cn:81/2023-12-05_16:52:29.431.jpg"
  }
}
```

##### 状态码说明
- 200: 请求参数错误或不完整。
- 202: 音频或视频文件的云地址无效或缺失。
- 203: 内部服务器错误，例如视频转换失败或存储失败。

### 2.任务查询接口

#### 请求方式

- **方法**: GET
- **URL**: https://obai.ipolloverse.cn/iPollo/twinSync/videotalking?taskID=xxx

#### 请求参数
 - taskID：生成接口返回的task_id

```
{
    "result_url": "https://pop.ipolloverse.cn:8090/iPollo/twinSync/example/20230423_11_23_05_10279.mp4",    #生成的视频路径
    "result_code": 100,     #返回的code值
    "msg": "taskID:20230423_11_23_05_10279 has been completed, and the output video url is: https://pop.ipolloverse.cn:8090/iPollo/twinSync/example/20230423_11_23_05_10279.mp4",   #返回的Msg信息
    "api_time_consume": 10, #视频时长（秒）
    "api_time_left": 590,   #剩余时长（秒）
    "video_w": 1920,        #视频宽度 "video_h": 1080,        #视频高度
    "gpu_type": "NVIDIA GeForce RTX 3090",  #对标GPU类型（暂时无用）
    "gpu_time_estimate": 120,   #预估gpu消耗时长（暂时无用）
    "gpu_time_use": 82      #gpu消耗时长
} 
```
code值列表: 
- 100：任务处于成功状态
- 101：任务处于等待状态
- 102：任务处于运行状态
- 103：任务处于失败状态
- 200：taskID字段缺失或者该字段不在服务队列中
