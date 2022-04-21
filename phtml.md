## Translatable text
```
<?= __('String to translate'); ?>
```

## Call static block ID in template (if exist/enabled/not empty)
```
<?php if($this->getLayout()->createBlock('Magento\Cms\Block\Block')->setBlockId('BLOCK_ID')->toHtml() != ''): ?>
    <div class="static-block">
        <?php echo $this->getLayout()->createBlock('Magento\Cms\Block\Block')->setBlockId('BLOCK_ID')->toHtml(); ?>
    </div>
<?php endif; ?>
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
$block->stripTags(); // removes HTML tags

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

## 2 ways to call Fotorama gallery script

```
<script type="text/x-magento-init">
    {
        "[data-gallery-role=gallery-placeholder]": {
            "mage/gallery/gallery": {
                "mixins":["magnifier/magnify"],
                "magnifierOpts": <?= $block->getMagnifier() ?>,
                "data": <?= $block->getGalleryImagesJson() ?>,
                "options": <?= $block->getGalleryOptions()->getOptionsJson() ?>,
                "fullscreen": <?= $block->getGalleryOptions()->getFSOptionsJson() ?>,
                "breakpoints": <?= $block->getBreakpoints() ?>
            }
        }
    }
</script>
```
```
<script>
    require(['jquery', 'mage/gallery/gallery'], function ($, gallery) {
        $(function () {
            $('[data-gallery-role="gallery-placeholder"]').each(function(index, element) {
                gallery({
                    "mixins":["magnifier/magnify"],
                    "magnifierOpts": <?= $block->getMagnifier() ?>,
                    "data": <?= $block->getGalleryImagesJson() ?>,
                    "options": <?= $block->getGalleryOptions()->getOptionsJson() ?>,
                    "fullscreen": <?= $block->getGalleryOptions()->getFSOptionsJson() ?>,
                    "breakpoints": <?= $block->getBreakpoints() ?>
                }, element);
             });
        });
    });
</script>
```
