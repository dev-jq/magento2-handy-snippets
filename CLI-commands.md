# Useful Magento 2 CLI commands

**Deploy Mode Functions:**
```
php bin/magento deploy:mode:show
php bin/magento deploy:mode:set developer ( default | production | developer )
php bin/magento deploy:mode:set production --skip-compilation

php bin/magento maintenance:disable
php bin/magento maintenance:enable
php bin/magento maintenance:enable --ip=192.0.0.1 --ip=192.0.0.2 (for all clients except this IPs)
php bin/magento maintenance:enable --ip=none (to clear the list of IPs)
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
php bin/magento module:uninstall VENDOR_MODULENAME (if installed by Composer)
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
php bin/magento setup:store-config:set --base-url-secure="https://project.dev/"

php bin/magento config:set admin/security/session_lifetime 604800 ( 86400 = 1 day / 604800 = 7 days / 31536000 = 1 year / etc )
php bin/magento config:set admin/security/password_is_forced 0
```

**Indexer ( Reindex | Reset ):**
```
php -d memory_limit=2048M bin/magento indexer:reindex
```

**Generate a translation package for a definite module**
```
php bin/magento i18n:collect-phrases -o app/code/Module/Vendor/i18n/pl_PL.csv app/code/Module/Vendor/
php bin/magento i18n:collect-phrases --output="app/design/frontend//Module/Vendor/i18n/pl_PL.csv" --magento (This option adds themes or modules to each line in the dictionary.)
```

**Catalog Images Resize:**
```
php bin/magento catalog:image:resize
```

**For admin**
```
php bin/magento admin:user:create
php bin/magento info:adminuri
php bin/magento admin:user:unlock USERNAME
```

**Get list of all available commands**
```
php bin/magento list
php bin/magento help
```
