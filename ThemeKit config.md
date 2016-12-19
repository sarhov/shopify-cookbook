# ThemeKit Config

ThemeKit enables you to connect to your Shopify Theme to upload changes made in your code editor.

Download ThemeKit by following the Installation instructions:
http://shopify.github.io/themekit/

Add a **config.yml** file to the root directory of your Shopify Theme folder. And paste the Config Structure below into **config.yml**.


### Config Structure

```
development:
  password: d684290dcb925b27dd6e58ac3914e446
  store: storename.myshopify.com
  theme_id: 106160196
  bucket_size: 40
  refill_rate: 2
```

Below are 3 variables that need to match the Shopify store for ThemeKit to work.

### 1. Password
The password is located in the Shopify online store. Go to **Apps > Private Apps (Top right corner)**.

Click on **Create Private App**.

In the **Title** Input, add a name e.g. *"Theme"*.

Change all of the **Permissions** to be **Read & Write Access**. If that option isn't available, select **Read Access**.

Then click **Save app**.

You will be redirected to the **Private Apps** page.

Copy the **Password** key under the Private App key just created.
The key will look like e.g. *d684290dcb925b27dd6e58ac3914e446*.

Paste and Replace the **Password** into the **config.yml file** where the file says **password:**.

File Save.


### 2. Store

Copy and paste the store URL into the **config.yml** file where the file says **store:**.

### 3. Theme Id

Go to your Shopify store.

Navigate to **Online Store > Themes.**

Select the Theme you want to upload and make changes to by selecting the **Three Dots Symbol**, then select **Edit HTML/CSS**.

In the URL there will be a number at the end. This is the theme Id. Copy the Id number. e.g. https://mystore.myshopify.com/admin/themes/150328391. **150328391** will be the theme Id.

Copy and paste the theme ID into the **config.yml** file where the file says **theme_id:**.

---
## Using ThemeKit

Go to the command line.

Navigate your you theme folder root directory.

To start ThemeKit type:

```
theme watch
```  

Now when you save files you will be uploading the changes to your selected theme. 
