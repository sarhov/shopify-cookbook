#QuickShot - Download + Upload - Blogs, Pages, Products, Themes, Metafields Data and more!
#### A Shopify theme development tool. Quickshot is super fast and feature rich. Everything you need to design and develop sites on Shopify.
* Supports uploading to multiple Shopify stores and themes
* Easy to use configuration wizard
* Uploads/downloads in parallel greatly reducing transfer times
* Supports autocompiling scss locally before uploading to Shopify
* Supports autocompiling Babel/ES6 into modules which are easily used by Requirejs and others
* Can download/upload Shopify Blogs, Pages and Products! Easily transfer them between stores! Even the metafields! And edit them locally in your favorite editor.

https://quickshot.readme.io/


## 1. Installation

```
npm install -g quickshot
```
## 2. Configuration

####Step 1. Create Config File

To setup the configuration json file, go to a new empty project directory.

Then run:
```
quickshot configure
```
or
```
qs configure
```

Then follow the configuration wizard prompts. The wizard will look like this:

```
? Main Menu (Use arrow keys)
❯ Configure targets
  Configure scss
  Configure babel
  Configure ignore file
  Configure concurrency
  Save configuration and exit
  ```
  Use the arrow keys and enter keys.

  ---
####Step 2. Setup Site Targets

Select **Configure Targets**.

Then **Create target**.

**Name** the target. e.g. Colette AUS.

Input the **API key** from the store. To find this, go to the Target Store's Shopify **Admin page**. Go **Apps > View Private Apps**. Then **Generate API Credentials**. Set all access to **Read and Write access** or **read access**. Then save. Input API Key.

Input **API password**.

Input **Store URL**.

Select a **Theme** to target. Either to download from or to upload to.

Success! Target Created!

To complete the wizard go to **Done managing targets**.


##3. Download Store Data

For each of the following, you will be asked which target you want to download from.

####Blogs

```
qs blogs download
```


####Pages

```
qs pages download
```

####Products

```
qs products download
```

####Theme

```
qs theme download
```

##4. Upload Store Data
For each of the following, you will be asked which target you want to upload to.

####Blogs

```
qs blogs upload
```


####Pages

```
qs pages upload
```

####Products

```
qs products upload
```

####Theme

```
qs theme upload
```
