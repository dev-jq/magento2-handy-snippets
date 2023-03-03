## Custom Variable
`{{CustomVar code='my_custom_variable'}}`

## Store URL
`{{store url='customer/account'}}` - with slash at the end

`{{store direct_url='contact-us'}}` - without slash at the end

## Media URL
`{{media url='wysiwyg/your-image.jpg'}}`
`{{view url='images/logo.svg'}}`

## Block ID
`{{block class="Magento\Cms\Block\Block" block_id="block_identifier"}}`

`{{block class="Magento\Framework\View\Element\Template" name="custom.template.block" template="Magento_Cms::custom.phtml"}}`

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

```
– For registration:
{{var customer}}

{{var customer.ID}}

{{var customer.email}}

{{var customer.firstname}}

{{var customer.lastname}}

{{var customer.name}}

{{var customer.password}}

{{var customer.created_in}} Store Name

{{var customer.dob}} Date of Birth

{{var customer.password_hash}}

{{var customer.prefix}}

{{var customer.middlename}} Initial

{{var customer.suffix}}

{{var customer.group_id}}

{{var customer.taxvat}}

{{var customer.store.name}}

{{var customer.store.group.name}}

– To subscribe/unsubscribe newsletter:

{{var subscriber.getConfirmationLink()}}

{{var subscriber.getUnsubscriptionLink()}}

{{var subscriber.email}}

– Send to a friend:

{{var product_image}}

{{var name}} Recipient’s Name

{{var email}} Recipient’s Email

{{var product_name}} Product Name

{{var product_url}} Product Url

{{var message}} Message Text

{{var sender_name}} Sender’s Name

{{var sender_email}} Sender’s Email

{{var product_image}} Product Image

– Depend Condition

{{depend order.getIsNotVirtual()}}

{{/depend}}

{{depend salable}}

{{/depend}}

– If Condition

{{if order.getIsNotVirtual()}}

{{else}}

{{/if}}

(else is optional)


– New order : Shipping Address

{{var order.getShippingAddress().format(‘html’)}}

Items of the shipping address :

{{var order.getShippingAddress().getName()}} Get the first and last name

{{var order.getShippingAddress().getPrefix()}}

{{var order.getShippingAddress().getFirstName()}}

{{var order.getShippingAddress().getMiddleName()}}

{{var order.getShippingAddress().getLastName()}}

{{var order.getShippingAddress().getSuffix()}}

{{var order.getShippingAddress().getStreet1()}}

{{var order.getShippingAddress().getStreet2()}}

{{var order.getShippingAddress().getCity()}}

{{var order.getShippingAddress().getRegion()}}

{{var order.getShippingAddress().getPostcode()}}

{{var order.getShippingAddress().getCountry()}} Get the country’s ID

{{var order.getShippingAddress().getCountryModel().getName()}} Get the country’s full name

{{var order.getShippingAddress().getRegion()}}

{{var order.getShippingAddress().getTelephone()}}

– Other

{{var addAllLink}}

{{var alertGrid}}

{{var billingAddress.format(‘html’)}}

{{var checkoutType}}

{{var comment}}

{{var creditmemo.id}}

{{var creditmemo.increment_id}}

{{var data.comment}}

{{var data.email}}

{{var data.name}}

{{var data.telephone}}

{{var dateAndTime}}

{{var invoice.id}}

{{var invoice.increment_id}}

{{var invoice.created_at}}

{{var items}}

{{var items_html}}

{{var message}}

{{var name}}

{{var order.customer_email}}

{{var order.getBillingAddress().format(‘html’)}}

{{var order.getBillingAddress().getName()}}

{{var order.getCreatedAtFormated(‘long’)}}

{{var order.getCustomerName()}}

{{var order.getCustomerFirstname()}}

{{var order.getCustomerLastname()}}

{{var order.getEmailCustomerNote()}} Currently unknwon how to test this variable for being set/empty

{{var order.getShippingDescription()}}

{{var order.getStatusLabel()}}

{{var order.getStoreGroupName()}}

{{var order.id}}

{{var order.increment_id}}

{{var password}}

{{var payment_html}}

{{var paymentMethod}}

{{var product_name}}

{{var product_url}}

{{var reason}} Reason for payment failure

{{var shipment.increment_id}}

{{var shippingAddress.format(‘html’)}}

{{var shippingMethod}}

{{var total}}

{{var user.name}}

{{var viewOnSiteLink}}

{{var warnings}}

{{var billing.name}}
```

# See more: https://docs.magento.com/user-guide/marketing/variables-reference.html
