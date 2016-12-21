# Image Options

## Image Tags

Add the **"|"** known as a *"pipe"* or *"filter"* at the end of the liquid output handlebars tag, followed by **img_tag**. This will render the image with the HTML code.

```
{{ 'smirking_gnome.gif' | asset_url | img_tag }}
```
Result:
```
<img src="//cdn.shopify.com/s/files/1/0147/8382/t/15/assets/smirking_gnome.gif?v=1384022871" alt="" />
```
#### Alternative Text
```
{{ variant | img_tag: 'alternate text' }}
```
Result:
```
<img src="//cdn.shopify.com/s/files/1/0159/3350/products/red_shirt_small.jpg?v=1398706734" alt="Red Shirt Small" />
```

#### Adding Classes
```
{{ line_item | img_tag: 'alternate text', 'css-class' }}
```
Result:
```
<img src="//cdn.shopify.com/s/files/1/0159/3350/products/red_shirt_small.jpg?v=1398706734" alt="alternate text" class="css-class" />
```
Note: Add a space after the class to add more classes.

#### Image size

```
{{ collection | img_tag: 'alternate text', 'css-class', 'large' }}
```
Result:
```
<img src="//cdn.shopify.com/s/files/1/0159/3350/products/red_shirt_small.jpg?v=1398706734" alt="alternate text" class="css-class" />
```
For more information on image size, continue below.

## Image Size
```
{{ product.image | img_url: 'large' }}
```

Results:
```
//cdn.shopify.com/s/files/1/0246/0527/files/logo_400x400.png?42
```


| Option | Size |
| --- | --- |
| pico | 16 x 16 px |
| icon | 32 x 32 px |
| thumb | 50 x 50 px |
| small | 100 x 100 px |
| compact | 160 x 160 px |
| medium | 240 x 240 px |
| large | 480 x 480 px |
| grande | 600 x 600 px |
| original | 1024 x 1024 px |
| master | original image size |

Note: The maximum image size is *2048 x 2048 px*.

Note: add "**| img_tag**" after the *img_url* to add the html image tags.


## Image crop

```
{{ product.image | img_url: '400x400', crop: 'bottom' }}
```

Results:
```
//cdn.shopify.com/s/files/1/0246/0527/files/logo_400x400.png?42
```


* top
* center
* bottom

Note: add "**| img_tag**" after the crop to add the html image tags.

## Image Scale

Specify the pixel density of the image.

```
{{ product.image | img_url: '400x400', scale: 2 }}
```

Standard Options:
* 2
* 3


# Upload and Accessing Images from Shopify Admin.

To upload images into the front-end. Go to the **Shopify Admin** then ** Settings > Files**.

Click the button **Upload files**.

Once uploaded, go to your code and paste the line below in.  

```
{{ 'logo.png' | file_img_url }}
```

The name must relate to the uploaded file name including the file extension.
