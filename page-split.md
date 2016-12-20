---
layout: post
title: Page split
excerpt: Using liquid, we can use a token inside a block of text to mark sections in that content, and therefore turn one block into multiple.
---
{% raw %}

# Split a block of content

Using liquid, we can use a token inside a block of text to mark sections in that content, and therefore turn one block into multiple.

```liquid
{%- assign pageContent = page.content | split:'<!-- split -->' -%}
{%- if pageContent.size > 1 -%}
    <div>{{ pageContent[0] }}</div>
    <div>{{ pageContent[1] }}</div>
{%- else -%}
    <div>{{ page.content }}</div>
{%- endif -%}
```


{% endraw %}
