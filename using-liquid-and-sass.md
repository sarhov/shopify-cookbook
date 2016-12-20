---
layout: post
title: Using liquid and sass
excerpt: ...
---

{% raw %}

_Taken from [https://medium.com/@josephbergdoll/writing-sass-for-shopify-22c7568dd8f2](https://medium.com/@josephbergdoll/writing-sass-for-shopify-22c7568dd8f2)_

```scss
@mixin font-file($asset-font-name) {
 src: url(‘ {{ “#{$asset-font-name}.eot” | asset_url }} ‘);
 src: url(‘ {{ “#{$asset-font-name}.eot” | asset_url }} ?#iefix ‘) format(“embedded-opentype”),
 url(‘ {{ “#{$asset-font-name}.woff” | asset_url }} ‘) format(“woff”),
 url(‘ {{ “#{$asset-font-name}.ttf” | asset_url }} ‘) format(“truetype”),
 url(‘ {{ “#{$asset-font-name}.svg” | asset_url }} ‘) format(“svg”);
}
@mixin background-file($asset-image-with-extension) {
 background-image: url(‘ {{ “#{$asset-image-with-extension}” | asset_url }} ‘)
}
```

## More information about using Liquid with Scss

* [https://stackoverflow.com/questions/11178265/less-css-and-escaping-liquid-syntax-for-shopify-theme-development](https://stackoverflow.com/questions/11178265/less-css-and-escaping-liquid-syntax-for-shopify-theme-development)
* [http://sass-lang.com/documentation/file.SASS_REFERENCE.html#interpolation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#interpolation)

`h1 { color: #{'{{ settings.brand_colour }}'}; }`

`font-size:#{' {% if settings.main-title-uppercase %} '}calc(16px * 0.875) !important#{' {% endif %} '};`

`color:#{' {{ settings.light-text-colour }} '};`



{% endraw %}
