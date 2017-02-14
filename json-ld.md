
###JSON-LD for Seo application
######  This snippet was installed by the JSON-LD for SEO application.

  It could be updated from time to time as we add new JSON-LD features, so we
  don't recommend editing it manually. If you run into an issues, or would like
  to request a JSON-LD feature, please contact us at help@discolabs.com.

  Thanks!

  **Gavin from Disco**



```html
{% unless jsonld_for_seo_applied %}{% capture jsonld_for_seo_protocol %}{{ canonical_url | split: '://' | first }}://{% endcapture %}<script type="application/ld+json">
{
    "@context": "{{ jsonld_for_seo_protocol }}schema.org",
    "@type": "WebSite",
    "url": "{{ jsonld_for_seo_protocol }}{{ shop.domain }}",
    "potentialAction": {
        "@type": "SearchAction",
        "target": "{{ jsonld_for_seo_protocol }}{{ shop.domain }}/search?q={query}",
        "query-input": "required name=query"
    }
}
</script>
{%- unless shop.metafields.jsonld.hide_business == "true" -%}
{%- assign jsonld_business_type = shop.metafields.jsonld.type | default: 'Organization' -%}
<script type="application/ld+json">
{
    "@context": "{{ jsonld_for_seo_protocol }}schema.org",
    "@type": {{ jsonld_business_type | json }},
    "name": {{ shop.name | json }},
    "url": "{{ jsonld_for_seo_protocol }}{{ shop.domain }}",
    "description": {{ shop.description | json }},{% unless shop.phone == blank %}
    "telephone": {{ shop.phone | json }},{% endunless %}{% unless shop.metafields.jsonld.logo == blank %}
    "logo": {{ shop.metafields.jsonld.logo | json }},{% endunless %}{% unless shop.metafields.jsonld.image == blank %}
    "image": {{ shop.metafields.jsonld.image | json }},{% endunless %}{% unless shop.metafields.jsonld.openingHours == blank %}
    "openingHours": {{ shop.metafields.jsonld.openingHours | json }},{% endunless %}
    "sameAs": {{ shop.metafields.jsonld.sameAs | default: '' | split: ',' | json }},{% if jsonld_business_type == 'LocalBusiness' %}
    "hasMap": "{% unless shop.metafields.jsonld.hasMap == blank %}{{ shop.metafields.jsonld.hasMap }}{% else %}https://www.google.com/maps/@{{ shop.latitude }},{{ shop.longitude }},16z{% endunless %}",
    "geo": {
        "@type": "GeoCoordinates",
        "latitude": {{ shop.latitude | json }},
        "longitude": {{ shop.longitude | json }}
 	  },{% endif %}
    "address": {
        "@type": "PostalAddress",
        "streetAddress": {{ shop.address.street | json }},
        "addressLocality": {{ shop.address.city | json }},
        "addressRegion": {{ shop.address.province | json }},
        "postalCode": {{ shop.address.zip | json }},
        "addressCountry": {{ shop.address.country | json }}
    }
}
</script>
{%- endunless -%}
{%- unless shop.metafields.jsonld.hide_products == "true" -%}
{%- if template contains 'product' -%}
{%- assign jsonld_for_seo_object = product -%}
<script type="application/ld+json">
{
	"@context": "{{ jsonld_for_seo_protocol }}schema.org",
	"@type": "Product",{% unless shop.metafields.jsonld.hide_vendor == "true" %}
  "brand": {
		"@type": "Brand",
		"name": {{ product.metafields.jsonld.vendor | default: shop.metafields.jsonld.vendor | default: product.vendor | json }}
	},{% endunless %}
	"sku": {{ product.selected_or_first_available_variant.sku | json }},
	"description": {{ product.description | strip_html | json }},
	"url": {{ canonical_url | json }},
	"name": {{ product.title | json }},{% if product.featured_image %}
	"image": "https:{{ product.featured_image | product_img_url: 'grande' }}",{% endif %}{% unless shop.metafields.jsonld.itemCondition == blank %}
	"itemCondition": "http://schema.org/{{ shop.metafields.jsonld.itemCondition }}",{% endunless %}
	"offers": [{% for variant in product.variants %}{
		"@type": "Offer",
		"price": "{{ variant.price | divided_by: 100.0 }}",
		"priceCurrency": "{{ shop.currency }}",
		"availability": "{% if variant.available %}InStock{% else %}OutOfStock{% endif %}"
	}{% unless forloop.last %},{% endunless %}{% endfor %}]{% if product.metafields.yotpo.reviews_count and product.metafields.yotpo.reviews_count != "0" %},
	"aggregateRating": {
	  "@type": "AggregateRating",
	  "ratingValue": {{ product.metafields.yotpo.reviews_average }},
	  "ratingCount": {{ product.metafields.yotpo.reviews_count }}
	}{% elsif product.metafields.loox.num_reviews and product.metafields.loox.num_reviews != "0" %},
	"aggregateRating": {
	  "@type": "AggregateRating",
	  "ratingValue": {{ product.metafields.loox.avg_rating }},
	  "ratingCount": {{ product.metafields.loox.num_reviews }}
	}{% elsif product.metafields.ssw.count_rate and product.metafields.ssw.count_rate != "0" %},
	"aggregateRating": {
	  "@type": "AggregateRating",
	  "ratingValue": {{ product.metafields.ssw.avg_rate }},
	  "ratingCount": {{ product.metafields.ssw.count_rate }}
	}{% endif %}
}
</script>
{%- endif -%}
{%- endunless -%}
{% if template contains 'article' %}{% assign jsonld_for_seo_object = article %}
<script type="application/ld+json">
{
	"@context": "{{ jsonld_for_seo_protocol }}schema.org",
	"@type": "Article",
	"url": {{ canonical_url | json }},
	"mainEntityOfPage": {{ canonical_url | json }},
	"name": {{ article.title | json }},
	"author": {{ jsonld_for_seo_object.metafields.jsonld.author | default: article.author | json }},
	"publisher": {
	  "@type": "Organization",{% unless shop.metafields.jsonld.logo == blank %}
    "logo": {
      "@type": "ImageObject",{% unless shop.metafields.jsonld.logoWidth == blank %}
      "width": {{ shop.metafields.jsonld.logoWidth | json }},{% endunless %}{% unless shop.metafields.jsonld.logoHeight == blank %}
      "height": {{ shop.metafields.jsonld.logoHeight | json }},{% endunless %}
      "url": {{ shop.metafields.jsonld.logo | json }}
    },{% endunless %}
	  "name": {{ shop.name | json }}
	},
	"headline": {{ article.title | json }},
	"image": {
    "@type": "ImageObject",{% assign articleImageWidth = article.metafields.jsonld.imageWidth | default: shop.metafields.jsonld.articleImageWidth | default: 1024 %}
    "width": {{ articleImageWidth | json }},{% assign articleImageHeight = article.metafields.jsonld.imageHeight | default: shop.metafields.jsonld.articleImageHeight | default: 1024 %}
    "height": {{ articleImageHeight | json }},{% if article.image %}
	  "url": "https:{{ article | img_url: '1024x1024' }}"{% else %}
	  "url": "https://cdn.shopify.com/s/images/admin/no-image-large.gif"{% endif %}
	},
	"datePublished": "{{ article.created_at }}",
	"dateModified": "{{ article.published_at }}",
	"description": {{ article.summary_html | strip_html | json }},
	"articleBody": {{ article.body_html | strip_html | json }}
}
</script>{% endif %}{% if template contains 'collection' %}{% assign jsonld_for_seo_object = collection %}
{% endif %}{% if jsonld_for_seo_object.metafields.jsonld.type == 'VideoObject' %}
<script type="application/ld+json">
{
  "@context": "{{ jsonld_for_seo_protocol }}schema.org",
  "@type": "VideoObject",
  "name": {{ jsonld_for_seo_object.metafields.jsonld.name | json }},
  "description": {{ jsonld_for_seo_object.metafields.jsonld.description | json }},
  "thumbnailUrl": {{ jsonld_for_seo_object.metafields.jsonld.thumbnailURL | json }},
  "duration": {{ jsonld_for_seo_object.metafields.jsonld.duration | json }},
  "embedUrl": {{ jsonld_for_seo_object.metafields.jsonld.embedURL | json }},
  "uploadDate": "{{ jsonld_for_seo_object.metafields.jsonld.uploadDate | default: jsonld_for_seo_object.published_at }}",
  "publisher": {
	  "@type": "Organization",{% unless shop.metafields.jsonld.logo == blank %}
    "logo": {
      "@type": "ImageObject",{% unless shop.metafields.jsonld.logoWidth == blank %}
      "width": {{ shop.metafields.jsonld.logoWidth | json }},{% endunless %}{% unless shop.metafields.jsonld.logoHeight == blank %}
      "height": {{ shop.metafields.jsonld.logoHeight | json }},{% endunless %}
      "url": {{ shop.metafields.jsonld.logo | json }}
    },{% endunless %}
	  "name": {{ shop.name | json }}
	}
}
</script>{% endif %}{% unless jsonld_for_seo_object.metafields.jsonld.recipeCategory == blank %}{% assign jsonld_for_seo_default_image = jsonld_for_seo_object.image | img_url: 'grande' | prepend: 'https:' %}
<script type="application/ld+json">
{
  "@context": "{{ jsonld_for_seo_protocol }}schema.org",
  "@type": "Recipe",{% unless jsonld_for_seo_object.metafields.jsonld.recipeCategory == blank %}
  "recipeCategory": {{ jsonld_for_seo_object.metafields.jsonld.recipeCategory | json }},{% endunless %}{% unless jsonld_for_seo_object.metafields.jsonld.cookTime == blank %}
  "cookTime": {{ jsonld_for_seo_object.metafields.jsonld.cookTime | json }},{% endunless %}{% unless jsonld_for_seo_object.metafields.jsonld.prepTime == blank %}
  "prepTime": {{ jsonld_for_seo_object.metafields.jsonld.prepTime | json }},{% endunless %}{% unless jsonld_for_seo_object.metafields.jsonld.totalTime == blank %}
  "totalTime": {{ jsonld_for_seo_object.metafields.jsonld.totalTime | json }},{% endunless %}
  "nutrition": { {% unless jsonld_for_seo_object.metafields.jsonld.calories == blank %}
    "calories": {{ jsonld_for_seo_object.metafields.jsonld.calories | append: ' calories' | json }},{% endunless %}
    "@type": "NutritionInformation"
  },
  "recipeIngredient": {{ jsonld_for_seo_object.metafields.jsonld.recipeIngredient | default: '' | split: ';' | json }},
  "recipeInstructions": {{ jsonld_for_seo_object.metafields.jsonld.recipeInstructions | default: '' | split: ';' | json }},
  "name": {{ jsonld_for_seo_object.metafields.jsonld.name | default: jsonld_for_seo_object.title | escape | json }},
  "description": {{ jsonld_for_seo_object.metafields.jsonld.description | default: jsonld_for_seo_object.excerpt_or_content | strip_html | truncatewords: 120 | escape | json }},
  "author": {{ jsonld_for_seo_object.metafields.jsonld.author | default: jsonld_for_seo_object.author | json }},
  "image": {{ jsonld_for_seo_object.metafields.jsonld.image | default: jsonld_for_seo_default_image | json }}
}
</script>{% endunless %}{% endunless %}{% assign jsonld_for_seo_applied = true %}

```
