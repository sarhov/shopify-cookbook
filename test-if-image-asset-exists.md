# Test if image asset exists in Shopify.

### Liquid Variables
```{% capture vendor %}{{ product.vendor | handleize | lowercase }}{% endcapture %}
{% capture vendorCaseImg %}case-{{ vendor }}.jpg{% endcapture %}
```
### Liquid Image Asset Tag
```
<img src="{{ vendorCaseImg |  file_img_url: '350x' }}">
```
Change file_img_url to any other Shopify image filter.

### Tests if image returns any errors.
```

<script type="text/javascript">

function checkImage(src) {
  var img = new Image();
  img.onload = function() {
    console.log('yes');
  };

  img.onerror = function() {
    console.log('no');

  };

  img.src = src;
}

checkImage('{{ vendorCaseImg |  file_img_url: "350x" }}');

</script>
```

##### Recommend replacing the console.logs with jQuery to hide img if returns false.

___

AM

18 - 01 - 17
