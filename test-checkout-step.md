---
layout: post
title: Test checkout step
author: unknown
excerpt: Note that if you’re doing something on the shipping methods step, you need to not only check for `Shopify.Checkout.step === 'shipping_method'`
order: 1
---
{% raw %}

## Test what step of the checkout you are in

`if(Shopify.Checkout.step === 'contact_information'){}`
`if(Shopify.Checkout.step === 'shipping_method'){}`
`if(Shopify.Checkout.step === 'payment_method'){}`

Note that if you’re doing something on the shipping methods step, you need to not only check for `Shopify.Checkout.step === 'shipping_method'` but also for `$('[data-poll-refresh]').length === 0` to ensure that dynamic shipping rates have been loaded in.


{% endraw %}
