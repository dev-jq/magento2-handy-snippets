## Translatable text
```
<?= __('String to translate'); ?>
```

## Can be used to get the list of handles while debugging
```
$this->getLayout()->getUpdate()->getHandles()
```
## Useful block functions
```
$block->getUrl('checkout/cart/index')
$block->getBaseUrl()
$block->getMediaDirectory()
$block->getChildBlock('block.name')
$block->getChildHtml('block.name')
$block->getChildChildHtml('block.name')
$block->getBlockHtml('block.name')
$block->escapeHtml()
$block->escapeUrl()

$block->escapeHtml('value', $allowedTags);
$block->escapeHtmlAttr('value', $escapeSingleQuote);
$block->escapeJs('value');
$block->escapeUrl($url);
```
