# Escape Liquid in SCSS

Expected output:
```
a {
  color: {{ settings.link-color }};
 }
```
```
a{
color: #{'{{ settings.link-color }}'};
}
```

#### Reuasble liquid:
```
$myVar: #{'{{ settings.font-family }}'};

h1{
font-family: $myVar;
}
```

#### Using a sass variable from the current file:
```
$var1: #fff;
$var2: #{'{% if settings.colour %}{{ settings.colour }}{% else %}'}$var1#{'{% endif %}'};
```

#### Liquid if statement:

```
body{

/* {% if settings.background-image %} /

background: url(#{'{{ settings.background-image | asset_url }}'}) center no-repeat;

/ {% else %} /

background: whitesmoke;

/ {% endif %} /

}
```

#### Liquid outside a css statement:
If we wrote / {{ settings.custom-css }} / then our compiled liquid would be inside the comments making it useless.
We need liquid to create the ending and opening comments when its compiled,
however if we wrote / {{ settings.custom-css | prepend: '/' | append: '/' }} / the string: ' | append: '
is still seen as being outside the comments.
We need to escape them untill liquid can create them so we add an extra character and then remove it.
```
{{ settings.custom-css | prepend: '/' | append: '/' | remove: '' }} /

{% if settings.custom-css %}{{ settings.custom-css | prepend: '/' | append: '/' | remove: '' }}{% endif %} */
```
