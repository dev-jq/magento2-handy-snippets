## Attributes in xml
` cacheable="false" // or "true" `
` remove="true" // or "false" `
` display="true" // or "false" `

## Custom block with template
```
<block name="my_block" class="Magento/Framework/View/Element/Template" template="Vendor_Module::my-template.phtml" />
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

## Set template layout in xml (e.g. catalog_category_view.xml)
```
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="2columns-left" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        ...
    </body>
</page>
```
