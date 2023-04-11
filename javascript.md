## :point_right: Explanation of JS files
```
jquery: The jQuery library is used in Magento for manipulating HTML elements and handling events.

jquery/ui: This module contains jQuery UI-based user interface components such as dialog boxes, trees, calendars, etc.

mage/adminhtml/wysiwyg/widget: This module is responsible for handling the WYSIWYG editor in the Magento admin panel.

mage/adminhtml/events: This module contains the JavaScript code used in the Magento admin panel.

mage/adminhtml/notification: This module is responsible for displaying notifications in the Magento admin panel.

mage/adminhtml/grid: This module is responsible for handling the data table in the Magento admin panel.

mage/adminhtml/browser: This module is responsible for handling the file browser in the Magento admin panel.

mage/calendar: This module is responsible for handling the calendar in Magento.

mage/captcha: This module is responsible for handling CAPTCHA verification in Magento.

mage/checkout: This module is responsible for handling the checkout process.

mage/cookies: This module is responsible for handling cookies in Magento.

mage/dropdown: This module is responsible for handling dropdown menus in Magento.

mage/gallery: This module contains functions for handling image galleries in Magento.

mage/loader: This module is responsible for loading JavaScript and CSS files.

mage/mage: This module contains functions and tools used in Magento.

mage/menu: This module is responsible for handling the navigation menu in Magento.

mage/requirejs/text: This module contains tools for loading text files in Magento.

mage/smart-keyboard-handler: This module is responsible for handling the keyboard in Magento.

mage/translate-inline: This module is responsible for live text translation in Magento.

mage/translate: This module is responsible for text translation in Magento.

mage/validation/validation: This module contains form validators in Magento.

mage/sticky: This module is responsible for allowing elements to remain in place while scrolling in Magento.

mage/collapsible: This module is responsible for handling collapsible elements in Magento.

mage/ie-class-fixer: This module is responsible for fixing bugs in Internet Explorer browsers.
```

## the most commonly used configuration options in RequireJS
```
paths: The paths configuration option allows developers to specify the locations of the JavaScript files that contain the modules they want to load. For example, if a module called myModule is located in the js directory of the application, the path can be defined as paths: { myModule: 'js/myModule' }. This option is useful when the files are not located in the same directory as the application.

shim: The shim configuration option is used to define dependencies between non-AMD modules. For example, if a module called jquery is not written in the AMD format but is required by an AMD module, it can be defined as shim: { jquery: { exports: '$' } }. This tells RequireJS that jquery should be treated as an AMD module and that the $ symbol should be used as its export value.

map: The map configuration option allows developers to create aliases for modules. For example, if a module called myModule depends on a module called otherModule, and otherModule has been aliased as aliasModule, the mapping can be defined as map: { 'myModule': { 'otherModule': 'aliasModule' } }. This allows developers to use more descriptive names for modules without affecting their underlying code.

config: The config configuration option is used to pass configuration data to modules. For example, if a module called myModule requires a configuration object, the configuration can be defined as config: { 'myModule': { 'apiKey': '12345' } }. This configuration object can then be accessed by myModule using the requirejs.config() method.
```

## :point_right: How to modify/extend component with mixin?
Create file `app/code/Module/Vendor/view/frontend/requirejs-config.js`
```
var config = {
    config: {
        mixins: {
            'Magento_Checkout/js/view/minicart': {
                'Module_Vendor/js/minicart-mixin': true
            }
        }
    }
};
```

Then, create `app/code/Module/Vendor/view/frontend/web/js/minicart-mixin.js`
```
define([
    /* [...] */
], function() {
    'use strict';

    return function(target) {
        return target.extend({

            getCartItems: function() {
                console.log('Mixin Component -- Before getCartItems');

                var items = this._super();

                console.log('Mixin Component -- After getCartItems');
                console.log(items);
            }

        });
    };
});
```

## :point_right: How to modify/extend widget with mixin?
Create file `app/code/Module/Vendor/view/frontend/requirejs-config.js`
```
var config = {
    config: {
        mixins: {
            catalogAddToCart: {
                'Magento_Catalog/js/catalog-add-to-cart-theme-mixin': true // Mixin example
            }
        }
    }
};
```

Then, create `app/code/Module/Vendor/view/frontend/web/js/catalog-add-to-cart-theme-mixin.js`
```
define([
    'jquery'
], function($) {
    'use strict';

    return function(target) {
        $.widget('jq.catalogAddToCart', target, {

            ajaxSubmit: function(form) {
                console.log('Mixin Widget -- Before ajaxSubmit');

                this._super(form);

                console.log('Mixin Widget -- After ajaxSubmit');
            }

        });

        return $.jq.catalogAddToCart;
    };
});
```
