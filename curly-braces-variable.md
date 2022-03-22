## Custom Variable
`{{CustomVar code='my_custom_variable'}}`

## Store URL
`{{store url='customer/account'}}` - with slash at the end
'{{store direct_url='contact-us'}}' - without slash at the end

## Media URL
`{{media url='wysiwyg/your-image.jpg'}}`
`{{skin url='images/loader-1.gif'}}`
`{{view url='images/logo.svg'}}`

## Block ID
`{{block class="Magento\Contact\Block\ContactForm" name="contactForm" template="Magento_Contact::form.phtml"}}`

`{{block type="catalog/product_list" category_id="22" template="catalog/product/list.phtml"}}`

## Widget
`{{widget type="catalog/product_widget_new" display_type="new_products" products_count="10" template="catalog/product/widget/new/content/new_grid.phtml"}}`

`{{widget type="catalog/product_widget_link" anchor_text="My Product Link" title="My Product Link" template="catalog/product/widgetlink/link_block.phtml" id_path="product/31"}}`

## Store Contact Information Variables 
Base Secure URL	`{{config path='web/secure/base_url'}}`

General Contact Email	`{{config path='trans_email/ident_general/email'}}`

## New Account Template Variables
Customer Account URL `{{var this.getUrl($store, ‘customer/account/’)}}`

Customer Email `{{var customer.email}}`

## New Order Template Variables
Order ID `{{var order.increment_id}}`

Payment Details `{{var payment_html|raw}}`

Shipping Description `{{var order.getShippingDescription()}}`

## Email Template Variables
Email Logo Image URL `{{var logo_url}}`

Email Logo Image Width `{{var logo_width}}`

# See more: https://docs.magento.com/user-guide/marketing/variables-reference.html
