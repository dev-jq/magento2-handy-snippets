# Useful Magento 2 CLI commands

**Deploy Mode Functions:**

```
php bin/magento deploy:mode:show
php bin/magento deploy:mode:set developer ( default | production | developer )
php bin/magento deploy:mode:set production --skip-compilation

php bin/magento maintenance:disable
php bin/magento maintenance:enable
```

**CSS and JS config for development**

```
php bin/magento config:set dev/js/enable_js_bundling 0
php bin/magento config:set dev/js/merge_files 0
php bin/magento config:set dev/js/enable_js_bundling 0
php bin/magento config:set dev/js/minify_files 0
php bin/magento config:set dev/css/merge_css_files 0
php bin/magento config:set dev/css/minify_files 0

php bin/magento config:set --scope="stores" --scope-code="default" dev/js/minify_files 0
```

**Cache Operations:**

```
php bin/magento cache:status
php bin/magento c:f ( cache:flush }
php bin/magento c:c ( cache:clean }
php bin/magento cache:disable full_page layout block_html translate
```

**Module oprations (check current status / disable module / enable module):**

```
php bin/magento module:status
php bin/magento module:disable VENDOR_MODULENAME
php bin/magento module:enable VENDOR_MODULENAME
```

**Setup Upgrade / Setup Compile / Static Content Deploy:**

```
php -d memory_limit=2048M bin/magento setup:upgrade
php -d memory_limit=2048M bin/magento setup:di:compile
php -d memory_limit=2048M bin/magento setup:static-content:deploy
php bin/magento setup:static-content:deploy pl_PL -f
php bin/magento setup:static-content:deploy pl_PL --theme Vendor/theme --no-html-minify -f
php bin/magento setup:static-content:deploy pl_PL en_US en_GB --jobs 20

```

**Setup config:**
```
php bin/magento setup:store-config:set --base-url="http://project.dev/"
php bin/magento setup:store-config:set --base-url-secure="http://project.dev/"
```

**Indexer ( Reindex | Reset ):**

```
php -d memory_limit=2048M bin/magento indexer:reindex
```

**Catalog Images Resize:**

```
php bin/magento catalog:image:resize
```
