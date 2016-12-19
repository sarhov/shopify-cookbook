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

# Loops

**i** becomes the variable.

**(1..3)** is the range of numbers to be iterated through.

Each loop will replace **i** with a **number**. 

```
{% for i in (1...3) %}

        {% capture featureLink %}title{{ i }}{% endcapture %}
                   <h3>{{ settings.[featureTitle] }}</h3>
{% endfor %}
```
