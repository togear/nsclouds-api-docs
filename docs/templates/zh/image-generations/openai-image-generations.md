# OpenAI - 图像生成

### 1. 概述

OpenAI 的图像生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `gpt-image-2` (image_generation 模式)

### 2. 计费方式

`gpt-image-2-oai` 按响应顶层 `usage` 的实际 Token 用量计费。原 `gpt-image-2` 保留按图像张数计费，单张价格由图像像素规模（宽 × 高）和生成质量 `quality` 的档位确定。具体单价以所选模型价格配置为准。

### 3. 接口详情

{% openapi-operation spec="openai-zh-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/openai.bundled.yaml)
{% endopenapi-operation %}
