## :point_right: How to replace/extend a javascript component with mixin?
Create file `app/code/Module/Vendor/view/frontend/requirejs-config.js`
```
var config = {
    config: {
        mixins: {
            'Magento_Swatches/js/swatch-renderer': {
                'Module_Vendor/js/swatch-renderer-mixin': true
            }
        }
    }
};
```

Then, create `app/code/Module/Vendor/view/frontend/web/js/swatch-renderer-mixin.js`
```
define(['jquery'], function ($) {
    'use strict';
    return function (SwatchRenderer) {
        $.widget('mage.SwatchRenderer', SwatchRenderer, {
            _init: function () {
                console.log('Custom Swatch Renderer init function call successfully');
                return this._super();
            }
        });
        return $.mage.SwatchRenderer;
    };
});
```
