---
layout: post
title: Add social media tags
author: unknown
excerpt: Use this code to create dynamic liquid-created social media tags for products, articles, pages and more. Supports Facebook's Open Graph, Twitter Cards, Pinterest's Pins
order: 1
---
{% raw %}


Create Liquid Social Media Tags
Use this code to create dynamic liquid-created social media tags for products, articles, pages and more. Supports Facebook's Open Graph, Twitter Cards, Pinterest's Pins

To use this, simply create a new Shopify snippet called `social-media-tags.liquid` and paste this code into it and save.

After that, where ever in your theme you have your meta tags, type in `{%- include 'social-media-tags' -%}`.

And that's it!

The code supports Shopify's newly created whitespace reducing tags.

Note: There are some parts in this code that may not work for you, notably the tags `{{ 'logo.png' | asset_url }}`. Unless you actually have a file called logo.png in your Assets Folder, this will need changing to reflect your files. Also, remember to change fb:app_id to your actual FB App ID

```liquid
{%- comment -%}
Add Facebook and Pinterest Open Graph meta tags to product pages
for friendly Facebook sharing and Pinterest pinning.
Remember that Facebook requires any image using the og:image/og:image:secure_url to be a minimum of 200px x 200px in resolution
More info Open Graph meta tags
- https://developers.facebook.com/docs/opengraph/using-objects/
- https://developers.pinterest.com/rich_pins/
Use the Facebook Open Graph Debugger for validation (and cache clearing)
- http://developers.facebook.com/tools/debug
Validate your Pinterest rich pins
- https://developers.pinterest.com/rich_pins/validator/
{%- endcomment -%}
<meta property="fb:app_id" content="****************">
{%- if template contains 'product' -%}
<meta property="og:type" content="product">
<meta property="og:title" content="{{ product.title | strip_html | escape }}">
<meta property="og:url" content="{{ canonical_url }}">
{%- for image in product.images limit:3 -%}
<meta property="og:image" content="http:{{ image.src | img_url: 'grande' }}">
<meta property="og:image:secure_url" content="https:{{ image.src | img_url: 'grande' }}">
{%- endfor -%}
<meta property="og:price:amount" content="{{ product.price | money_without_currency | strip_html | escape }}">
<meta property="og:price:currency" content="{{ shop.currency }}">
{%- elsif template contains 'index' -%}
<meta property="og:type" content="website">
<meta property="og:title" content="{{shop.name}} | {{ page_title }}">
<meta property="og:url" content="{{ canonical_url }}">
<meta property="og:description" content="{{ page_description }}">
<meta property="og:image" content="{{ 'logo.png' | asset_url }}">
<meta property="og:image:secure_url" content="{{ 'logo.png' | asset_url }}">

{%- elsif template contains 'article' -%}
<meta property="og:type" content="article">
<meta property="og:title" content="{{ article.title | strip_html | escape }}">
<meta property="og:url" content="{{ canonical_url }}">
<meta property="og:author" content="{{ article.user.homepage }}">
{%- if article.image -%}
<meta property="og:image" content="http:{{ article | img_url: '1024x1024' }}">
<meta property="og:image:secure_url" content="https:{{ article | img_url: '1024x1024' }}">
{%- endif -%}
{%- elsif template == 'password' -%}
<meta property="og:type" content="website">
<meta property="og:title" content="{{ shop.name }}">
<meta property="og:url" content="{{ shop.url }}">
{%- if settings.logo_use_image -%}
<meta property="og:image" content="http:{{ 'logo.png' | asset_url }}">
<meta property="og:image:secure_url" content="https:{{ 'logo.png' | asset_url }}">
{%- endif -%}
{%- else -%}
<meta property="og:type" content="website">
<meta property="og:title" content="{{ page_title }}">
<meta property="og:url" content="{{ canonical_url }}">
{%- if settings.logo_use_image -%}
<meta property="og:image" content="http:{{ 'logo.png' | asset_url }}">
<meta property="og:image:secure_url" content="https:{{ 'logo.png' | asset_url }}">
{%- endif -%}
{%- endif -%}
{%- unless template contains 'index' -%}
{%- if page_description -%}
<meta property="og:description" content="{{ page_description }}">
{%- endif -%}
{%- endunless -%}
<meta property="og:site_name" content="{{ shop.name }}">
{%- comment -%}
This snippet renders meta data needed to create a Twitter card
for products and articles.
Your cards must be approved by Twitter to be activated
- https://dev.twitter.com/docs/cards/validation/validator
More information:
- https://dev.twitter.com/docs/cards/types/summary-card
{%- endcomment -%}
{%- if template contains 'article' and article.image -%}
<meta name="twitter:card" content="summary_large_image">
{%- elsif template == 'index' and slider_enabled -%}
<meta name="twitter:card" content="summary_large_image">
{%- else -%}
<meta name="twitter:card" content="summary">
{%- endif -%}
{%- comment -%}
Twitter user name of the site, based on theme settings
{%- endcomment -%}
{%- unless settings.social_twitter_url == blank -%}
<meta name="twitter:site" content="@{{ settings.social_twitter_url | split: 'twitter.com/' | last }}">
{%- endunless -%}
{%- if template contains 'index' -%}
<meta name="twitter:title" content="{{ page_title }}">
{%- if settings.home_page_content != blank -%}
<meta name="twitter:description" content="{{ pages[settings.home_page_content].content | strip_html | truncate: 200, '' | escape }}">
{%- else -%}
<meta name="twitter:description" content="{{ page_description | escape }}">
{%- endif -%}

{%- elsif template contains 'product' -%}
<meta name="twitter:title" content="{{ product.title | strip_html | escape }}">
<meta name="twitter:description" content="{{ product.description | strip_html | truncate: 200, '' | escape }}">
<meta name="twitter:image" content="https:{{ product | img_url: 'large' }}">
<meta name="twitter:image:width" content="480">
<meta name="twitter:image:height" content="480">
{%- elsif template contains 'article' -%}
<meta name="twitter:title" content="{{ article.title | strip_html | escape }}">
<meta name="twitter:description" content="{{ article.excerpt_or_content | strip_html | truncate: 200, '' | escape }}">
{%- if article.image -%}
<meta property="twitter:image" content="https:{{ article | img_url: '1024x1024' }}">
{%- endif -%}
{%- endif -%}
```


{% endraw %}
