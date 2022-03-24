# Useful Magento 2 CLI commands

**Prepare The Cron in Crontab:**

```
php bin/magento cron:install
```

**Check The Module Status:**

```
php bin/magento module:status
```

**Disable Module:**

```
php bin/magento module:disable VENDOR_MODULENAME
```

**Enable Module:**

```
php bin/magento module:enable VENDOR_MODULENAME
```

**Indexer ( Reindex | Reset ):**

```
php -d memory_limit=2048M bin/magento indexer:reindex
```

**Setup Upgrade:**

```
php -d memory_limit=2048M bin/magento setup:upgrade
```

**Setup Compile:**

```
php -d memory_limit=2048M bin/magento setup:di:compile
```

**Static Content Deploy:**

```
php -d memory_limit=2048M bin/magento setup:static-content:deploy
```

**Catalog Images Resize:**

```
php bin/magento catalog:image:resize
```

**Deploy Mode Functions:**

```
php bin/magento deploy:mode:show
```

```
php bin/magento deploy:mode:set production ( default | production | developer )
```

**CSS and JS config for development**

```
php bin/magento config:set dev/js/enable_js_bundling 0
php bin/magento config:set dev/js/merge_files 0
php bin/magento config:set dev/js/enable_js_bundling 0
php bin/magento config:set dev/js/minify_files 0
php bin/magento config:set dev/css/merge_css_files 0
php bin/magento config:set dev/css/minify_files 0
```

**Cache Operations:**

```
php bin/magento cache:status
php bin/magento c:f ( cache:flush }
php bin/magento c:c ( cache:clean }
php -d memory_limit=2048M bin/magento cache:flush
php -d memory_limit=2048M bin/magento cache:clean
php bin/magento cache:disable full_page layout block_html translate
```
