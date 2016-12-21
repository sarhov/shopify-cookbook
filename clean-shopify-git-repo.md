When you run themedownload, sometimes you might notice some “orphan files” being pulled down from your Shopify theme - files that used to be in your repository and were renamed or deleted, but still got uploaded to the version of the theme on the Shopify servers. A nice one-line command to clean those files from the server (after you’ve run  ) is:

```
theme download
bash $ git clean -n | sed 's/Would remove //' |
xargs theme remove
git clean
```

This uses   to get a list of files that aren’t in version control, and passes them on to the theme remove command to clean them up from the server. This command won’t remove the files locally, so you don’t need to worry about accidentally losing work.
