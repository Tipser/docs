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

The example connects Tipser SDK and sets primary color to `#0000FF`.

All the available configuaration options are: 

```javascript
const configurationOptions = {
  primaryColor: "#0000FF",
  env: "stage",
  lang: 'en-US',
  openOldDialog: false,
  addToCartSettings: {
      directToCheckoutMode: false,
  },
  useDeepLinking: false,
  customLabels: {
    buy: "buy now!",
    unavailable: "not available",
    add_to_cart: "add to shopping bag",
    choose_variant: "available variants",
    out_of_stock: "magazine supplies finished",
  },
  posData: {
    key: "value"
  },
  customUrls: {
    productBaseUrl: (productId) => `/product-page?productId=${productId}`,
    checkoutConfirmationUrl: "/checkout-confirmation",
    checkoutUrl: "/checkout",
  },
  prePopulatedAddress: {
      delivery: {
        firstName: 'John',
        lastName: 'Doe',
        email: 'youremail@email.com',
        zipCode: '12345',
        city: 'Ankeborg',
        street: 'Stårgatan 1',
        country: 'Sweden',
        state: '',
        phoneNumber: '0765260000'
      },
      billing: {
        firstName: 'Jane',
        lastName: 'Doe',
        email: 'billing@w.pl',
        zipCode: '12345',
        city: 'Ankeborgen',
        street: 'Stårgatan 1',
        country: 'Sweden',
        state: '',
      },
  },
  modalUi: {
    hideSearchIcon: true,
    hideFavouritesIcon: true,
    hideCartIcon: false,
    hideMoreIcon: true,
    hideSimilarProducts: false,
  },
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

By default, Tipser Elements connect to production Tipser environment. Yet if testing environment is preferred (e.g. in order to do test purchase), then it can be customized with env parameter in Tipser options, which accept the following values:

- **prod**
- **stage**

***

## Language and locale

`lang` configuration option specifies the language to be used. Supported languages are currently: `en-US`, `en-GB`, `de-DE`, `de-DE-formal`, `fr-FR`, `fi-FI` and `sv-SE`.
                                                                                                                                        
```js
  tipser.elements('posId', {
    lang: 'en-US'
  })
```

It affects all the localizable texts in the UI - buy buttons, store, shopping cart and checkout. It does not affect the currency in which the customer will pay for the product.

***

## Open Old Dialog

If you set this option to `false`, you will have an early access the new Product Dialog (after clicking product tile eg. in a collection), which is based entirely on Tipser Elements and not opened in an iframe. Therefore, it is much easier to style via CSS overwrite. New product dialog will allow some new features and better User Experience compared to the one used previously. Consequently, the old product dialog will be deprecated soon, which will be communicated ahead to every POS through an appropriate channels.

***


### Add To Cart Settings

When the`directToCheckoutMode` option is set to `true`, after clicking the `buy button` the user goes directly to checkout.

***

## Deep linking

By default the `Store` component saves the active collection in the browser's URL hash part (everything after the `#` symbol in the URL). It means that your shopping page may be bookmarked by the user or shared with other users by sending a browser link (the same collection will be active in the `Store` when opening that link). 

If you wish to turn this behaviour off (e.g. because it interferes with the routing system of your site), set the `useDeepLinking` parameter to **false**.

***

## Custom Labels

If you want to override our default text with your own, you can do it via `customLabels` option. At the moment we allow to change following labels for buttons and product information: 

```javascript
const tipserOptions = {
    customLabels: {
      buy: "buy now!",
      unavailable: "not available",
      add_to_cart: "add to shopping bag",
      choose_variant: "available variants",
      out_of_stock: "magazine supplies finished",
    }
};
```

*Example:*
[![](custom-label.png)](/images/custom-label.png)

***

## POS data

Go to [this](#adding-pos-data) section to see the usage.

***

## Custom Urls

To fully embed the Tipser `Product Page` or the `Checkout` on your site, please use these configuration options to determine the relative path directing to them.

```javascript
const tipserOptions = {
    customUrls: {
       productBaseUrl: (productId) => `/product-page?productId=${productId}`,
       checkoutUrl: "/checkout",
       checkoutConfirmationUrl: "/checkout-confirmation",
    }
}
```
***

## Prepopulated address data

If you would like to use your logged-in User's data to prepopulate address data of the payment provider, you can pass it on via Tipser config `prePopulatedAddress` option.

```javascript
const tipserOptions = {
    prePopulatedAddress: {
      delivery: {
        firstName: 'John',
        lastName: 'Doe',
        email: 'youremail@email.com',
        zipCode: '12345',
        city: 'Ankeborg',
        street: 'Stårgatan 1',
        country: 'Sweden',
        state: '',
        phoneNumber: '0765260000'
      },
      billing: {
        firstName: 'Jane',
        lastName: 'Doe',
        email: 'youremail@email.com',
        zipCode: '',
        city: 'Ankeborgen',
        street: 'Stårgatan 1',
        country: 'Sweden',
        state: '',
      },
    },
}
```

To add the address data dynamically, please use the [`updateConfig`](#updateconfig())function.

##Parameters for old dialog customization
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

### updateConfig()

To update any of the configuration options dynamically, please use the `updateConfig()` function. 

* In Tipser Script:

```javascript
window.elements = tipser.updateConfig({
  primaryColor: "#333333",
})
```

