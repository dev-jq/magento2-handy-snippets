## Generate source maps in .css files for faster developing styles (compilcation process will take longer and output file will be larger! Only for development)
in file:
```
vendor/magento/framework/Css/PreProcessor/Adapter/Less/Processor.php
```

in line 71 (before: 'relativeUrls' => false) add this code:
`'sourceMap' => true,`

## Find cacheable="false" blocks in templates

```
cd app/design/frontend/ && grep --recursive -l 'cacheable="false"' * && cd ../../..;
cd app/code && grep --recursive -l 'cacheable="false"' * && cd ../..;
cd vendor && grep --recursive -l 'cacheable="false"' * && cd ..;
```

## Set aAdmin session lifetime
```
php bin/magento config:set admin/security/session_lifetime 31536000
```
