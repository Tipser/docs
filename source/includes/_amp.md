#AMP

Tipser Elements can be also rendered as a part of an AMP-based page. 

Due to the limitations of AMP format, AMP snippet is limited in functionality compared to standard Tipser Elements.

## Limitations

- even if you need to display only one product, please create a Tipser collection with just one product
- there is no support for an interactive shopping cart icon
- the checkout process is finalized after a redirect to tipser.com page (no way to keep the user in the article)

But despite those limitations, the basic shopping experience is sustained, allowing AMP articles to generate income from E-commerce.  

## Installation

### Required imports
Add the following AMP imports to the `<head>` element of your page or make sure they are already there.

```html
<script async custom-element="amp-list" src="https://cdn.ampproject.org/v0/amp-list-0.1.js"></script>
<script async custom-template="amp-mustache" src="https://cdn.ampproject.org/v0/amp-mustache-0.2.js"></script>
<script async custom-element="amp-iframe" src="https://cdn.ampproject.org/v0/amp-iframe-0.1.js"></script>
<script async custom-element="amp-bind" src="https://cdn.ampproject.org/v0/amp-bind-0.1.js"></script>
```

### Styles

Add the following Tipser styles to the `<head>` element of your page. They are not mandatory but highly recommended.

```
<style amp-custom>*{box-sizing:border-box}.list{display:flex}.tipser-product-tile{cursor:pointer;float:left;max-width:250px;min-width:160px;position:relative;overflow:hidden;width:25%;padding:10px}.tipser-product-tile:hover .tipser-product-text{opacity:1;transform:translate(0,-3)}.tipser-tile-img-container{display:block;position:relative;background:#fff;height:250px;width:100%}amp-img.tipser-tile-img img{object-fit:contain}amp-img.tipser-tile-img-hover{transition:.7s;opacity:0}.tipser-product-tile:hover .tipser-tile-img-hover{opacity:1}.tipser-product-text{background:rgba(255,255,255,0.9);bottom:0;border-top:1px solid #ececec;color:black;margin-left:auto;margin-right:auto;min-height:140px;left:0;letter-spacing:.3px;opacity:0;position:absolute;right:0;text-align:center;transition:.7s;z-index:2}.tipser-tile-product-text,.tipser-tile-product-text[data-tipser-hide-text="slide"]{font-size:12px;padding:10px;text-align:center;transition:.5s}.tipser-tile-prod-brand{color:#afafaf;line-height:1.8em;text-transform:uppercase;text-overflow:ellipsis;overflow:hidden;white-space:nowrap}.tipser-tile-prod-name{line-height:1.8em;text-overflow:ellipsis;overflow:hidden;white-space:nowrap}.tipser-buy-button-small{background-color:#e91e63;border-radius:0;color:white;display:inline-block;font-size:12px;font-weight:700;line-height:1.8;margin:5px auto 0;padding:5px 30px;padding:10px 30px;position:relative;text-transform:uppercase;text-align:center;transition:.5s;width:auto}.tipser-tile-price{height:30px;overflow:hidden}.tipser-label-price-new{color:#cd5550;font-size:13.2px;font-weight:bold;white-space:nowrap}.tipser-label-price-new+.tipser-label-price-old{text-decoration:line-through}.tipser-label-price-save{color:#cd5550}.overlay{background:rgba(255,255,255,0.7);bottom:0;left:0;overflow:auto;position:fixed;right:0;top:0;z-index:10}.dialog{background-color:#fff;border:1px solid lightgray;bottom:5px;left:5px;position:fixed;right:5px;top:5px;z-index:1}.tipser-dialog{display:block;transition:opacity 2s ease;opacity:0;overflow:hidden;border:1px red solid;position:fixed;top:4%;left:5%;bottom:5%;right:5%}.tipser-dialog_closed{pointer-events:none;opacity:0;height:1px}.tipser-dialog_open{opacity:1;pointer-events:all}.close_button{cursor:pointer;float:right;padding:10px 15px;z-index:2}.list-overflow[overflow]{position:absolute;bottom:0;left:10px;background:lightgray;color:gray;font-size:12px;padding:6px 35px;width:130px}.tipser-product-text[data-tipser-hide-text="false"]{background-color:transparent;border:0;opacity:1;position:relative;width:100%}@media(max-width:900px){.tipser-product-tile{max-width:300px;width:calc((100% - 20px) / 3)}.tipser-product-text{background-color:transparent;border:0;opacity:1;position:relative;width:100%}.tipser-tile-product-text{padding:10px 0 0 0}.tipser-buy-button-small{width:100%}}@media(max-width:620px){.tipser-product-tile{max-width:250px;width:calc((100% - 20px) / 2)}}@media(max-width:360px){.tipser-product-tile{max-width:unset;width:calc(100% - 20px)}}</style>
```

## Insert collection

This step assumes that your are familiar with [Tipser Bookmarklet](https://developers.tipser.com/tipser-tools). Feel free to write to support@tipser.com to get a more personalized introduction.

1. Log-in to Tipser Bookmarklet
2. Click "Insert collections" button
3. From the collections list, select the collection that you want to embed
4. Click "Insert collection" button and in the dialog that opens tick "Google AMP ready" checkbox
5. Copy the code from the dialog and paste it somewhere into the `body` section of your page
   