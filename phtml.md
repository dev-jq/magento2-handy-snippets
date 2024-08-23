## Translatable text
```
<?= __('String to translate'); ?>
```

## Translatable text with html and variables
```
<?= $block->escapeHtml(__('You will receive a <strong>10% discount on your first purchase</strong> and information about promotions and new products.'), ['strong']) ?>
<?= $block->escapeHtml(__('I agree with the <a href="%1">Privacy Policy</a> and the principles of how we <a href="%2">process data</a>.', $block->getUrl('privacy-policy'), $block->getUrl('process-cookie')), ['a']) ?> 
```

## Useful block functions
```
$block->getViewFileUrl('images/loader-1.gif'); - from web/images directory
$block->getViewFileUrl('Magento_Catalog::images/filename.jpg'); - from e.g Magento_Catalog/web/images directory

$block->getUrl('checkout/cart/index');
$block->getUrl('', array('_direct'=>'hairproducts.html'));
$block->getUrl('', array('_direct'=>'hairproducts.html', '_query'=>'manufacturer=412'));

$block->getBaseUrl();
$block->getMediaDirectory();
$block->getChildBlock('block.name');
$block->getChildHtml('block.name');
$block->getChildChildHtml('block.name');
$block->getBlockHtml('block.name');
$block->stripTags(); // removes HTML tags

$block->escapeHtml();
$block->escapeUrl();
$block->escapeHtml('value', $allowedTags);
$block->escapeHtmlAttr('value', $escapeSingleQuote);
$block->escapeJs('value');
$block->escapeUrl($url);
```
## Escaping
```
/* @noEscape */
/* @escapeNotVerified */

$block->escapeHtml();
$block->escapeHtml('value', $allowedTags);
$block->escapeUrl();
$block->escapeUrl($url);
$block->escapeHtmlAttr('value', $escapeSingleQuote);
$block->escapeJs('value');

$escaper->...
```

## Call static block ID in .phtml  template (if exist/enabled/not empty)
```
<?php if($this->getLayout()->createBlock('Magento\Cms\Block\Block')->setBlockId('BLOCK_ID')->toHtml() != ''): ?>
    <div class="static-block">
        <?php echo $this->getLayout()->createBlock('Magento\Cms\Block\Block')->setBlockId('BLOCK_ID')->toHtml(); ?>
    </div>
<?php endif; ?>
```

## Call widget in .phtml template
```
<?= $this->getLayout()->createBlock("Magento\Catalog\Block\Product\Widget\NewWidget")
            ->setDisplayType("all_products")
            ->setShowPager(1)
            ->setProductsPerPage(5)
            ->setProductsCount(10)
            ->setPageVarName("pwkvbl")
            ->setTemplate("product/widget/new/content/new_grid.phtml")
            ->toHtml(); ?>
```

## Call method from module helper
```
<?php $helper = $this->helper(Vendor\Module\Helper\Data::class); ?>
<?php $helper->callMethodName(); ?>
```

## Get VAR value from /etc/view.xml in phtml
```
<?= $block->getVar("gallery/width", 'Magento_Catalog'); ?>
<?= $block->getVar("breakpoints/mobile/conditions/max-width", 'Magento_Catalog'); ?>
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
```
$product->getAttributeText('color'); - value as 'text' label
$product->getResource()->getAttribute('color')->getFrontend()->getValue($product); - value as 'text' label
$product->getData('color'); - value as 'id attribute number'
```

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

## Script initialization
:information_source: ``<script type="text/lazy">...</script>`` is my custom, optimized JS tag call after first user interaction (click, scroll, etc.)

### Example 1
#### standard way
```
<div class="swiper-container header-slider" data-mage-init='{"Swissup_Swiper/js/swiper": {"loop":true,"centeredSlides":true,"autoplay": {"delay": 10000}, "navigation":{"nextEl":".swiper-button-next","prevEl":".swiper-button-prev"}}}'>
    <div class="swiper-wrapper">
        <div class="swiper-slide">1</div>
        <div class="swiper-slide">2</div>
        <div class="swiper-slide">3</div>
   </div>
</div>
```
#### or optimized way:
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

### Example 2
#### standard way
```
<script type="text/x-magento-init">
  {
    "*": {
      "Edrone_Magento2module/js/edroneDataTransfer": {}
    }
 }
</script>
```
#### or optimized way:
```
<script type="text/lazy">
   require(['jquery', 'Edrone_Magento2module/js/edroneDataTransfer'], function ($, edroneDataTransfer) {
        $(function () {
            edroneDataTransfer({});
        });
   })
</script>
```
