# Commomn examples
```
<div data-bind="mageInit: {'collapsible':{'openedState': '_active', 'active': true}}">
...
</div>
```
```
<textarea class="input-text" data-bind="attr:{placeholder: $t('Enter your comment...')} "></textarea>
```
```
<a href="#" data-bind="attr:{href: product_url}, html: name" class="product-item-link"></a>
```
```
<span data-bind="i18n: 'Forgot Your Password?'"></span>
```
```
<div class="minicart">
  <span class="text"><!-- ko i18n: 'My Cart' --><!-- /ko --></span>
  <span class="qty empty"
        data-bind="css: { empty: !!getCartParam('summary_count') == false },
                         attr: { title: $t('Items in Cart') }">
        <!-- ko text: getCartParam('summary_count') --><!-- /ko -->
   </span>
</dv>
```


# Binding
## if
```
<!-- ko if: isVisible-->
...
<!-- /ko -->
```
```
<div data-bind="if: isVisible"></div>
```
```
<!-- ko if: getCartParam('summary_count') -->
```

## ifnot
```
<!-- ko ifnot: isVisible-->
...
<!-- /ko -->
```
```
<div data-bind="ifnot: isVisible"></div>
```
```
<!-- ko ifnot: getCartParam('summary_count') -->
```

## text
```
<!-- ko text: 'Some text' --><!-- /ko -->
```
```
<div data-bind="text: 'Some text'"></div>
```

## i18n
```
<!-- ko i18n: 'Sign In' --><!-- /ko -->
```
```
<span data-bind="i18n: 'Sign In'"></span>
```

## foreach
```
<!-- ko foreach: elements -->
...
<!-- /ko -->
```

## component
```
<!-- ko component: 'componentName' --> <!-- /ko -->
```
```
<div data-bind="component: 'componentName'"> </div>
```

## css
```
<div data-bind="css: {_visible: isVisible}"> </div>
```

## attr
```
<div data-bind="attr: {title: title}"> </div>
```

## style
```
<div data-bind="style: {color: redColor}"> </div>
```

## html
```
<div data-bind="html: '<span/>'"> </div>
```

## click
```
<div data-bind="click: onClick"> </div>
```

## event
```
<div data-bind="event: {mouseover: showEl}"> </div>
```

## template
```
<div data-bind="event: {mouseover: showEl}"> </div>
```

## submit
```
<form data-bind="submit: onSubmit"> </form>
```

## options
```
<select data-bind="options: optionsList"> </select>
```

## selectedOptions
```
<select data-bind="options: optionsList, selectedOptions: value"> </select>
```

## optionsText
```
<select data-bind="options: optionsList, optionsText: 'label'"> </select>
```

## optionsValue
```
<select data-bind="options: optionsList, optionsValue: 'value'"> </select>
```

## enable
```
<input data-bind="enable: isEnabled"/>
```

## disable
```
<input data-bind="enable: isEnabled"/>
```

## hasfocus
```
<input data-bind="hasFocus: onFocus"/>
```

## textInput
```
<input data-bind="textInput: value"/>
```

## value
```
<input data-bind="value: value"/>
```

## checked
```
<input type="checkbox" data-bind="checked: isChecked"/>
```
```
<input type="radio" data-bind="value: value, checked: isSelected" />
```

## checkedValue
```
<input type="checkbox" data-bind="checkedValue: $data, checked: isChecked"/>
```

## with
```
<!-- ko with: element --><!-- /ko -->
```
```
<div data-bind="with: element"></div>
```
