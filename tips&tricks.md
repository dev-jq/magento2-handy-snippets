## Source maps in .css files for faster developing styles (compilcation process will take longer and output file will be larger!
in file:
`in file: vendor/magento/framework/Css/PreProcessor/Adapter/Less/Processor.php`

in line 71 (before: 'relativeUrls' => false) add this code:
`'sourceMap' => true,`
