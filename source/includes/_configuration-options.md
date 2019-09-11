#Configuration options

Both Tipser Elements and Tipser SDK initialization functions accept configuration object as a second parameter. 


Tipser Elements example:

```javascript
const tipserElements = tipser.elements("59e86b79b8f3f60a94ecd26a", {primaryColor: "#222"});
```

Tipser SDK Example:

```javascript
const tipserSdk = TipserSDK("59e86b79b8f3f60a94ecd26a", {primaryColor: "#222"});
```

The example connects Tipser SDK and sets primary color to yellow.

All the available configuaration options are: 

```javascript
const configurationOptions = {
  primaryColor: "#222",
  env: "stage",
  lang: 'en',
  modalUi: {
    hideSearchIcon: true,
    hideFavouritesIcon: true,
    hideCartIcon: false,
    hideMoreIcon: true,
    hideSimilarProducts: false,
    useCustomCss: true
  },
  useDeepLinking: false,
  customLabels: {
    buy: 'custom button label'
  }
}
```
They will be described in the following sections.

***

## Primary Color

If you'd like to unify our design with your own color-theme, you can use our primary color configuration option to change the color of `buy` buttons in Product and indicator of items number in Cart. You only need to make sure to use the right hex color code.

```javascript
const tipserSdk = TipserSDK("59e86b79b8f3f60a94ecd26a", {primaryColor: "#5F9F9F"});
```

[![](primary-color.png)](/images/primary-color.png)

* If your primary color is bright, you may consider changing also the text color for elements like buttons via CSS overrides of element's specific class [(examples)](#customizing-tipser-elements-styles). 


***

## Environment

```javascript
const tipser = tipser.elements("59e86b79b8f3f60a94ecd26a", {env: "stage"});
```

By default, Tipser Elements and SDK connect to production Tipser environment. Yet if testing environment is preferred (e.g. in order to do test purchase), then it can be customized with env parameter in Tipser options, which accept the following values:

**prod** or production

**stage** or staging

**dev** or development

***

## Language and locale

`lang` configuration option specifies the language to be used. Supported languages are currently: `en`, `de`, `fr` and `sv`.

```js
  tipser.elements('posId', {
    lang: 'en'
  })
```

It affects all the localizable texts in the UI - buy buttons, store, shopping cart and checkout. It does not affect the currency in which the customer will pay for the product.

***

##Parameters for dialog customization
Sometimes Tipser dialogue styling and functionality needs to be customized. It is possible with modalUi parameters group.

> Complete example of dialog customizations:

```javascript
const tipserOptions = {
    modalUi: {
      hideSearchIcon: true,
      hideFavouritesIcon: true,
      hideCartIcon: false,
      hideMoreIcon: true,
      hideSimilarProducts: false,
      useCustomCss: true
    }
};
```

### Hiding icons on menu bar

The following parameters under modalUi can be used to selectively hide tipser icons on the dialog menu bar: 

`hideSearchIcon` <br> 
`hideFavouritesIcon` <br>
`hideCartIcon` <br>
`hideMoreIcon` <br>

[![](widget1.png)](/images/widget1.png)

### Hiding Similar Products Module

Similarly, `hideSimilarProducts` parameter, if set to **true**, can be used to hide Similar Products Module on product page

[![](widget2.png)](/images/widget2.png)

### Custom CSS

If there is a need to use custom css stylesheet inside the Tipser dialog iframe, it may be activated in two steps:

1. set `useCustomCss` parameter to **true**
    
2. Send the custom css stylesheet to Tipser administrator in order for it to be uploaded to your account.

***

## Deep linking

By default the `Store` component saves the active collection in the browser's URL hash part (everything after the `#` symbol in the URL). It means that your shopping page may be bookmarked by the user or shared with other users by sending a browser link (the same collection will be active in the `Store` when opening that link). 

If, you wish to turn this behaviour off (e.g. because it interferes with your the routing system of your site), set the `useDeepLinking` parameter to **false**.

***

## Custom Labels

If you want to override our default text with your own, you can do it via customLabels option. At the moment we allow to change the label of the `buy button` only. 

```javascript
const tipserOptions = {
    customLabels: {
      buy: 'buy now!'
    }
};
```

[![](custom-label.png)](/images/custom-label.png)