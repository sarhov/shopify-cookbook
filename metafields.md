# Metafields + Shopify

ShopifyFD
Google Chrome
Custom Fields

To add additional fields to add extra data to a collection, product, articles, etc.

**{{ metafields.c_f.collection_image }}**


## Markers

Markers are used to select where you want to metafield be to used in the store. The options are :  

| Marker | Detail |
|--- | --- |
| [a] | articles |
| [c] | collections |
| [g] | pages |
| [p] | product |



## Create a Metafield

Go to **Shopify Admin** then **Settings**.
Load your **ShopifyFD** & **Custom Fields** Google Chrome Plugin in your menu bar.

In the page find, **Store Metafields**

Select from the drop down **"Select or create a metafield"**.

Add in the following:

#### 1st Line

c_f

#### 2nd line

The name of the feature.

e.g. collection_image

#### 3rd Line

Using a *marker* (see the section above), followed by a description of the metafield's function.

e.g. [c] Image to use for the collection page.

#### Save

Once complete, select the button **save**.


## Adding Data to the metafield

Navigate to the page which you've setup the metafield.

E.g. Go to a collection page if you setup your marker as **[c]**. To get to the collection page go to **Online Store > Collections**.

Once there, load the **ShopfiyFD** and **Custom Fields** plugin in your *Google Chrome* browser.

Go to the **Custom Fields** section. Add in the information you need.

Then select **Save Custom Fields** button.

## Displaying the metafield in liquid

Go to the correct template assosicated with your metafields marker.

Add the code below:
```
{{ metafields.c_f.collection_image }}
```
Change the variable after the last **dot** or **"."** to your **3rd Line**.


## Links:
https://freakdesign-us.s3.amazonaws.com/shopify/custom_fields/freakdesign-custom-fields-for-shopify-guide.pdf
