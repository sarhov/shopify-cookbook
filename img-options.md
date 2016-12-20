# Image Options

## Image Size

**{{ product.image | img_url: 'large' }}**


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

To crop and image

## Image crop

```
{{ product.image | img_url: '400x400', crop: 'bottom' }}
```

* top
* center
* bottom

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
