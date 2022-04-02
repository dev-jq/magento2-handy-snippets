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
