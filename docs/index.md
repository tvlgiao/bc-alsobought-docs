# User Guide for BigCommerce Frequently Bought Together
-- Developed by [PapaThemes](https://papathemes.com/)


## Install on your BigCommerce theme

1. Extract [THEME_MOD.zip](https://papathemes.com/content/alsoboughtaddon/THEME_MOD.zip) and copy all files in `templates/components/papathemes/also-bought/` to your theme with the corresponding path `templates/components/papathemes/also-bought/`.


2. Edit file `assets/js/app.js` of your theme, find the line:

```js
const customClasses = {};
```

Insert the code below under it:

```js
// PapaThemes AlsoBought MOD
if (!window.jQueryTheme) {
    window.jQueryTheme = $;
}
```


3. Edit file `assets/js/theme/common/product-details.js`, find the line:

```js
this.previewModal = modalFactory('#previewModal')[0];
```

Insert the code below under it:

```js
// PapaThemes AlsoBought MOD
$('body').trigger('product-details-init', this);
```


4. Edit file `lang/en.json`, At the end of file, before the last `}`, insert the code below:

```json
    ,
    "also_bought": {
        "heading": "Frequently bought together:",
        "add_all": "Select all",
        "add_selected_to_cart": "Add selected to cart"
    }
```


Add the code below to **Storefront** > **Script Manager**, **Location** = `Footer`, **Pages** = `All Storefront Pages`:

```html
<script>
    window.jQueryAlsoBought = window.jQueryTheme || window.jQuery;
    // Optional configuration to display Also Bought at different position:
    // window.AlsoBoughtOptions = {
    //     getScopeWithoutAlsoBought: function($scope) {
    //         return $scope.children().not('[data-also-bought]');
    //     },
    //     renderAlsoBought: function(alsoBought) {
    //         alsoBought.$alsoBoughtEl.appendTo(alsoBought.parentProductDetails.$scope);
    //     }
    // };
</script>
<script src="//papathemes.com/content/alsoboughtaddon/alsobought.YOURDOMAIN.js" async></script>
```

**Note:** replace `YOURDOMAIN` by your own domain, example:

```html
<script>window.jQueryAlsoBought = window.jQueryTheme || window.jQuery;</script>
<script src="//papathemes.com/content/alsoboughtaddon/alsobought.fivebrotherworkwear.mybigcommerce.com.js" async></script>

```


## Assign frequently bought products to a product

Edit your product, add some custom field with name `__alsobought` and value is the frequently product ID. You can add many custom field `__alsobought` as you want.

Example:

* `__alsobought` : `389`
* `__alsobought` : `388`
* `__alsobought` : `390`


