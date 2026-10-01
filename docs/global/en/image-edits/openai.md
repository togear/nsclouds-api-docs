# OpenAI - Image Edits

### 1. Overview

OpenAI exposes image edit capabilities in this environment.

{% hint style="success" %}
This endpoint provides GPT Image 2 and GPT Image 2.5 capabilities through the OpenAI Images API.
{% endhint %}

**Supported models：**

* `gpt-image-2`
* `gpt-image-2.5-flare`
* `gpt-image-2.5-flare-oai`
* `gpt-image-2.5-sunburst`
* `gpt-image-2.5-sunburst-oai`


### 2. Image Model Parameter Notes

#### gpt-image-2

{% hint style="info" %}
`gpt-image-2` supports editing from one or more input images. `mask` is optional, and transparent areas represent regions to edit.
{% endhint %}

| Parameter | Support |
| --- | --- |
| `image` | Required. Supports a single image or multiple images; accepts URLs, base64, data URIs, or file uploads. |
| `prompt` | Required. Reference maximum length is 32000 characters. |
| `mask` | Optional. Transparent areas represent the edit region. |
| `n` | Optional. Reference range is 1-10; the actual number of returned images can be lower than requested. |
| `size` | Optional. Supports `auto` and the fixed sizes listed below. |
| `quality` | Optional. Supports `low`, `medium`, and `high`; omitted, `auto`, and `standard` are billed as `high`. |
| `background` | Optional. Supports `opaque` and `auto`. |
| `output_format` | Optional. Supports `png` and `jpeg`. |

Supported sizes: `auto`, `1024x1024`, `1024x1536`, `1536x1024`, `2048x2048`, `2048x1152`, `3840x2160`, `2160x3840`, `2048x1360`, `1360x2048`, `1152x2048`, `2048x1536`, `1536x2048`, `2048x880`, `880x2048`, `688x2048`, `2048x688`, `2048x1024`, `1024x2048`

#### GPT Image 2.5

{% hint style="info" %}
Use `gpt-image-2.5-sunburst-oai` for detailed image editing and `gpt-image-2.5-flare-oai` for fast image generation. Names without the `-oai` suffix expose the same API capabilities.
{% endhint %}

The endpoint accepts one or more multipart input images; repeat the `image[]` field for multiple references. It also supports `moderation=low|auto`.

`quality` supports `low`, `medium`, `high`, `xhigh`, `max`, and `auto`, with `auto` as the default. For transparent backgrounds, set `background="transparent"` and use `output_format="png"` or `"webp"`.

Requests are billed from actual token usage in the response (per one million tokens):

| Modality | Input | Cached input | Output |
| --- | ---: | ---: | ---: |
| Text | $5.00 | $1.25 | - |
| Image | $8.00 | $2.00 | $30.00 |

`usage.input_tokens_details` separates text, image, and cached input tokens, while `usage.output_tokens_details` reports image output tokens. Tokens are aggregated in the top-level `usage` object and are not attached to individual `data[]` image objects.

### 3. API Details

{% openapi-operation spec="openai-en-global" path="/v1/images/edits" method="post" %}
[OpenAPI OpenAI](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/global/en/openai.bundled.yaml)
{% endopenapi-operation %}
