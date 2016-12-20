---
layout: post
title: Add content to checkout
author: Peter
excerpt: ...
order: 1
---

{% raw %}

```
{% capture ORDER_CONFIRMATION_RETURNS_INFO %}
<div>
  <h2>Returns information</h3>
  <p>No returns!</p>
</div>
{% endcapture %}

<script>
  Shopify.Checkout.OrderStatus.addContentBox({{ ORDER_CONFIRMATION_RETURNS_INFO | json }})
</script>
```

{% endraw %}
