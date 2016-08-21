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
