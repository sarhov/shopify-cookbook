---
layout: post
title: Money format currency
author: unknown
excerpt: .We had a UK Store where the currency was set to show as £, but in some cases where values were affected by javascript logic, the default '$' symbol showed.
order: 1
---
{% raw %}

#Shopify money formats

##Currency values in JS vs Liquid

We had a UK Store where the currency was set to show as £, but in some cases where values were affected by javascript logic, the default '$' symbol showed.

In the javascript, we needed to change

`var formattedPrice = Shopify.formatMoney(variant.price, "");`

It required a value to specificy the shop's money format:

`var formattedPrice = Shopify.formatMoney(variant.price, "{{shop.money_format}}" );`

And in another instance for variants:

`var cartTotal = Shopify.formatMoney(data.total_price, "{{shop.money_format}}");`



{% endraw %}
