# Add a field to the checkout via JavaScript

Using some simple JavaScript we can inject a field into the Shopify checkout (Plus customers only)

```js
var insertAttr = function( attr ) {
   var inputTemplate = <input type='hidden' value='" + attr + "name='checkout[attributes]["attr-name"]'>;
   $('.main form').append();
}
```
