---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/image-generations/openai-image-generations
---

# OpenAI

### 1. Overview

OpenAI's image generation API, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `gpt-image-2` (image_generation mode)

### 2. Billing

`gpt-image-2-oai` is billed by actual tokens in the top-level response `usage`. Legacy `gpt-image-2` retains per-image billing, with the unit price determined by pixel count (width × height) and the `quality` tier. Use the selected model's pricing configuration for unit prices.

### 3. API Details

{% openapi-operation spec="openai-en-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/openai.bundled.yaml)
{% endopenapi-operation %}
