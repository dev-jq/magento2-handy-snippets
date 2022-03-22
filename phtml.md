## Translatable text
```
<?= __('String to translate'); ?>
```
## Call method from module helper
```
<?php $helper = $this->helper('Vendor\Module\Helper\Data'); ?>
<?php $helper->callMethodName(); ?>
```

## Useful block functions
```
$block->getViewFileUrl();
$block->getUrl('checkout/cart/index');
$block->getBaseUrl();
$block->getMediaDirectory();
$block->getChildBlock('block.name');
$block->getChildHtml('block.name');
$block->getChildChildHtml('block.name');
$block->getBlockHtml('block.name');
$block->escapeHtml();
$block->escapeUrl();

$block->escapeHtml('value', $allowedTags);
$block->escapeHtmlAttr('value', $escapeSingleQuote);
$block->escapeJs('value');
$block->escapeUrl($url);
```

## Can be used to get the list of handles while debugging
```
$this->getLayout()->getUpdate()->getHandles();
```

## Get backend config option enebled/disabled
```
<?php $config = $block->getLayout()->createBlock(\Magento\Config\Block\System\Config\Form::class);?>
<?php if($config->getConfigValue('dev/translate_inline/active')): ?>
  // do something
<?php endif; ?>
```
