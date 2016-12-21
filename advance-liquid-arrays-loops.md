# Advance Liquid Arrays

https://code.graygilmore.com/2014/advanced-arrays-in-shopify-s-liquid


```liquid
{% assign myArray = "item-1,item-2,item-3" | split: "," %}

{% for item in myArray %}
  {{ item }}
{% endfor %}
```

Results:
```
item-1
item-2
item-3
```

# Advance Liquid Loops

**i** becomes the variable.

**(1..3)** is the range of numbers to be iterated through.

Each loop will replace **i** with a **number**.

```
{% for i in (1...3) %}

        {% capture title %}title {{ i }}{% endcapture %}
        {{ [title] }}

{% endfor %}
```

Results:
```
title 1
title 2
title 3
```

Notes: Using the capture method for variables need to be escaped with square brackets. e.g. **{{ [title] }}**


## Loop Example

#### Product Tags
```
{% capture productTags %}{% for tags in product.tags %}{{ tags }}, {% endfor %}{% endcapture %}
{% assign productTagsSplit= productTags | strip | split: ", " %}

{{ productTagsSplit }}
```
