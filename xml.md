## Attributes in xml
` cacheable="false" // or "true" `
` remove="true" // or "false" `
` display="true" // or "false" `

## ESI Block
Only when full page cache application is set to Varnish, ESI blocks are actual. ESI block is fetched by separate Varnish request, cached and invalidated independently from the page.

### You should use the ESI block in the following situations:
- The block is considered to be invalidated more frequently than pages where this block is rendered.
- The block is considered to be invalidated less frequently than pages where this block is rendered.

```
<block class="MyBlock\Class" ttl="3600"/>
```

## Custom block with template
```
<block class="Magento\Framework\View\Element\Template" name="my_block" template="Vendor_Module::my-template.phtml" /> ( after="-" or before="-" )
<block class="Magento\Framework\View\Element\Template" name="footer_logo_brands" template="Magento_Theme::html/brand-logos.phtml" after="footer_links"/> 
```

## Block with configuration condition
```
<block class="Magento\Newsletter\Block\Subscribe" name="form.subscribe" as="subscribe" before="-" template="Magento_Newsletter::subscribe.phtml" ifconfig="newsletter/general/active"/>
```

## Block inside container
```
<container name="some.block.wrapper" htmlTag="div" htmlClass="container">
      // block here
</container>
```

## Call static block from XML
```
<referenceContainer name="footer-container">
            <block class="Magento\Cms\Block\Block" name="promo" before="-">
                <arguments>
                    <argument name="block_id" xsi:type="string">promo</argument>
                </arguments>
            </block>
</referenceContainer>
```

## Two ways set template in xml
1)
```
<referenceBlock name="page.main.title" template="Vendor_Module::path/to/template.phtml"/>`
```
2)
```
<referenceBlock name="page.main.title">
	<arguments>
		<argument name="template" xsi:type="string">Vendor_Module::path/to/template.phtml</argument>
	</arguments>
</referenceBlock>
```

## Set template layout in xml (e.g. "2columns-left" in catalog_category_view.xml)
```
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="2columns-left" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        ...
    </body>
</page>
```

## Add custom link to top.links (customer dropdown)
```
<referenceBlock name="top.links">
    <block class="Magento\Framework\View\Element\Html\Link" name="acount-create-link">
        <arguments>
            <argument name="label" xsi:type="string" translate="true">Create an Account</argument>
            <argument name="path" xsi:type="string">customer/account/create</argument>
            <argument name="sortOrder" xsi:type="number">100</argument>
        </arguments>
    </block>
</referenceBlock>
```

## Include static resources (JavaScript, CSS, fonts)
```
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
  <head>
    <!-- Add local styles resources -->
    <css src="css/my-styles.css" />
    <css src="<Namespace>_<Module>::css/custom-styles.css" />

    <!-- The following two ways to add local JavaScript files are equal -->
    <script src="Magento_Catalog::js/sample1.js" />
    <script src="Magento_Catalog/js/sample1.js" />

    <!-- Magento support async or defer attribute in script tag -->
    <script async="" src="Magento_Catalog::js/sample1.js" />
    <script defer="" src="Magento_Catalog::js/sample1.js" />

    <link src="js/sample.js" />
    <link src="sample.js" />

    <!-- Add external resources -->
    <css src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap-theme.min.css" src_type="url" />
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js" src_type="url" />
    <link rel="stylesheet" type="text/css" src="http://fonts.googleapis.com/css?family=Montserrat" src_type="url" />
  </head>
</page>
```

## Remove static resources (JavaScript, CSS, fonts)
```
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
   <head>
    <!-- Remove local styles resources -->
    <remove src="css/styles-m.css" />
    <remove src="<Namespace>_<ModuleName>::css/styles.css" />

    <!-- Remove js resources -->
    <remove src="my-js.js" />
    <remove src="Magento_Catalog::js/sample1.js" />

    <!-- Remove external resources -->
    <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap-theme.min.css" />
    <remove src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/js/bootstrap.min.js" />
    <remove src="http://fonts.googleapis.com/css?family=Montserrat" />
   </head>
</page>
```

## Add meta tags to the head block
```
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
   <head>
    <!-- This will create a tag like '<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">' -->
    <meta name="x_ua_compatible" content="IE=edge,chrome=1"/>
    <!-- This will create a tag like '<meta property="og:type" content="article"/>'' -->
    <meta name="og:type" content="article"/>
    <!-- This will create a tag like '<meta charset="UTF-8">' -->
    <meta name="charset" content="UTF-8"/>
    <!-- This will create a tag like '<meta http-equiv="Content-Type" content="content-type-value"/>' -->
    <meta name="content_type" content="content-type-value"/>
    <!-- This tag will not render (see \Magento\Framework\View\Page\Config\Renderer for details) -->
    <meta name="media_type" content="any-value"/>
    <!-- This will create a tag like '<meta name="my_custom_type" content="my_custom_value"/>' -->
    <meta name="my_custom_type" content="my_custom_value"/>
   </head>
</page>
```

## Set body attributes
```
<body>
     <attribute name="class" value="my-new-body-class"/>
</body>
```

## Set custom page title
```
<referenceBlock name="page.main.title">
     <action method="setPageTitle">
          <argument translate="true" name="title" xsi:type="string">My title</argument>
     </action>
</referenceBlock>
```
