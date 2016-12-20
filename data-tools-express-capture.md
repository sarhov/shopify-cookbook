---
layout: post
title: Data tools express capture
author: unknown
excerpt: The setup instructions on the Data Tools website help you get set up to a point, but there are some considerations for the Shopify Checkout. Please note it is only possible to install Express Capture on a Shopify Plus store.
order: 1
---
{% raw %}

#Data Tools Express Capture instructions

##Additional setup information for Shopify Checkout.

The setup instructions on the Data Tools website help you get set up to a point, but there are some considerations for the Shopify Checkout. Please note it is only possible to install Express Capture on a Shopify Plus store.

`{SubBuilding}` = just the sub building

`{{SubBuilding}, }{Line1}` = sub building and line, with a comma and space if sub building is not blank

`{StreetAddress}` = the address of the building, without sub building information

The trick is you need to put curly brackets if it's a custom field.

The main issue was the State/Territory not populating the correct value. To fix this issue, the state field should be mapped as `County Name` not as `County`.

`County` = abbreviated state

`County Name` = Full text state





{% endraw %}
