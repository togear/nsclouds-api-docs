# OpenAI - 图像生成

### 1. 概述

OpenAI 在当前环境中提供的图像生成能力。

{% hint style="success" %}
本接口提供 OpenAI Images API 的 GPT Image 2 与 GPT Image 2.5 图像能力。
{% endhint %}

**模型列表：**

* `gpt-image-2`
* `gpt-image-2.5-flare`
* `gpt-image-2.5-flare-oai`
* `gpt-image-2.5-sunburst`
* `gpt-image-2.5-sunburst-oai`


### 2. 图像模型参数说明

#### gpt-image-2

{% hint style="info" %}
`gpt-image-2` 支持文本生成图像。`n` 可请求 1-10 张图像，实际返回数量可能少于请求数量。
{% endhint %}

| 参数 | 支持情况 |
| --- | --- |
| `prompt` | 必填，最长参考为 32000 个字符。 |
| `n` | 可选，范围参考为 1-10；实际返回图片数量可能少于请求数量。 |
| `size` | 可选，支持 `auto` 和下方列出的固定尺寸。 |
| `quality` | 可选，支持 `low`、`medium`、`high`；省略、`auto`、`standard` 按 `high` 计费。 |
| `background` | 可选，支持 `opaque`、`auto`。 |
| `moderation` | 可选，仅图像生成接口支持，支持 `low`、`auto`。 |
| `output_format` | 可选，支持 `png`、`jpeg`。 |
| `output_compression` | 可选，范围 0-100，仅 `jpeg` 使用；`png` 应省略或设为 100。 |

支持尺寸：`auto`, `1024x1024`, `1024x1536`, `1536x1024`, `2048x2048`, `2048x1152`, `3840x2160`, `2160x3840`, `2048x1360`, `1360x2048`, `1152x2048`, `2048x1536`, `1536x2048`, `2048x880`, `880x2048`, `688x2048`, `2048x688`, `2048x1024`, `1024x2048`

#### GPT Image 2.5

{% hint style="info" %}
推荐使用 `gpt-image-2.5-flare-oai` 进行快速图片生成，使用 `gpt-image-2.5-sunburst-oai` 进行精细图片编辑。非 `-oai` 名称提供相同接口能力。
{% endhint %}

`quality` 支持 `low`、`medium`、`high`、`xhigh`、`max` 和 `auto`，默认值为 `auto`。透明背景需同时设置 `background="transparent"` 和 `output_format="png"` 或 `"webp"`。

费用按响应 `usage` 中的实际 token 用量计算（每 100 万 token）：

| 类型 | 输入 | 缓存输入 | 输出 |
| --- | ---: | ---: | ---: |
| 文本 | $5.00 | $1.25 | - |
| 图片 | $8.00 | $2.00 | $30.00 |

`usage.input_tokens_details` 区分文本、图片和缓存输入 token，`usage.output_tokens_details` 返回图片输出 token。token 仅在顶层 `usage` 汇总返回，不会附加到每个 `data[]` 图片对象。

### 3. 接口详情

{% openapi-operation spec="openai-zh-global" path="/v1/images/generations" method="post" %}
[OpenAPI OpenAI](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/global/zh/openai.bundled.yaml)
{% endopenapi-operation %}
