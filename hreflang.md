---
layout: post
title: Hreflang
author: unknown
excerpt: bi-directional links that reference each other and themselves in a network - x-default being the fallback for all regions outside what is specified.
order: 1
---
{% raw %}

# hreflang attribute and http lang
handling multi-language websites

### hreflang:

bi-directional links that reference each other and themselves in a network - x-default being the fallback for all regions outside what is specified.

Canonical liquid tag incorporated for each region

Add the below to the head:
```
<link rel="alternate" hreflang="x-default" href="{{ canonical_url | replace: shop.domain, 'au.kirstinash.com' }}" />
<link rel="alternate" hreflang="en-EU" href="{{ canonical_url | replace: shop.domain, 'eu.kirstinash.com' }}" />
<link rel="alternate" hreflang="en-NZ" href="{{ canonical_url | replace: shop.domain, 'nz.kirstinash.com' }}" />
<link rel="alternate" hreflang="en-GB" href="{{ canonical_url | replace: shop.domain, 'uk.kirstinash.com' }}" />
<link rel="alternate" hreflang="en-US" href="{{ canonical_url | replace: shop.domain, 'us.kirstinash.com' }}" />
```

##### hreflang guides:
https://moz.com/blog/using-the-correct-hreflang-tag-a-new-generator-tool
https://www.sistrix.com/hreflang-guide/

##### canonical tags:
https://ecommerce.shopify.com/c/shopify-discussion/t/hreflang-tags-374074

##### hreflang validator tools:
http://flang.dejanseo.com.au/
https://technicalseo.com/seo-tools/hreflang/

---

### Associated http lang attribute in the head:

Capture from settings and place on html tag - to make the hrefland syntax for each

```
{% capture lange %}
	{% case settings.region %}
		{% when 'nz' %}
			en-NZ
		{% when 'uk' %}
			en-GB
		{% when 'us' %}
			en-US
		{% when 'australia' %}
			en-AU
		{% when 'europe' %}
			en-EU
		{% else %}
			en
	{% endcase %}
{% endcapture %}

<html lang="{{ lange }}"> 
```


{% endraw %}
