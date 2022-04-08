## :point_right:  Simple way to debug Knockout in browser console by 𝐫𝐞𝐪𝐮𝐢𝐫𝐞('𝐮𝐢𝐑𝐞𝐠𝐢𝐬𝐭𝐫𝐲').𝐠𝐞𝐭(𝐬𝐜𝐨𝐩𝐞)
![Debug Knockout in browser console](https://github.com/jq91/magento2-handy-snippets/blob/master/assets/debug-knockout.jpg)

## :point_right: How to use Luma icons (list with CSS code)
![Magento_Luma icons list](https://github.com/jq91/magento2-handy-snippets/blob/master/assets/luma-icons.png)

## :point_right:How to add other icons pack to Magento 2 (e.g. Bootstrap Icons, Material Icons)?
`Check this out:` https://github.com/GrimLink/magento2-icon-packs

## :point_right:How to create patch file?
https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/patches/apply.html
```
diff -u File.php File-new.php > File.patch
```

## :point_right: Generate source maps in .css files for faster developing styles (compilcation process will take longer and output file will be larger! Only for development)
in file:
```
vendor/magento/framework/Css/PreProcessor/Adapter/Less/Processor.php
```

in line 71 (before: 'relativeUrls' => false) add this code:
`'sourceMap' => true,`

## :point_right: Find cacheable="false" blocks in templates

```
cd app/design/frontend/ && grep --recursive -l 'cacheable="false"' * && cd ../../..;
cd app/code && grep --recursive -l 'cacheable="false"' * && cd ../..;
cd vendor && grep --recursive -l 'cacheable="false"' * && cd ..;
```

## :point_right: Dump Magento2 database (for development purpose) without all logs, sessions, admin users, orders, and customers
```
n98-magerun2.phar db:dump --strip="@development"
```

**TIP**: to install n98-magerun2 run below command in your Linux terminal:
```
wget https://files.magerun.net/n98-magerun2.phar
chmod +x ./n98-magerun2.phar
./n98-magerun2.phar --version
```

## :point_right: When you should run which commands in Magento 2?
### `php bin/magento setup:upgrade`
```
You should run this command only on following senarios:
- When you made changes in the Setup script(InstallData, InstallSchema,
- UpgradeData, UpgradeSchem)
- When you install a new module
- When you change setup_version in module.xml
- After upgrade Magento version
```

### `php bin/magento setup:di:compile`
```
If you made changes like add new dependency in __construct(), changes in di.xml, Add new controller…

If you are in developer mode you can simply delete changed files from /generated folder
```

### `php bin/magento setup:static-content:deploy`
```
You need to run this command only when you made changes in HTML, CSS, JS

If you are in developer mode and enabled symlinks in system you need not run this command. 
If disabled symlinks, need to delete particular changed files from pub/static folder.
```

### `php bin/magento cache:flush`
```
You need to run this command, if you made changes in:
- admin configuration
- layout xml
- ui component
- phtml or overrite html
- js in frontend theme
```

## :point_right: Overview list of caches in Magento 2
***Configuration***: After adapting configuration files, it is necessary to flush them including configuration and store specific settings

***Layouts***: After adapting layout files, it is necessary to flush them including the compiled page layout from all components

***Blocks HTML output***: After adapting the view layers, it is necessary to flush them including page fragments per block

***Collections Data***: By Magento, it can flush automatically database queries. However, Custom modules may write entries which make Magento can not clean by itself, in case, Magento can not clean so we need to clean the cache

***Reflection Data***: API interfaces reflection data will be flushed

***Database DDL operations***: it can be flush automatically by Magento, but 3rd party can plus more data, after making custom changes to the database schema, which can clean the cache

***EAV types and attributes***: The metadata regarding the entity attributes into the cache, in general, it should not flush the cache

***Integrations Configuration***: Caches the compiled integrations on your store. Clean after adding new or changing existing integrations

***Integrations API Configuration***: Compiled integration APIs configuration of the Store’s Integrations

***Page Cache***: This cache links the HTML pages so it is necessary to clean this type of cache regularly

***Translations***: After merging translations from all modules, the merger cache will be cleaned

***Web Services Configuration***: Caching the Web API Structure


