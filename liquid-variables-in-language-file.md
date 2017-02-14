#Using liquid Variables in the language file
##### The power of variables ( ͡° ͜ʖ ͡°)
---
### Step 1: Define variables in the language file

Navigate to the language file:
> theme/locales/en.default.json

**Define** the variable in the sentence with double handlebars liquid statement.

Example:
> "warranty_message": "This **{{ vendor }}** comes with a **{{ warranty }}**."

---

### Step 2: Accessing variables in liquid files

Assign the **variables**.

>{% assign **vendor** = product.vendor %}
>
>{% assign **warranty** = product.metafields.c_f.product_warranty %}

Rendering the language property.

> {{ 'products.product.warranty_message' | t: **vendor:vendor, warranty:warranty**   }}
