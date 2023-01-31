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
$this->getUrl('', array('_direct'=>'hairproducts.html', '_query'=>'manufacturer=412'));
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

## Example operations on product attribute
```
<?php if($_product->getTypeId() == \Magento\ConfigurableProduct\Model\Product\Type\Configurable::TYPE_CODE): ?>
        <?php
        $deliveryTime = $_product->getResource()->getAttribute('delivery_time');
        $minDeliveryTime = $deliveryTime->getFrontend()->getValue($_product);
        ?>
        <div class="delivery-time">
            <?php echo __('Delivery time: %1', $minDeliveryTime); ?>
        </div>
<?php endif; ?>
```
``
$product->getAttributeText('color'); - value as 'text' label
$product->getResource()->getAttribute('color')->getFrontend()->getValue($product); - value as 'text' label
$product->getData('color'); - value as 'id attribute number'
``

## Execute JavaScript code after swatches are displayed in category view
```
<script>
    require(['jquery', 'Magento_Swatches/js/swatch-renderer'], function ($, swatch) {
        $(document).on('swatch.initialized', function() {
            // Here make some layout changes
        });
    });
</script>  
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

## Media Queries in JavaScript
```
<script type="text/javascript">
        require(['jquery', 'matchMedia'], function ($, mediaCheck) {
            mediaCheck({
                media: '(min-width: 768px)',
                // Switch to Desktop Version
                entry: function () {
                   alert('desktop');
                },
                // Switch to Mobile Version
                exit: function () {
                    alert('mobile');
                }
            });
        });
    </script>
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

## script initialization
standard
```
<div class="swiper-container header-slider" data-mage-init='{"Swissup_Swiper/js/swiper": {"loop":true,"centeredSlides":true,"autoplay": {"delay": 10000}, "navigation":{"nextEl":".swiper-button-next","prevEl":".swiper-button-prev"}}}'>
    <div class="swiper-wrapper">
        <div class="swiper-slide">1</div>
        <div class="swiper-slide">2</div>
        <div class="swiper-slide">3</div>
   </div>
</div>
```
or better:
```
<script type="text/lazy">
    require(['jquery', 'Swissup_Swiper/js/swiper'], function ($, swiper) {
        $(function() {
            $('.header-slider').each(function(index, element) {
                swiper({"loop":true,"centeredSlides":true,"autoplay": {"delay": 10000}, "navigation":{"nextEl":".swiper-button-next","prevEl":".swiper-button-prev"}}, element);
             });
        });
    });
</script>
```

