---
layout: post
title: Responsive images
author: unknown
excerpt: Using the new [image size a parameters](https://help.shopify.com/themes/liquid/filters/url-filters#size-parameters) we can easily serve up responsive images
order: 1
---
{% raw %}

# Lazy load images in liquid

Using the new [image size a parameters](https://help.shopify.com/themes/liquid/filters/url-filters#size-parameters) we can easily serve up responsive images:

```liquid
<img class="lazyload"
        src="{{ product.images[0] | img_url: '480px', format: 'pjpg' }}"
        srcset="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="
        data-srcset="{{ product.images[0] | img_url: '480x', format: 'pjpg' }} 480w,
          {{ product.images[0] | img_url: '160x', format: 'pjpg' }} 160w,
          {{ product.images[0] | img_url: '240x', format: 'pjpg' }} 240w,
          {{ product.images[0] | img_url: '600x', format: 'pjpg' }} 600w,
          {{ product.images[0] | img_url: '1024x', format: 'pjpg' }} 1024w"
        data-sizes="auto"
        alt="{{ product.title | escape }}">
```





------------
Collete - snippets/collecton-carousel.liquid

```liquid
Option 1 - file_img_url

{% capture images %}{{ collection.metafields.c_f.collection_carousel }}{% endcapture %}
{% assign imagesArray = images | split : "," %}

{% for item in imagesArray %}

			<img
			srcset="{{ item | file_img_url: '350x' }} 350w,
						{{ item | file_img_url: '700x' }} 700w,
						{{ item | file_img_url: '1050x' }} 1050w,
						{{ item | file_img_url: '1400x' }}  1400w"
			sizes="(max-width: 520px) 350px,
				   (max-width: 875px) 700px,
				   (max-width: 1200px) 1050px,
				   (max-width: 1450px) 1400px"
			src="{{ item | file_img_url: '1400x' }}"
			alt="{{collection.title}}">

{% endfor %}
```

```liquid
Option 2 - img_url 
<img
				srcset="{{ collection.image | img_url: '350x' }} 350w,
 			   {{ collection.image | img_url: '700x' }} 700w,
 			   {{ collection.image | img_url: '1050x' }} 1050w,
 			  {{ collection.image | img_url: '1400x' }}  1400w"
				sizes="(max-width: 520px) 350px,
				 (max-width: 875px) 700px,
				 (max-width: 1200px) 1050px,
			            (max-width: 1450px) 1400px"
				src="{{ collection.image | img_url: '1400x' }}"
				alt="{{collection.title}}">

```


{% endraw %}
